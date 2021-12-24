# Main thread waits for others to die

## Method 1: join()

``````java
class MyThread1 implements Runnable
{
    private int id;

    public MyThread1(int id)
    { this.id = id; }

    public void run()
    {
        for(int i=1; i<=1000; i++)
        { System.out.println("This is thread " + this.id); }
    }
}

public class testJoin
{
    public static void main(String args[]) throws InterruptedException
    {
        int threadNum = 3;
        Thread[] threads = new Thread[threadNum];

        for(int i=0; i<threadNum; i++)
        {
            threads[i] = new Thread(new MyThread1(i));
            threads[i].start();
        }

        System.out.println("All threads start running...");

        for(int i=0; i<threadNum; i++)
        { threads[i].join(); }

        System.out.println("End");
    }
}
``````

## Method 2: CountDownLatch

A synchronization aid that allows one or more threads to wait until a set of operations being performed in other threads completes.

``````java
import java.util.concurrent.CountDownLatch;

class MyThread2 implements Runnable
{
    private int id;
    private final CountDownLatch latch;

    public MyThread2(int id, CountDownLatch latch)
    {
        this.id = id;
        this.latch = latch;
    }

    @Override
    public void run()
    {
        for(int i=1; i<=1000; i++)
        { System.out.println("This is thread " + this.id); }

        latch.countDown();
    }
}

public class testCountDownLatch
{
    public static void main(String[] args)
    {
        int count = 3;
        final CountDownLatch latch = new CountDownLatch(count);

        for(int i=0; i<count; i++)
        { new Thread(new MyThread2(i, latch)).start(); }

        System.out.println("All threads start running...");

        try {
            latch.await();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("End");
    }
}
``````

## Method 3: CyclicBarrier

```java
import java.util.concurrent.BrokenBarrierException;
import java.util.concurrent.CyclicBarrier;
import java.util.concurrent.Executor;
import java.util.concurrent.Executors;

class Visitor implements Runnable
{
    private CyclicBarrier cyclicBarrier;
    private String name;
    private int arriveTime;

    public Visitor(CyclicBarrier cyclicBarrier, String name, int arriveTime)
    {
        this.cyclicBarrier = cyclicBarrier;
        this.name = name;
        this.arriveTime = arriveTime;
    }

    @Override
    public void run()
    {
        try {
            Thread.sleep(arriveTime * 1000);
            System.out.println(name + ": I am here!");
            cyclicBarrier.await();
            System.out.println(name + ": Cool!");
        } catch (InterruptedException e) {
            e.printStackTrace();
        } catch (BrokenBarrierException e) {
            e.printStackTrace();
        }
    }
}

class TourGuide implements Runnable
{
    @Override
    public void run()
    {
        System.out.println();
        System.out.println("Tour guide: Alright, everyone is here. You can go wherever you want now!");
        System.out.println();
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}

public class testCyclicBarrier
{
    public static void main(String[] args) throws Exception
    {
        int numOfVisitors = 3;
        CyclicBarrier cyclicBarrier = new CyclicBarrier(numOfVisitors, new TourGuide());
        Executor executor = Executors.newFixedThreadPool(numOfVisitors);

        executor.execute(new Visitor(cyclicBarrier,"Alex",1));
        executor.execute(new Visitor(cyclicBarrier,"Bob",2));
        executor.execute(new Visitor(cyclicBarrier,"Cathy",3));
    }
}
```

**Result**:
``````
Alex: I am here!
Bob: I am here!
Cathy: I am here!

Tour guide: Alright, everyone is here. You can go wherever you want now!

Cathy: Cool!
Alex: Cool!
Bob: Cool!

``````