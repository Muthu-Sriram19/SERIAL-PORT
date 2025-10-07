
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```MUTHU.A51

ORG 00H 
MOV TMOD, #20H 
MOV TH1, #0FDH 
MOV SCON, #50H 
SETB TR1 
MAIN_LOOP:
MOV SBUF, #'B' 
WAIT_TI:
JNB TI, WAIT_TI 
CLR TI 
END

MUTHU.c

#include<reg51.h>
void main(void)
{
TMOD=0X20;
TH1=0XFA;
SCON=0X50;
TR1=1;
while(1)
{
SBUF='A';
while(T1==0);
T1=0;
}
}


```
### (ii) Serial Port to Transfer a Message

```MUTHU.C

#include<reg51.h>
void main(void)
{
unsigned char msg[]="MUTHU";
unsigned char i;
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFA;
SCON=0X50;
TR1=1;
for(i-0;i<=12;i++)
{
SBUF=msg[i];
while(TI==0);
TI=0;
}
while(1);
}

MUTHU.A51

ORG 0000H
MOV TMOD, #20H
MOV TH1, #OFDH
MOV SCON, #50H
SETB TR1
MOV A ,#'T'
ACALL TRANS
MOV A ,#'A'
ACALL TRANS
MOV A, #'N'
ACALL TRANS
MOV A, #'U'
ACALL TRANS
MOV A , #'J'
ACALL TRANS
SJMP $
TRANS: MOV SBUF, A
WAIT: JNB T1, WAIT
CLR T1
RET
END



```

### OUTPUT:
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/05141ae9-c4b8-497e-aae2-7a82cf3e3664" />
![WhatsApp Image 2025-10-07 at 22 26 29_114ccaa8](https://github.com/user-attachments/assets/ecb63e50-a2e6-49ab-bbd5-4794e990252b)


### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
