# Internship_Task_2
**IN this task we debug the Assembly code(which is)**
```
Disassembly of section .text:

00000000000100b0 <main>:
   100b0:       00021537                lui     a0,0x21
   100b4:       ff010113                addi    sp,sp,-16
   100b8:       00f00613                li      a2,15
   100bc:       00500593                li      a1,5
   100c0:       18050513                addi    a0,a0,384 # 21180 <__clzdi2+0x48>
   100c4:       00113423                sd      ra,8(sp)
   100c8:       340000ef                jal     ra,10408 <printf>
   100cc:       00813083                ld      ra,8(sp)
   100d0:       00000513                li      a0,0
   100d4:       01010113                addi    sp,sp,16
   100d8:       00008067                ret

```
***
***this is the snapshot of the code***
***
![task ii1](https://github.com/user-attachments/assets/827c9e0e-89da-454c-83b8-03589c11ea14)
***
**A DEBUGGER WAS RUN** 
***
``` spike -d pk vardan.c ``` 

![task 2](https://github.com/user-attachments/assets/f45f4eec-ea38-41b0-a278-f657858319f1)

**.**


This code helps us to debug the code in assembly for every a and how many times it was used eg. a0,0x21,and for each reg we get the values

***

***
**CHECK FOR REG SP BEFORE AND AFTER -16**
***
***as in code , sp has its own reg and it has got -16, we check for the hexa decimal befor and after -16***

***the code***


``` 100b4:       ff010113                addi    sp,sp,-16 ```


![task 3](https://github.com/user-attachments/assets/b34c744c-da05-4a57-abcc-7cfe6b43024e)
