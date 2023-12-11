# 

## L3
### Demo Task1
- `ps`
- `ps -a`
- `ps -l`

Task 2:
- `ls`: list the files in the current directory
  - `ls -l`: list the files in the current directory in long format
  - `ls -a`: list the files in the current directory, including the hidden files
  - `ls -t`: list the files in the current directory, sorted by time
  - `ls -lat`: list the files in the current directory, including the hidden files, in long format, sorted by time

- `cd`: change the current directory
  - `.`: the current directory
  - `..`: the parent directory

- `cp`: copy a file
  - `cp file1 file2`: copy file1 to file2
  - `cp file1 file2 file3 dir`: copy file1, file2, file3 to dir
  - `cp -r dir1 dir2`: copy dir1(all the content) to dir2 recursively

- `mv`: move a file
  - `mv file1 file2`: move file1 to file2
  - `mv file1 file2 file3 dir`: move file1, file2, file3 to dir
  - `mv dir1 dir2`: rename dir1 to dir2
  
- `rm`: remove a file
  - `rm -rf dir`: remove dir recursively and forcefully

- `mkdir`: make a directory
  - `mkdir dir`: make a directory named `dir`

- `who`: show the users who are currently logged in
  - `whami`: show the current user
  - `who -q`: show the number of users who are currently logged in
  - `who -u`: show the idle time of the users who are currently logged in

- `cat`: concatenate files and print on the standard output
  - `cat file`: print the content of file on the standard output
  - `cat file1 file2`: print the content of file1 and file2 on the standard output
  - `cat file1 file2 > file3`: concatenate file1 and file2, and write the result to file3
  - `cat file1 file2 >> file3`: concatenate file1 and file2, and append the result to file3
 
- `man`: an interface to the on-line reference manuals
  - `man command`: show the manual of command
  - `man -k keyword`: search the manual for keyword
  - `man -f command`: show the manual of command
  - `man -a command`: show all the manual of command

- `gcc`: GNU project C and C++ compiler
  - `gcc file`: compile file
  - `gcc file -o file`: compile file and output the executable file to file
  - `gcc file1 file2 -o file`: compile file1 and file2 and output the executable file to file
 

Task 3:
- `vi`: a text editor
  - `vi file`: open file in vi
  - `i`: enter insert mode
  - `esc`: exit insert mode, enter command mode
- Under command mode:
  - `:w`: save the file
  - `:q`: quit vi
  - `:wq`: save and quit vi
  - `:q!`: quit vi without saving
  - `h`: move leftward; `l`: move rightward; `j`: move downward; `k`: move upward
  - `w`: move rightward word by word; `b`: move leftward word by word
  - `dw`: delete the word after the cursor
  - `u`: undo the last command
  - `dd`: delete the current line
  - `$`: move to the end of the line; `^`: move to the beginning of the line

- `gedit`: a text editor
  - `gedit file`: open file in gedit

Task 4: Shell output redirection
  - `who > users`: redirect the output of `who` to file `users`, overwriting(replace) the original content of `users`
  - `who >> users`: append the output of `who` to file `users`

Task 5: Shell input redirection
  - `wc < users`: redirect the content of `users` to `wc`, and count the number of lines, words, and characters in `users`
  - `wc -l`: count the number of lines
  - `wc -l < output.txt > output1.txt`: count the number of lines in `output.txt`, and write the result to `output1.txt`

Task 6: write, compile, and run a C program
  - `vim hello.c`: write a C program in vi
  - `gcc hello.c -o hello`: compile the C program and output the executable file to `hello`
  - `./hello`: run the executable file

External Task: pipeline - make a pipe among processes
  - `ls -l | wc -l`: count the number of files in the current directory
  - `ls -l | grep "hello"`: list the files in the current directory whose name contains "hello"
  - `ls -l | grep "hello" | wc -l`: count the number of files in the current directory whose name contains "hello"

