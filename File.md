# File Descriptor (FD)
```c
#include<stdio.h>
#include<fcntl.h>  // for file handling

main() {
	int fd;
	fd = open("h",65,0666);  // fd = 3
	write(fd,"kthwey",6);
}
```
