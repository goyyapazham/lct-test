# lct-test

## Monday 11/17: Signals by Nalanda Sharadjaya
Tech News: [How Twitter Shaped The Election](http://www.nytimes.com/2016/11/09/technology/for-election-day-chatter-twitter-ruled-social-media.html?ref=technology)

### AIM: Are your processes running? Then you should go out and catch them!

### NOTES: 
> First, we learned about **processes**. Every running program is a process. A process can create a subprocess, but they function exactly the same as regular processes do.

> A processor can handle 1 process per cycle (per core). "Multitasking" appears to happen because the processor switches between all the active processes quickly. 

> You can type `ps` in the command line to see all of the processes that your computer is currently running.

`pid`
* Every process has a unique identifier called the PID (Process IDentifier)
* `pid` 1 is the init process
* Each entry in the /proc entry is a current `pid`

`getpid()` - `<unistd.h>` — returns the current process's `pid`

`getppid()` - `<unistd.h>` — return the current process's parent's `pid`

> Then, we learned about **signals**. A signal is a limited way of sending information to a process.

`kill`
* Command line utility to send a signal to process
> $ kill \<PID\>
Sends signal 15 (SIGTERM) to PID
> $ kill -\<SIGNAL\> \<PID\>
Sends SIGNAL to PID

`killall`
> $ killall [-\<SIGNAL\>] \<PROCESS\>
* Sends SIGTERM (or SIGNAL if provided) to all processes with PROCESS as the name

> To handle signals in C programs, we use `<signal.h>`
`kill \<PID\>, \<SIGNAL\>` — returns 0 on success or -1 (errno) on failure

EXAMPLE C CODE:
> static void sighandler (int signo) {
>     if (signo == SIGINT)
>         printf("Nice try!\n");
> }

> int main () {
>     signal(SIGINT, sighandler);
>     while(1) {
>          printf("pid: %d\n", getpid());
>     }
> return 0;
> }