---
### Demo Task2
```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

void main (void){
    printf("Process ID: %ld\n", (long)getpid());
    printf("Parent ID: %ld\n", (long)getppid());
    printf("Onwer user ID: %ld\n", (long)getuid());
}

```


---
### Demo Task3
```c
#include <stdio.h> 
#include <sys/types.h> 
#include <unistd.h> 
void main(void){
    int ret_from_fork, mypid;
    mypid = getpid();
    printf("Before: my pid is %d\n", mypid);
    ret_from_fork = fork();
    sleep(1);
    printf("After: my pid is %d, fork() said %d\n", getpid(), ret_from_fork); 
}

```


---
### Demo Task5
```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
void main(void){
    int i, n = 4;
    pid_t childpid;
    for (i = 1; i < n; ++i)
        if (childpid = fork())
            break; //parent breaks out; child continues
    fprintf(stdout, "This is process %ld with parent %ld, i = %d\n",(long)getpid(), (long)getppid(), i);
}

```


---
### Demo Task6
```c
#include <stdio.h> 
#include <sys/types.h> 
#include <unistd.h> 
void main(void){
    int i, n = 4;
    pid_t childpid;
    for (i = 1; i < n; ++i)
        if ((childpid = fork()) <= 0)
        break; //child and error break out; parent continues
    fprintf(stdout, "This is process %ld with parent %ld\n, i = %d",(long)getpid(), (long)getppid(), i);
}

```


---
### Demo Task7
```c
#include <stdio.h> 
#include <sys/types.h> 
#include <sys/wait.h> 
#include <unistd.h> 
#include <errno.h> 
  void main(void){
    int i, n = 4, status;
    pid_t childpid, waitreturn;
    for (i = 1; i < n; ++i) {
      if (childpid = fork()) {
        break; //parent breaks from for loop
      }
    }
    // parent process waits for all children to terminate
    // in parent process, childpid is the PID of the child process
    // if child terminated, the return value is positive and is the PID of that child
    while (childpid != (waitreturn = wait(&status))){ // child process has not terminated
      if ((waitreturn == -1) && (errno != EINTR)) // child process has terminated
        break;
      }
    fprintf(stdout, "I am process %ld, my parent is %ld\n", (long)getpid(), (long)getppid());
}
```

---
### Demo Task 8
- In-class demo: `exec` example on creating a process to run `ls -l` 

```c
#include <sys/types.h> 
#include <sys/wait.h> 
#include <unistd.h> 
#include <stdio.h>
#include <stdlib.h> 
void main(void){
  int status;
  pid_t childpid;
  if ((childpid = fork()) == -1){
    perror("Error in the fork"); 
    exit(1);
  }else if (childpid == 0){ 
    /* child code */
    if (execl("/usr/bin/ls", "ls", "-l", NULL) < 0){ // user/bin/ls is not the path of ls - use & user
      perror("Exec of ls failed"); 
      exit(1);
    } 
  } else if (childpid != wait(&status))
    // 
    /* parent code */ 
    perror("A signal occurred before child exited");
  exit(0);
}
```
> Compare with typing `ls -l` directly in terminal, the process performs `ls -l` in `./l3demo8` is the **grandson** of the terminal process, and the process performs `ls -l` in `./l3demo8` is the **child** of the terminal process.

---
### Demo Task 9
- In -class demo: `exec` example on creating a process to run `ls -l`
  - `execvp()`: 
    - `p` - search the executable file in the `PATH` environment variable
    - `v` - arguments are passed to main as an array of char *const pointers, each pointing to a C string.


