---
title: 编程例题
date: 2023-10-19 12:20:44
tags:
---
  ### C语言
 1. 求两个整数的最大公约数和最小公倍数
 随便假设一个数 m 为 a 与 b 的最大公约数，则 a 与 b 的最小公倍数为 a*b/m。
程序如下：
/* 该程序是通过两数每次都模上最大数减一直到减到 1，如果之中有一个数 i 能符合被两数同时模上后为 0，则说明该数 i 是起的最大公约数 */ 
        ①#include<stdio.h>
        void main ()
        {
            int a,b,i;
            scanf ("% d,% d",&a,&b);
            if (a>b)
            {
                i=b;
                b=a;
                a=i;
            }
        for (i=a;i>=1;i--)
            if (a% i==0&&b% i==0)
            {
            printf ("它们的最大公约数为 % d\n",i);
            break; 
            }

        } 
②辗转相除法（求最大公约数）
        #include<stdio.h>
        void main ()
        {
            int p,r,a,b,temp;
            printf ("请输入两个正整数：");
            scanf ("% d,% d",&a,&b);
            if (a>b)
            {
                temp=b;
                b=a;
                a=temp;

            }
            p=b*a;//a 和 b 的乘积除以其最大公约数，就是最小公倍数。
            while (a!=0)
            {
                r=b% a;
                b=a;
                a=r;

                }
                printf ("它们的最大公约数为：% d\n",b);
                printf ("它们的最小公倍数为：% d\n",p/b);
            }
2. 输出如下金字塔型数字
            #include<stdio.h>
            void main ()
            {
            int i,j,k;
            for (i=1;i<10;i++)
            {
                for (j=10;j>i;j--)
                    printf (" ");// 输入空格

                for (k=1;k<=i;k++)
                    printf ("% c",48+k);

                for (k=i;k>1;k--)
                printf ("% c",48+k-1);

                printf ("\n");        

            }

            }    
图示

3. 译密码（顺移四个字母依次，W-Z 顺移至 A-D）
            ①#include<stdio.h>
            void main ()
            {
                char c;
                c=getchar ();// 输入单字母
                while (c!='\n')// 字母存在（循环）
            {
                if ((c>='a'&&c<='z')||(c>='A'&&c<='Z'))
            {
                    if ((c>='w'&&c<='z')||(c>='W'&&c<='Z'))
                        c=c+4-26;
                    else
                    c=c+4;   
            }
            printf ("% c",c);
            c=getchar ();// 输入下一个

        }   

        }
        ②#include<stdio.h>
        void main ()
        {
            char c;
            while ((c=getchar ())!='\n')// 特别注意 (c=getchar ()) 是一个整体，是整体不等于 '\n'
            {
        if (c>='A'&&c<='Z')
            c=(c-'A'+4)%26+'A';
        else if (c>='a'&&c<='z')
            c=(c-'a'+4)%26+'a';
        printf ("%",c);        

        }

        }
        ③#include<stdio.h>
        void main ()
        {   
        char c;
        while ((c=getchar ())!='\n') 
        {
       if ((c>='A'&&c<='Z')||(c>='a'&&c<='z'))
       {
           c=c+4;// 注意此处已经加上了 4
           if (c>='Z'&&c<='Z'=4||c>'z')
           {
               c=c-26;
           }
       }
       printf ("% c",c);

        }  

        }
4. 字符统计，输入一行字符，分别统计出其中的英文字母、空格、数字和其它字符的个数。
        ①#include<stdio.h>
            void main ()
        {
            int z,k,s,q;
            char ch;
            z=k=s=q=0;
            ch=getchar ();
            while (ch=!'\n')
        {
            if (ch>='a'&&ch<='z'||ch>='A'&&ch<='Z')
            z++;
            else if (ch==' ')
            k++;
            else if (ch>='0'&&ch<='9')
            s++;
            else q++;
            ch=getchar ();      
        }
        printf ("字母：% d\n，空格：% d\n，数字：% d\n，其它：% d\n",z,k,s,q);
    }
        ②for (ch=getchar ();ch!='\n';)// 另一种检测方法
        {
            if (ch>='a'&&ch<='z'||ch>='A'&&ch<='Z')
            {
                z++;
            else if (ch==' ')
                k++;
            else if (ch>='0'&&ch<='9')
                s++;
            else q++;
                ch=getchar ();   
        }   
        }
        ③while (   (ch=getchar ())   !='\n') //"!=" 优先级大于 "="
        {
            if (ch>='a'&&ch<='z'||ch>='A'&&ch<='Z')
                z++;
            else if (ch==' ')
                k++;
            else if (ch>='0'&&ch<='9')
                s++;
            else q++;         

        } 
