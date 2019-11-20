### Clock Angle

# Calculate the angle between hour hand and minute hand

This problem is know as [Clock angle problem](http://en.wikipedia.org/wiki/Clock_angle_problem) where we need to find angle between hands of an analog clock at a given time.

**Examples:**

```java
Input:  h = 12:00, m = 30.00
Output: 165 degree

Input:  h = 3.00, m = 30.00
Output: 75 degree
```



~~~java

// Java program to find angle between hour and minute hands 
import java.io.*; 
  
class GFG  
{ 
    // Function to calculate the angle 
    static int calcAngle(double h, double m) 
    { 
        // validate the input 
        if (h <0 || m < 0 || h >12 || m > 60) 
            System.out.println("Wrong input"); 
  
        if (h == 12) 
            h = 0; 
        if (m == 60)  
            m = 0; 
  
        // Calculate the angles moved by hour and minute hands 
        // with reference to 12:00 
        int hour_angle = (int)(0.5 * (h*60 + m)); 
        int minute_angle = (int)(6*m); 
  
        // Find the difference between two angles 
        int angle = Math.abs(hour_angle - minute_angle); 
  
        // smaller angle of two possible angles 
        angle = Math.min(360-angle, angle); 
  
        return angle; 
    } 
      
    // Driver program 
    public static void main (String[] args)  
    { 
        System.out.println(calcAngle(9, 60)+" degree"); 
        System.out.println(calcAngle(3, 30)+" degree"); 
    } 
} 
~~~

