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
![task ii1](https://github.com/user-attachments/assets/2896d669-089b-4e4d-9cd3-df33e203daa7)

***
**A DEBUGGER WAS RUN** 
***
``` spike -d pk vardan.c ``` 

![task 2](https://github.com/user-attachments/assets/1fedb105-f08b-4a4f-a21b-2257525baf39)


**.**


This code helps us to debug the code in assembly for every a and how many times it was used eg. a0,0x21,and for each reg we get the values

***

***
**CHECK FOR REG SP BEFORE AND AFTER -16**
***
***as in code , sp has its own reg and it has got -16, we check for the hexa decimal befor and after -16***

***the code***


``` 100b4:       ff010113                addi    sp,sp,-16 ```


![task 3](https://github.com/user-attachments/assets/2649f2a1-f79e-42c7-80f1-4cc563b75515)

***
***

***calculation for sp***
* 1


![taskkkkkkkkkk](https://github.com/user-attachments/assets/fbe3ff99-192a-402a-8743-5ca0c45e10ff)
***
* 2


![task 2](https://github.com/user-attachments/assets/06f2b8c1-caea-4d58-a601-54eae658cb34)
***
* 3



![task 3](https://github.com/user-attachments/assets/6faaff4d-da14-4015-9975-76f2447ec01f)


----------------------------------------------------------------------------------------------------------------------------
***
**CREATING A NEW C CODE AND RUNNING THROUGH RISCV COMPILER**
***
**CHECKING CODE FIRST USING ./A.OUT** 

![edit 1](https://github.com/user-attachments/assets/aa56362e-d925-46f4-b9a3-0678b836a882)

***

**COMPILING THROUGH RISCV**

![extra 2](https://github.com/user-attachments/assets/2383ac8a-7ee6-4197-9216-08eb054d65c8)



``` spike pk v2.o ``` **was the code used**


***

**DOING DEBUG**

![extra 3](https://github.com/user-attachments/assets/0bb1ef8e-a44f-4070-a207-8ea2c5cdf3fb)
