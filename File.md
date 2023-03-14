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
