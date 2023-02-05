# Zombie process
```
After execution of child process, it becomes zombie waiting for parent to terminate.

child process doesn't becomes zombie if it dies after parent or when parent is waiting

From child death till parent death, child remains zombie

However if we use wait(); in parent, then child is terminated from zombieness 

when we use wait(); in parent, it pauses and waits for its child process to complete, then only it resumes
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
Example 2
```c
#include<stdio.h>
main()
{
   int i,p=fork();
   printf("%d %d\n",getpid(),getppid());
 //  scanf("%d",&i); //Give 2 numbers as input
   if (p!=0){ sleep(30);printf("K\n");wait();printf("T\n");sleep(12); }
   else sleep(20);
   printf("%d over\n",getpid());
}
```
```
t=20 child over
Child is zombie from t=20-30
t=30 K, child released, T
t=42 parent over

Time is measured after giving input

Replace sleep(30) by sleep(2)
t=2 K, parent waits
t=20 child over and released, T
t=32 parent over
```