```c
#include <sys/types.h> 
#include <sys/wait.h>
#include <unistd.h> 
#include <stdio.h> 
#include <stdlib.h> 

void main(void){
  int status;
  pid_t childpid; 
  char *argv[3]; 
  argv[0] = "ls"; 
  argv[1] = "-l"; 
  argv[2] = 0; //NULL pointer

  if ((childpid = fork()) == -1){
    perror("Error in the fork"); 
    exit(1);
  } else if (childpid ==0) {
  /* child code */
  if (execv("/user/bin/ls", argv) < 0){
    perror("Exec of ls failed"); 
    exit(1);
  } 
  } else if (childpid != wait(&status))
  /* parent code */ 
  perror("A signal occurred before child exited");
  exit(0);
}
```

---
#### Demo Task 10
- In-class demo: `exec` has no return.

```c
#include <sys/types.h> 
#include <sys/wait.h> 
#include <unistd.h> 
#include <stdio.h> 
#include <stdlib.h> 
int main(void){
  printf("Old image: pid=%d\n", getpid());  
  execlp("./newimage", "newimage", NULL); 
  printf("Old image: hello\n"); 
  return 0;
}

```

```c
#include <sys/types.h> 
#include <sys/wait.h> 
#include <unistd.h> 
#include <stdio.h> 
#include <stdlib.h> 
int main (void) {
  printf("New image: pid=%d\n", getpid());
  return 0;
}

```
`exec` will not create a new process, still the same process. The memory will be re-written by the new image.

```c
#include <sys/types.h> 
#include <sys/wait.h> 
#include <unistd.h> 
#include <stdio.h> 
#include <stdlib.h> 
int main(void){
  char * envp[2]
  envp[0] = "PATH=test"
  envp[1] = NULL;

  printf("Old image: pid=%d\n", getpid());  
  execle("./newimage", "newimage", NULL, envp); 
  printf("Old image: hello\n"); 
  return 0;
}
```

```c
#include <sys/types.h> 
#include <sys/wait.h> 
#include <unistd.h> 
#include <stdio.h> 
#include <stdlib.h> 
int main (void) {
  printf("New image: pid=%d\n", getpid());
  printf("New image: PATH=%s\n", getenv("PATH")); 
  return 0;
```

- `e`: entire 

---

#### Demo Task 11

```c
#include <stdio.h> 
#include <stdlib.h> 
#include <errno.h> 
#include <sys/types.h> 
#include <sys/stat.h> 
#include <fcntl.h> 
#include <unistd.h> 
#include <syslog.h> 
#include <string.h> 
#define MAX_I 100
void main (void){
  pid_t pid, sid; 
  FILE* p_output; 
  int i = 0;

  pid = fork(); 
  if (pid < 0) exit(EXIT_FAILURE); 
  if (pid > 0) exit(EXIT_SUCCESS);

  umask(0);
  sid = setsid(); // create the daemon process
  if (sid < 0) 
    exit(EXIT_FAILURE); 
  if ((chdir(".")) < 0) // change the directory to the current directory
    exit(EXIT_FAILURE);

  printf("Daemon: Hello!\n"); // the child session will inherit the stdout from the parent, so it will still print out on the current terminal("parent" session)

  close(STDIN_FILENO); 
  close(STDOUT_FILENO); 
  close(STDERR_FILENO); 

  printf("Daemon: Goodbye!\n"); // `STDIN/OUT` are closed, the child session cannot access parent I/O, so it will not print out in current terminal

  while(1){
    if ((p_output = fopen( “daemon_output.txt”, “a”)) != NULL){
      fprintf(p_output, “%d\n”, i++); i %= MAX_I; fclose(p_output);
    } 
    sleep(3);
  } 
  exit(EXIT_SUCCESS);
}

```
**umask**
- `umask(0)`: set the **file mode creation mask(umask)** to 0, so that the file mode of the daemon output file is not restricted.
- `umask()` sets the calling process's file mode creation mask to `mask & 0777`, `7` means `111` in binary 
  - `open()` and `mkdir()`
  - `mkdir()`: the mode of the created  directory  is  (`mode  & ~umask & 0777`)
    - `mode` is default mode
    - e.g. `umask(0)` -> `mkdir()` -> `0777 & ~0 & 0777` -> `0777`: the deafult mode will be remained

