# Cursor
```
when main process dies leaving its child, cursor comes
```


```c
#include<stdio.h>
main()
{  printf("%d %d\n",getpid(),getppid());
   int i,p=fork();
   if (p!=0) sleep(5);
   else 
      for(i=1;i<3;i++)
      {  sleep(3); 
         printf("%d %d\n",getpid(),getppid());
      }
}
```
```
let a:main  b:window  c:child  d:login 
t=0 a b      (main, window = parent of main)
t=3 c a
t=5 cursor   (When main dies cursor comes)
t=6 c d      (when parent dies, child is adopted by login process)

Here main and parent same but it is not necessary.
```
