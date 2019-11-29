# ret2win

# solution

First, just follow the instruction written on the challenge web page, run `nm ./ret2win | grep "ret"` consequently we can see the result show that the function ret2win is at 0x400811.

Thus, what we need to do is to overflow 32 bytes for the fgets buffer, and 8 bytes for the return address.
Unfortunately, we can see that in system execve function call there is `movabs` which will align the address, so if we just set the address 0x400811, which is the instruction of `push rbp`, there will be coming up some troubles.

According to the reason mentioned, I edit the address to the next instruction 0x400812, then it will show the flag successfully.