**setsid**
- although `setsid` will move to another session, but the opened file is still be accessed
- the child process calls `setsid()` to create a new session and obtain a new session ID (SID). If setsid() fails (returns -1), the program exits with a failure status.
- The child process then changes the current working directory to the root directory using `chdir(".")`. If the `chdir()` call fails, the program exits with a failure status.
- child process closes the standard input, standard output, and standard error file descriptors. This is done to **disconnect** the daemon process from the terminal, as it no longer needs them.

> above code is a daemon process, which is terminal-realted not login-related.


---
## L4
### Demo Task 1
**What are the differences between a regular file and a device file?
**
```c
>cp /etc/passwd /tmp/garbage 
>cp /etc/passwd /dev/tty
//
> cp normal.txt /dev/tty
Hello world!
```

- content will be **displayed** on the terminal for `tty` device file

---
### Demo Task 2
The C library function `getcwd` returns the pathname of the current working directory
  - `char *getcwd(char *buf, size_t size)` 
  - `size` specifies maximum length pathname. If longer than the maximum, returns `NULL` and sets `errono to ERANGE`.

```c
#include <unistd.h> 
#include <stdio.h> 
#include <errno.h> 
int main(){
  char cwd[1024]; 
  if (getcwd(cwd, sizeof(cwd)) != NULL)
    printf("Current working dir: %s\n", cwd);
  else 
    perror("getcwd() error"); return 0;
}
```

---
**read a file**
> bytes = read(fd, buffer, count) 
- Read from file associated with `fd`; place `count` bytes into `buffer`
  - `fd`: file descriptor to reasd from
  - `buffer`: pointer to any array
  - `count`: number of bytes to read
- Returns number of bytes read or `-1` if an error occured

### Demo Task 3
```c
int fd = open("someFile", O_RDONLY);
char buffer[4]; // store in stack, no need to de-allocate
char * buff2 = malloc(4*sizeof(char)); // store in heap, need to de-allocate
int bytes = read(fd, buffer, 4*sizeof(char));
free(buff2); // de-allocate the memory or there will be memory leak
```

---
**write a file - overwrite**
> bytes = write(fd, buffer, count)
- Write contents of `buffer` to the file associated with `fd`, write `count` bytes into the file
  - `O_TRUNC`: if the file already exists and is a regular file and the access mode allows writing, truncate it to length 0.
  - `fd`: file descriptor to write to
  - `buffer`: pointer to any array
  - `count`: number of bytes to write
- Returns number of bytes written or `-1` if an error occured

### Demo Task 4
```c
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>
#include <stdlib.h>

void main(){
  char buff4[4] = {'a','b','c',0}
  int i = 0;
  int bytes_written = 0;
  int fd;
  fd = open("someFile", O_WRONLY|O_CREAT, 0644);

  printf("sizeof(buffer) is %d\n", sizeof(buffer));
  // char buffer[4];
  bytes_written = write(fd, buffer, 4*sizeof(char));

  for (i = 0; i < 4; i++) {
    printf("The %dth byte is %c\n", i, buffer[i]);
  }

  fsync(fd); // flashes the content into disk before close (for written)
  close(fd); // when open, close it
}
```

---
#### Demo Task 5
```c
#include <stdio.h>
FILE *myfp;
if ((myfp = fopen("/home/ann/my.dat", "w")) == NULL)
  fprintf(stderr, "Could not fopen file\n");
else
  fprintf(myfp, "This is a test");
```

- overwrite

```c
#include <stdio.h>
void main() {
  FILE *fp;

  fp = fopen("someFile", "w");
  if (fp == NULL) {
    fprintf(stderr, "Could nor fopen file.\n");
  }
  else {
    fprintf(fp, "This is a test");
  }
  fflush(fp);
  fclose(fp);
}
```