5. 编程输出 n-m 中（0<n<m）能被 3 整除，且至少有一个数字是 5 的所以有数。
        #include<stdio.h>
        void main ()
        {
            long i,m,x,t,n;
            int z;
            scanf ("% ld% ld",&n,&m);
            if (n>m)
    {
        z=n;
        n=m;
        m=z;
    }
    if (n==m)
    {
      printf ("请重新输入：");
      scanf ("% ld% ld",&n,&m);
    }
    for (i=n;i<=m;i++)
    {
        if (i%3==0)
        {
            x=i;
            while (x)
            {
                t=x%10;
                if (t==5)
                {
                   printf ("% ld\n",i)
                   break;
                }
                x=x/10;
            }
        }
    } 
} 
6.穷举法
 编程求 1000 以内的完数 完数就是其真因子的和等于其本身的数
。
        #include<stdio.h>
        void main ()
            {
        int i,j,s;
        for (i=1;i<=1000;i++)
    {
        s=0;
        for (j=1;j<i;j++)
       {
           if (i% j==0)
           {
               s+=j;
           } 
       }
       if (s==j)
           {
               printf ("% d\n",i);
           }
    } 
    }  
    
   ### 微机原理     
二、微机原理区
1. 实现内存中三个数的加法运算
    DATA SEGMENT
    M1 DB 34H,56H,78H ; 定义内存中的数据
    DATA ENDS
    CODE SEGMENT      ; 代码段
            ASSUME DS:DATA ; 把 DATA 这个段声明为数据段
            ASSUME CS:CODE
    START:
            MOV AX,DATA
            MOV DS,AX      ; 把 DATA 的段基值存入相应数据段寄存器 DS 中
            LEA BL,[DI]
            MOV CL,[DI+1]
            MOV DL,[DI+2]
                ADD BL,CL
            ADC BL,DL
    CODE ENDS
        END START  
2. 编写程序，实现把一个内存中 16 位的数的位 3 和位 7 置 1 后回写到原存储单元。
        DATA SEGMENT
        M1  DW 1234H
        DATA ENDS
    CODE SEGMNET
        ASSUME DS:DATA,CS:CODE
    START:
        MOV AX,DATA
        MOV DS,AX
        XOR AX,AX; 清零
        MOV AX,M1
        MOV CX,88H
        OR  AX,CX
        MOV M1,AX
    CODE ENDS
        END START
3. 在内存单元 TAB1 开始中有一个字符串，长度为 CN CN>5
。编写程序找出这个字符串是否有 ‘C’ 出现，若有，在 TAB2 中存 “Y”，否则在 TAB2 中存 “N”。
    DATA SEGMENT
    TAB1 DB 'ASDWEDSAC'
    TAB2 DB ''
    DATA ENDS
    CODE SEGMENT
    ASSUME DS:DATA,CS:CODE
    START:
        MOV AX,DATA
        MOV DS,AX
        LEA BX,TAB1
        MOV CX,9
    LP: MOV AL,[BX]
        INC BX
        CMP AL,'C'; 不等于跳转
        LOOPNZ LP
        JZ LP2
        MOV TAB2,'N'
        JMP END
    LP2:MOV TAB2,'Y'
    END:HLT
        CODE ENDS
    END START        
4. 试编制程序段实现求 | X+Y|×|X-Y | 并将结果存入内存。其中 X 和 Y 是内存数据段 DATA 中字节单元无符号数。
    DATA SEGMENT
        M1 DB 11H;X
        M2 DB 22H;Y
        M3 DW 1122H;Z
    DATA ENDS
    CODE SEGMENT
        ASSUME CS:DATA,DS:DATA
    START:
        MOV AX,DATA
        MOV DS,AX

        LEA SI,M1
        LEA DI,M2

        MOV AL,[SI]
        MOV BL,[DI]
        ADD AL,BL
        MOV CL,AL;|X+Y|
        SUB AL,BL; 前面加过了再减去 bl
        CMP AL,BL
        JAE JUMP1
        JB  JUMP2
    JUMP1: SUB AL,BL;|X-Y|
        MUL CL
        MOV M3,AX
        JMP END
    JUMP2: SUB BL,AL;|Y-X|
        MUL CL
        MOV M3,AX
    END:MOV AH,4CH
        INT 21H
        CODE ENDS
    END START             
