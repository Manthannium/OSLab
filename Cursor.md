# Cursor
```
when main process dies leaving its child, cursor comes
```

Example 1
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

Example 2
```c
#include<stdio.h>
main()
{  printf("%d %d\n",getpid(),getppid());
   int i,q,p=fork();
   if (p!=0) sleep(5);
   else 
   {  q=fork();
      if(q==0) sleep(1);
      for(i=1;i<4;i++)
      {  sleep(3); 
         printf("%d %d\n",getpid(),getppid());
      }
   }
}
```
```
let a:main  b:window  c:child  g: grandchild d:login
t=0 a b
t=3 c a
t=4 g c
t=5 cursor  (As main dies, so comes cursor)
t=6 c d  (now c is adopted by login process)
t=7 g c
t=9 c d
t=10g d   (after c's death, d is adopted by login)
 
Here though c dies (father of g), cursor doesn't come as c is not main process
```
