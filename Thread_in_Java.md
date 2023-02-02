# Thread in Java
```
Threads execute in parallel like processes but have more control and communication
```
```java
class xyz implements Runnable { 
  public void run() {
    int i; 
    for(i=0; i<5; i++) { 
      System.out.print(i); 
      try{
        Thread.sleep(1000);
      } 
      catch(Exception e){}
    }
  }
}

class kapil {
  public static void main(String ar[}) throws Exception {
    xyz k;            // create new object of class xyz called k
    Thread a,b;       // create two threads a and b
    k = new xyz();    
    a = new Thread(k); 
    b = new Thread(k);
    a.start(); 
    System.out.print("x");
  }
}
```
Practical Application
```
various types of outputs can be generated using suitable combination of a.start(), a.run() and Thread.sleep(x)
```
