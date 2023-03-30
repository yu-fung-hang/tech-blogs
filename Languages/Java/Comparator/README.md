# Comparator

An example of defining a comparator for a class.

**Point.java**

``````java
public class Point
{
    private double x;
    private double y;
    private String name;

    public Point(double x, double y) {
        this.x = x;
        this.y = y;
    }

    public double getX() {
        return x;
    }

    public void setX(double x) {
        this.x = x;
    }

    public double getY() {
        return y;
    }

    public void setY(double y) {
        this.y = y;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public boolean equals(Object obj) {
        double x = ((Point)obj).getX();
        double y = ((Point)obj).getY();

        return this.x == x && this.y == y;
    }
}

class PointComparator implements Comparator<Point>
{
    public int compare(Point p1, Point p2)
    {
        double x1 = p1.getX();
        double y1 = p1.getY();
        double x2 = p2.getX();
        double y2 = p2.getY();

        if(x1 != x2) {
            return (x1 - x2) > 0 ? 1 : -1;
        } else {
            return (y1 - y2) > 0 ? 1 : -1;
        }
    }
}
``````

**Main.java**

```java
import java.util.PriorityQueue;

public class Main
{
    public static void main(String[] args)
    {
        PointComparator pointComparator = new PointComparator();
        PriorityQueue<Point> queue = new PriorityQueue<>(pointComparator);
        Point p1 = new Point(1, 5);
        Point p2 = new Point(4, 3);
        Point p3 = new Point(3, 6);
        Point p4 = new Point(2, 4);
        Point p5 = new Point(4, 1);

        queue.add(p1);
        queue.add(p2);
        queue.add(p3);
        queue.add(p4);
        queue.add(p5);

        while (!queue.isEmpty())
        {
            Point p = queue.poll();
            System.out.println("("+p.getX()+", "+p.getY()+")");
        }
    }
}
```

**Result**
```
(1.0, 5.0)
(2.0, 4.0)
(3.0, 6.0)
(4.0, 1.0)
(4.0, 3.0)
```