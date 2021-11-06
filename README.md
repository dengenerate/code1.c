# code1.c
#include <stdio.h>
#define MAX_DIGITS 10
#define MAX_ROWS 3
//定全局数组segments并赋初值,初值依据是资料提供的数码管位段。
char segments[10][7] = { {1,1,1,1,1,1},
	{0,1,1},
	{1,1,0,1,1,0,1},
	{1,1,1,1,0,0,1},
	{0,1,1,0,0,1,1},
	{1,0,1,1,0,1,1},
	{1,0,1,1,1,1,1},
	{1,1,1,0,0,0,0},
	{1,1,1,1,1,1,1},
	{1,1,1,1,0,1,1} };
//定义全局数组,用于存放数码显示数据
char digits[MAX_ROWS][MAX_DIGITS * 4];
//一个显示数字8参考输出。供编程参考
void expalent()
{
	printf(" _ \n");
	printf("|_|\n");
	printf("|_|\n\n");
}
void process_digit(int digit, int position);
void print_digits_array(void);
void clear_digits_array(void);
void main()
{
	clear_digits_array();
	process_digit(4, 0);
	process_digit(9, 1);
	process_digit(1, 2);
	process_digit(9, 3);
	process_digit(0, 4);
	process_digit(1, 5);
	process_digit(4, 6);
	process_digit(6, 7);
	print_digits_array();
}
//清除digits数组中所有元素，即给元素赋值为'\0'
void clear_digits_array(void)
{
	int i, j;
	for (i = 0; i < MAX_ROWS; i++)
	{
		for (j = 0; j < MAX_DIGITS * 4; j++)
			digits[i][j] = '\0';//赋值为字符串结束符
	}
}
void process_digit(int digit, int position)
{
	const int pos_len = 4;
	switch (digit)
	{
	case 0:
	case 8:
	case 9:
		digits[0][pos_len * position + 0] = ' ';
		digits[0][pos_len * position + 1] = '_';
		digits[0][pos_len * position + 2] = ' ';
		digits[0][pos_len * position + 3] = ' ';
		digits[1][pos_len * position + 0] = '|';
		digits[1][pos_len * position + 1] = digit == 0 ? ' ' : '_';
		digits[1][pos_len * position + 2] = '|';
		digits[1][pos_len * position + 3] = ' ';
		digits[2][pos_len * position + 0] = digit == 9 ? ' ' : '|';
		digits[2][pos_len * position + 1] = '_';
		digits[2][pos_len * position + 2] = '|';
		digits[2][pos_len * position + 3] = ' ';
		break;
	case 1:
	case 7:
		digits[0][pos_len * position + 0] = ' ';
		digits[0][pos_len * position + 1] = digit == 1 ? ' ' : '_';
		digits[0][pos_len * position + 2] = ' ';
		digits[0][pos_len * position + 3] = ' ';
		digits[1][pos_len * position + 0] = ' ';
		digits[1][pos_len * position + 1] = ' ';
		digits[1][pos_len * position + 2] = '|';
		digits[1][pos_len * position + 3] = ' ';
		digits[2][pos_len * position + 0] = ' ';
		digits[2][pos_len * position + 1] = ' ';
		digits[2][pos_len * position + 2] = '|';
		digits[2][pos_len * position + 3] = ' ';
		break;
	case 2:
		digits[0][pos_len * position + 0] = ' ';
		digits[0][pos_len * position + 1] = '_';
		digits[0][pos_len * position + 2] = ' ';
		digits[0][pos_len * position + 3] = ' ';
		digits[1][pos_len * position + 0] = ' ';
		digits[1][pos_len * position + 1] = '_';
		digits[1][pos_len * position + 2] = '|';
		digits[1][pos_len * position + 3] = ' ';
		digits[2][pos_len * position + 0] = '|';
		digits[2][pos_len * position + 1] = '_';
		digits[2][pos_len * position + 2] = ' ';
		digits[2][pos_len * position + 3] = ' ';
		break;
	case 3:
		digits[0][pos_len * position + 0] = ' ';
		digits[0][pos_len * position + 1] = '_';
		digits[0][pos_len * position + 2] = ' ';
		digits[0][pos_len * position + 3] = ' ';
		digits[1][pos_len * position + 0] = ' ';
		digits[1][pos_len * position + 1] = '_';
		digits[1][pos_len * position + 2] = '|';
		digits[1][pos_len * position + 3] = ' ';
		digits[2][pos_len * position + 0] = ' ';
		digits[2][pos_len * position + 1] = '_';
		digits[2][pos_len * position + 2] = '|';
		digits[2][pos_len * position + 3] = ' ';
		break;
	case 4:
		digits[0][pos_len * position + 0] = ' ';
		digits[0][pos_len * position + 1] = ' ';
		digits[0][pos_len * position + 2] = ' ';
		digits[0][pos_len * position + 3] = ' ';
		digits[1][pos_len * position + 0] = '|';
		digits[1][pos_len * position + 1] = '_';
		digits[1][pos_len * position + 2] = '|';
		digits[1][pos_len * position + 3] = ' ';
		digits[2][pos_len * position + 0] = ' ';
		digits[2][pos_len * position + 1] = ' ';
		digits[2][pos_len * position + 2] = '|';
		digits[2][pos_len * position + 3] = ' ';
		break;
	case 5:
	case 6:
		digits[0][pos_len * position + 0] = ' ';
		digits[0][pos_len * position + 1] = '_';
		digits[0][pos_len * position + 2] = ' ';
		digits[0][pos_len * position + 3] = ' ';
		digits[1][pos_len * position + 0] = '|';
		digits[1][pos_len * position + 1] = '_';
		digits[1][pos_len * position + 2] = ' ';
		digits[1][pos_len * position + 3] = ' ';
		digits[2][pos_len * position + 0] = digit == 5 ? ' ' : '|';
		digits[2][pos_len * position + 1] = '_';
		digits[2][pos_len * position + 2] = '|';
		digits[2][pos_len * position + 3] = ' ';
		break;
	}
}
void print_digits_array(void)
{
	printf("%s\n", digits[0]);
	printf("%s\n", digits[1]);
	printf("%s\n", digits[2]);
	printf("\n");
}
#include<stdio.h>
int main()
{
	char ch = 0;
	while ((ch = getchar()) != EOF)
	{
		putchar(ch);
	}
	return 0;

}


