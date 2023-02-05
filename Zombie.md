# Zombie process
```
After execution of child process, it becomes zombie waiting for parent to terminate.
From child death till parent death, child remains zombie
However if we use wait(); in parent, then child is terminated from zombieness 
```
Example 1
```c
#include<stdio.h>
main()
{  int p=fork();
   printf("%d\n",getpid());
   if(p==0){sleep(30);printf("K\n");}
   else {sleep(40);wait();printf("T\n");sleep(10);}
}
```
```
Zombie child from t=30-40
if you remove wait
Zombie child from t=30-50
```
