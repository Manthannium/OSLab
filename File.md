# File Descriptor (FD)
### Low level system calls
```c
#include<stdio.h>
#include<fcntl.h>  // for file handling

main() {
int fd;
fd = open("h",65,0666);  // fd = 3
write(fd,"kthwey",6);    // 6 = no. of letters to write
}
```

### High level system calls
```c
FILE *k;  // k=58 is buffer
k = fopen("t","w"); // open file t in write mode
write(3,"gh",2);    // write gh in fd=3 (here file t)
fprintf(k,"pqr");   // write pqr in buffer=k
fflush(k);	    // flush buffer into file
write(3,"uv",2);

// buffer k=58 is associated with fd=3
// outputs ghpqruv. If fflush is removed then ghuvpqr
// buffer is flushed at last
```
```c
FILE *a;
p = open("x",65,0666);
a = fdopen(p,"w");
//is equivalent to
a = fopen("x","w");
```
```c
a = fopen("x","w");  // file in FD=3, buffer a=58
write(3,"pq",2);  // pq is written in x
fprintf(a,"rs");  // rs is written in buffer
close(3);    // makes FD=3 free
open("y",65,0666); // file y is opened in FD=3
write(3,"uv",2);
fprintf(a,"gh");

// x = pq, y = uvrsgh
// if we replace close(3) with fclose(3)
// fclose(3) frees both FD=3 and buffer=58
// x = pqrs, y = uv as buffer is not associated with FD=3
```