5. 编制程序实现将首地址为 STR、长度为 10 的字符串顺序颠倒，例如原串为 abcdefghij，变换后为 jihgfedcba。
        DATA SEGMENT
        STR DB 'ABCDEFGHIJ'
        DATA ENDS
        CODE SEGMENT
        ASSUME CS:CODE,DS:DATA
        START:
        MOV AX,DATA
        MOV DS,AX

        LEA SI,STR
        LEA DI,STR+9
        MOV CX,5
        MOV AX,0
        NEXT: MOV AL,[SI]
        MOV BL,[DI]
        MOV [SI],BL
        MOV [DI],AL
        INC SI
        DEC DI
        DEC CX
        JNZ NEXT

        MOV AH,4CH
        INT 21H
        CODE ENDS
    END START
6. 试编制程序段实现求 | X+Y|×|X-Y | 并将结果存入内存。其中 X 和 Y 是键盘输入数据。假设输入两个两位数
    DATA SEGMENT
        M1  DB  'X:$'
        M2  DB  'Y:$'
        ENT DB  0AH,0DH,'$'
        X   DB  5,0,5 DUP (0),'$'
        Y   DB  5,0,5 DUP (0),'$'
        Z   DW  0
    DATA ENDS
    CODE SEGMENT
        ASSUME  CS:CODE,DS:DATA
    START:
     MOV AX,DATA
     MOV DS,AX

     LEA DX,M1
     MOV AH,9
     INT 21H

     MOV DX,OFFSET X
     MOV AH,10
     INT 21H

     LEA DX,ENT
     MOV AH,9
     INT 21H

     LEA DX,M2
     MOV AH,9
     INT 21H

     MOV DX,OFFSET Y
     MOV AH,10
     INT 21H

     LEA DX,ENT
     MOV AH,9
     INT 21H 

     MOV DI,OFFSET X+2
     MOV AL,[DI]
     MOV CL,4
     SHL AL,CL
     MOV BL,[DI+1]
     AND BL,0FH
     ADD AL,BL
     MOV DX,0
     AND AX,0FFH
     MOV DX,AX         ;X
     AND AL,0F0H
     MOV CX,AX
     SHR CX,1
     SHR CX,1
     SHR CX,1
     SHR CX,1
     DEC CX
     SUB DX,6 

     CMP DX,14H        ; 自动判断循环几位
     JB NEXT
  J1:SUB DX,6 
     LOOP J1


    NEXT: MOV SI,OFFSET Y+2
        MOV AL,[SI]
        MOV CL,4
        SHL AL,CL
        MOV BL,[SI+1]
        AND BL,0FH
        ADD AL,BL
        AND AX,0FFH         ;Y 
        MOV BL,AL
        AND BL,0F0H
        MOV CL,BL
        SHR CX,1
        SHR CX,1
        SHR CX,1
        SHR CX,1
        DEC CL
        SUB AX,6

        CMP AX,14H
        JB  NEXT1          ; 自动判断循环几位
        J2:SUB AX,6  
        LOOP J2 

    NEXT1: ADD DX,AX
     MOV BX,0
     MOV BX,DX ;|X+Y|
     SUB DX,AX

     CMP DX,AX
     JA L1
     SUB AX,DX;Y>X 
     AND AX,0FFH
     MOV DH,0
     MUL BX

     MOV WORD PTR Z,AX
     MOV WORD PTR Z+16,DX
     JMP END
    L1:SUB DX,AX ;X>Y 
     AND AX,0FFH
     MOV AX,DX
     MOV DH,0
     MUL BX
     MOV WORD PTR Z,AX
     MOV WORD PTR Z+16,DX
    END:
       MOV AH,4CH
       INT 21H
    CODE ENDS
    END START
