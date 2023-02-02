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
```
possible outputs : x01234 or 0x1234
here sleep ensures one thread takes rest (1 sec) and other executes
However order of execution of threads is random that's why multiple possible outputs 
```
```
a.start();   // means start execution of thread a, however next instruction can also be executed
a.run();     // first execute a fully then only move to next instruction
Thread.sleep(x);   // Thread sleeps for x in miliseconds
```

Practical Application
```
various types of outputs can be generated using suitable combination of a.start(), a.run() and Thread.sleep(x)
```

# Thread in C
```c
#include<stdio.h>
#include<pthread.h>

void *f(void *x) {
  sleep(1);
  for(int i=0; i<=5; ++i) {
    printf("%d\n", i*10);
  }
}

int main() {
  pthread_t g;
  pthread_create(&g, NULL, f, NULL);
  for(int j=1; j<=3; ++j) {
    printf("%d\n", 346+j);
    sleep(2);
  }
  pthread_join(g, NULL);
  printf("done\n");
  sleep(8);
}

// compile : gcc prog.c -lpthread
```
```
Output : 347,10,348,20,349,30,40,50,done

if remove pthread_join then
Output : 347,10,348,20,349,30,done,40,50
(so there join waits till other threads completes and then joins them and executes further)

if remove pthread_join and sleep(8) then
Output : 347,10,348,20,349,30,done
(here once parent thread is killed/completed its children no further able to execute)

if we replace sleep(8) with sleep(2), then additional 40 is also printed
```