---
### Demo Task 6
```c
printf("The sum of %d, %d, and %d is %d\n", 65, 87, 33, 65+87+33); 
// output: The sum of 65, 87, and 33 is 185
printf("Error %s occurred at line %d \n", emsg, lno); 
// output: Error invalid variable occurred at line 27
printf("Hexadecimal form of %d is %x \n", 59, 59); 
// output: Hexadecimal form of 59 is 3B
```

```c
#include <stdio.h>

void main() {
  int x = -1;
  printf("%%d = (%d) , %%i = (%i), %%u = (%u), %%o = (%o), %%x = (%x), %%X = %X\n", x, x, x, x, x, x);
  char c = 'a';
  char* s = "hello world.\n"; // literal string
  float f = 1.12345678901234567890e20;
  double lf = 1.12345678901234567890e20;
  printf("%%c = (%c).\n", c);
  printf("%%s = (%s).\n", s);
  printf("%%f = (%f), %%lf = (%lf), %%e = (%e), %%E = (%E), %%g = (%g), %%G = (%G).\n", f,lf,lf,lf,lf,lf);
}
```

```
%d = (-1) , %i = (-1), %u = (4294967295), %o = (37777777777), %x = (ffffffff), %X = FFFFFFFF
```

---
### Demo Task 7
fgets():
```c
#include <stdio.h>

void main() {
  int i;
  char c;
  char buf[256];
  while (1) {
    fgets(buf, sizeof(buf), stdin);
    printf("%s = \"%s\".\n", buf);
  }
```

fscanf():
```c
#include <stdio.h>

void main() {
  int i;
  char c;
  char buf[256];
  FILE* datafile;
  datafile = fopen("mydata.txt", "r");
  while (!feof(datafile)) {
    fscanf(datafile, "%d %c %s", &i, &i, &buf);
    printf("i = %d, c = \'%c\', s = \"%s\".\n, i, c , buf");
  }
}

```

---
### Demo Task 8
```c
#include<stdio.h> 
#include<fcntl.h> 
#include<unistd.h> 

char* cmd[] = {"/bin/ls", "-l", 0}; 
int main(int argc, char* argv[]){
  int fd = open(argv[1], O_WRONLY | O_CREAT, 0600);
  //fd will be 3; a file will be opened in write mode

  int fd2 = dup(fd); //duplicate the fd-th pointer to entry 4, the lowest available entry

  close(STDOUT_FILENO);
  // the entry 1 is now available(free)

  dup(fd); //duplicate the fd-th pointer into entry 1, "my.dat" become the standard output file

  execvp(cmd[0], cmd); 
  // the old process image is replaced by the new process image for ls
  // the File Descriptor Table is "inherited" by the new process image, 
  // still the same process(PID), but the image is replaced

  close(fd); //close file descriptor 3 in the parent process.
  return; 
}
```

---
### Demo Task 9
```c
#include <stdio.h> 
#include <unistd.h> 
#include <sys/types.h> 
#include <string.h> 
int main(){
  int fd[2]; 
  pipe(fd); //fd[0] is for read and fd[1] is for write
  pid_t child = fork(); 
  char* data = "hello world";
  if (child == 0){ //child process
    close(fd[1]); 
    char buf[100]; //a large enough buffer to share data 
    int bytes_to_read = strlen(data)+1;
    while (bytes_to_read > 0) {
      int count = read(fd[0], buf, sizeof(data)); 
      bytes_to_read -= count;
    }
    printf("child process read: \"%s\" .\n", buf); 
  } else { //parent process
      close(fd[0]); 
      int bytes_to_write = strlen(data)+1;
      while (bytes_to_write > 0) {
        int count = write(fd[1], data, strlen(data)+1)
        // "+1" for null byte, terminateing 0
        bytes_to_write -= count;
      }
      fsync(fd[1]); //flush the data into pipe before close
      printf("parent process written: \"%s\" .\n", data);
      close(fd[1]);
  } 
  return 0;
}
```