#include<stdio.h>
int main()
{
	int i;
	float score[10];
	float max, min;
	for (i = 0; i<=9; i++)
	{
		scanf_s("%f", &score[i]);
		if (i == 0)
			max = min = score[i];
		else if (score[i] > max)
			max = score[i];
		else if (score[i] < min)
			min = score[i];
	}
	printf("MAX=%6.2f,MIN=%6.2f\n", max, min);
	return 0;
}


#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
int main()
{
	int retain = 0;
	int ch = 0;
	char password[20] = {0};
	printf("PIN:>");
	scanf("%s", password);//缓冲区还有一个'/n'
	while ((ch=getchar()) != '\n')
	{
		;
	}
	printf("PLEASE CONFIRM:(Y/N):>");
	retain = getchar();
	if (retain == 'Y')
		printf("CONFIRM SUCCESSFULLLY");
	else
		printf("YOU ARE FOOL");
}

#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
int main()
{
	char ch;
	scanf("%c", &ch);
	while (ch != EOF)
	{
		if (ch < '0' || ch>'9')
			continue;
		putchar(ch);
		break;
	}
	return 0;
}



#include <stdio.h>
#include <string.h>
int main()
{
char has_this[26]={0};//26个字大写字母
char ch,str[80]={0};
int i=0;
while ((ch = getchar()) != '\n')//从键盘上读取一个字符，如果为回车结束
{
if (ch >= 'A' && ch <= 'Z') 
{
if(has_this[ch-'A']==0)
{
has_this[ch - 'A'] = 1;//ch-'A'获得元素位置
str[i++]=ch;
}
}
}
if(i>0)
{
str[i]='\0';
printf("%s\n", str);
}
return 0;
}




#include <stdio.h>
int main()
{
int a[9];
int i, j, sum = 0;
printf("输入一个3x3矩阵元素:\n");
for (i = 0; i < 3; i++)
{
for (j = 0; j < 3; j++) 
{
scanf("%d", &a[i*3+j]);
if (i == j)// 主对角线位置
sum += a[i*3+j];
}
}
printf("sum=%d\n\n", sum);
return 0;
}


#include <stdio.h>
int main() 
{
int a[10] = { 15,27,31,40,53,66,72,83,96 };
int b, i, j;
printf("原数组元素:");
for (i = 0; i < 9; i++)
printf("%d ", a[i]);
printf("\n输入补插入数:");
scanf("%d", &b);
for (i = 0; i < 9; i++)
{
if (b < a[i])//确定插入位置i
{
//把所有后面的数字后移一位
for (j = 9; j >i; j--)
a[j] = a[j-1];
break;
}
}
a[i] = b;
printf("新元素顺序: ");
for (i = 0; i < 10; i++)
printf("%d ", a[i]);
printf("\n");
return 0;
}

#include<stdio.h>
void main()
{
int a[10],i,m,t;//m最小元素的位置
for(i=0;i<10;i++)
scanf("%d",&a[i]);
for(i=1,m=0;i<10;i++)
{
if(a[m]>a[i])
m=i;
}
if(m!=0)
{
t=a[0];
a[0]=a[m];
a[m]=t;
}
for(i=0;i<10;i++)
printf("%d ",a[i]);
printf("\n");
}


#include<stdio.h>
void main()
{
int a[10],i,m,t;//m最小元素的位置
for(i=0;i<10;i++)
scanf("%d",&a[i]);
for(i=1,m=0;i<10;i++)
{
if(a[m]>a[i])
m=i;
}
if(m!=0)
{
t=a[0];
a[0]=a[m];
a[m]=t;
}
for(i=0;i<10;i++)
printf("%d ",a[i]);
printf("\n");
}

#include <stdio.h>
void main()
{
char str1[80],str2[80];
int i=0;
gets(str1);
do
{
str2[i]=str1[i];
if(str1[i]=='\0')
break;
i++;
}while(1);
printf("\nstr1 is %s\n",str1);
printf("str2 is %s\n",str2);
}


#include <stdio.h>
void main()
{
double ds[5]={0},sum=0;
int i=0;
for(i=0;i<5;i++)
{
scanf("%lf",&ds[i]);
sum+=ds[i];
}
printf("\naverage is %.1f\n",sum/5);
for(i=0;i<5;i++)
printf("%.1f\t",ds[i]);
printf("\n\n");
}


#include <stdio.h>
int main() 
{
int a[5] = { 8,6,5,4,1 };
int i,ex;
printf("原数组元素:");
for (i = 0; i < 5; i++)
printf("%d ", a[i]);
//交换
for (i = 0; i < 5 / 2; i++) 
{
//交换a[i]和a[5-i-1]的值
ex=a[i];
a[i]=a[5-i-1];
a[5-i-1]=ex;
}
printf("\n交换后:");
for (i = 0; i < 5; i++) 
printf("%d ", a[i]);
printf("\n");
return 0;
}





