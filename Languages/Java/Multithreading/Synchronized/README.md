# Synchronized

```java
public class Bank {
    private int money = 0;

    public Bank(int money) {
        this.money = money;
    }

    //public void add(String name, int amount) {
    public synchronized void add(String name, int amount) {
        money += amount;
        System.out.println(name+" added "+amount+", in total: "+money);
    }

    //public boolean reduce(String name, int amount) {
    public synchronized boolean reduce(String name, int amount) {
        if(amount > money) {
            System.out.println("not enough money");
            return false;
        }

        money -= amount;
        System.out.println(name+" took "+amount+", in total: "+money);
        return true;
    }
}
```

```java
public class BankTest {
    public static void main(String[] args) {
        Bank bank = new Bank(1000);

        for (int i=0; i<900; i++) {
            new Thread(new Reduce(bank, ""+i, 1)).start();
        }
        for (int i=0; i<900; i++) {
            new Thread(new Add(bank, ""+i, 1)).start();
        }
    }
}

class Add implements Runnable {
    private Bank bank;
    private int amount;
    private String name;

    public Add(Bank bank, String name, int amount) {
        this.bank = bank;
        this.amount = amount;
        this.name = name;
    }

    @Override
    public void run() {
        bank.add("Thread" + name, amount);
    }
}

class Reduce implements Runnable {
    private Bank bank;
    private int amount;
    private String name;

    public Reduce(Bank bank, String name, int amount) {
        this.bank = bank;
        this.amount = amount;
        this.name = name;
    }

    @Override
    public void run() {
        bank.reduce("Thread" + name, amount);
    }
}
```