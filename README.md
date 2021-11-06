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




#include <stdio.h>
#define S ' '
int main()
{
int n,i,j;
//printf("Enter n:");
scanf(/*BLANK*/"%d",&n/*BLANK*/);//没有判断n的合法性
for(i=1;i<=n;i++)//打印前n行
{
for(j=1;j<=10;j++)//打印每行前面的空格
/*BLANK*/putchar(S) /*BLANK*/;
for(j=1;j<=2*(n-i);j++)//打印每行独有的空格
/*BLANK*/putchar(S) /*BLANK*/;
for(j=1;j<=2*i-1;j++)//打印每行独有的*
/*BLANK*/putchar('*') /*BLANK*/;
printf("\n");
}
for(i=1;i<=n-1;i++)//打印后n-1行
{
for(j=1;j<=10;j++)//打印每行前面的空格
putchar(S);
for(j=1;j<=2*(n-i)-1;j++)//打印每行独有的*
putchar('*');
printf("\n");
}
return 0;
}

#include <stdio.h>
#include <math.h>
int main()
{
int x,flag=1;
//printf("请输入一个5位整数:");
scanf("%d",&x);
if(fabs(x)>99999||fabs(x)<10000)
printf("不是5位整数\n");
if(x<0)//判断负数
{
flag=-1;
x*=-1;//变为正数
}
if(flag<0)
printf("-");
do
{
printf("%d",x%10);
/*BLANK*/x/=10;/*BLANK*/
}while(x>0);
putchar('\n');
return 0;
}

#include <stdio.h>
int main()
{
int i,a,b,c;
for(i=100;i<=999;i++)
{
a=i/100;//百位数字
b=(i-a*100)/10;//十位数字
c=i-a*100-b*10;//个位数字
if(/*BLANK*/i==a*a*a+b*b*b+c*c*c/*BLANK*/)
printf("%d\n",i);
}
return 0;
}

#include <stdio.h>
int main()
{
const int n = 1000;
int i, j, sum;
for (i = 2; i <= n; i++) 
{
sum = 0;
for (j = 1; j < i; j++) 
{
if (i % j == 0) 
sum += j;
}
if (/*BLANK*/sum == i/*BLANK*/)//i是完数
{
printf("%d = ", i);
for (j = 1; j < i; j++) 
{
if (i % j == 0) 
{
if(j==1)
printf("%d",j);
else
printf(" + %d", j);
}
}
printf("\n");
}
}
return 0;
}

#include <stdio.h>
int main()
{
int i,flag=1,c=0;//i循环变量,flag符号标识,c循环计数器
double sum=0,m,z,x;//sum累加值,m分母,z分子,x输入角度
printf("输入角度:");
scanf("%lf",&x); 
x=/*BLANK*/3.1415926*x/180.0/*BLANK*/; //角度转换为弧度
z=x;
m=1.0;
for(i=1 ; ; i+=2)
{
c++;
sum=/*BLANK*/sum+flag*z/m/*BLANK*/;//计算项的累计和
if(z/m < 1.0e-6)//判断精度
break;
z=/*BLANK*/z*x*x/*BLANK*/;//下项的分子
m=m*(i+1)*(i+2);//下项的阶乘值
flag*=-1;//下项的符号
}
printf("count=%d\nsin(%f)=%f\n",c,x,sum);
return 0;
}
#include <stdio.h>
int main()
{
int m,n,i,gys=0;
//printf("输入两个正整数:");
scanf("%d%d",&m,&n);
for(i=1;i<=m&& i<=n;i++)
{
if(/*BLANK*/m%i==0 && n%i==0/*BLANK*/)
gys=i;
}
printf("%d,%d的最大公约数为%d,最小公倍数为%d\n",m,n,gys,m*n/gys);
return 0;
}

#include <stdio.h>
int main()
{
/*BLANK*/double sum = 0/*BLANK*/;
int k;
for (k = 1; k <= 100; k++)
{
/*BLANK*/sum += k/*BLANK*/;
}
for (k = 1; k <= 50; k++) 
{
/*BLANK*/sum += (k * k)/*BLANK*/;
}
for (k = 1; k <= 10; k++)
{
/*BLANK*/sum += (1.0 / k)/*BLANK*/;
}
printf("%lf\n", sum);
return 0;
}
#include <stdio.h>
int main()
{
long int x,i,j;
//printf("pls input x:");
scanf("%d",&x);//没有判断x的合法性
for(i=1;i<=x/2;i++)
{
for(j=i+1;j<=x/2+1;j++)
{
if(/*BLANK*/(i+j)*(j-i+1)/2/*BLANK*/==x)//由等差数列和公式得到此判断条件
{
printf("%d+...+%d=%d\n",i,j,x);
break;
}
}
}
return 0;
}
#include <stdio.h>
int main()
{
int x,sum=0,c=0;
printf("请输入一个整数:");
scanf("%d",&x);
if(x<0)
x*=-1;
while(x!=0)
{
sum+=/*BLANK*/x%10/*BLANK*/;
if(c==0)
printf("%d",x%10);
else
printf(" + %d",x%10);
c++;
x/=/*BLANK*/10/*BLANK*/;
}
printf(" = %d\n",sum);
return 0;
}


#include <stdio.h>
int main()
{
int i;
i=0;
do
{
if(/*BLANK*/i%2==1 && i%3==2 && i%5==4 && i%6==5 && i%7==0/*BLANK*/)
break;
i++;
}while(1);
printf("最少梯数为:%d\n",i);
return 0;
}


#include <stdio.h>
#define RS 3
#define WS 3
#define BS 6
#define EQU 8
int main()
{
int r,w,b,count=0;
for(b=0;b<=BS;b++)//黑球取数范围
{
for(r=0;r<=RS;r++)//红球取数范围
{
for(w=0;w<=WS;w++)//白球取数范围
if(/*BLANK*/w+r+b/*BLANK*/==EQU)
count++;
}
}
printf("合符要求的搭配数%d\n",count);
return 0;
}

#include <stdio.h>
int main()
{
int i;
double z=2.0,m=1.0,sum=0.0,tmp;
for(i=0;i<20;i++)
{
sum+=z/m;//当前项值累加
tmp=z;//把分子暂存
z=/*BLANK*/z+m/*BLANK*/;//下一项分子
m=tmp;//下一项的分母(原分子变分母)
}
printf("前20项和%f\n",sum);
return 0;
}


#include <stdio.h>
int main()
{
int s,count=0,Items;//项值、输出项数计数、给定项数
int i, j;//循环变量
scanf("%d",&Items);//输入项数
for (i = 1,s=1; count<Items; s = 1, i++)//行数i从1开始
{
printf("%d ",s);//每行的第一项1
count++;
for (j = 1; j < i && count<Items ; j++)//列位置j绕过第一个直接开始循环
{
s = /*BLANK*/(i - j) * s/j/*BLANK*/;//通项公式,s-前项值
printf("%d ", s);
count++;//输出项计数
}
printf("\n");
if(count>=Items)
break;
}
return 0;
}

#include <stdio.h>
int main()
{
int i,j,k,count=0;
for(i=1;i<=100/3;i++)//大马
{
for(j=1;j<=100/2;j++)//中马
{
k=100-i-j;//小马数
if(i*3+j*2+k/2==100 && k%2==0)//货物总数，两匹小马驮一担
{
count++;
//printf("大马 %d, 中马 %d, 小马 %d\n",i,j,k);
}
}
}
printf("共有组合模式: %d\n",count);
return 0;
}

#include <stdio.h>
int main()
{
int x,y,min=133,finalx,finaly,t;
for(x=1;x<=133/19+1;x++)//19米的
{
for(y=1;y<=133/23+1;y++)//23米的
{
t=133-x*19-y*23;//剩余长度
if(t<min && t>=0)
{
min=t;
finalx=x;
finaly=y;
}
}
}
printf("19米段数:%d\n23米段数:%d\n余段长度:%d\n",finalx,finaly,min);
return 0;
}
#include <stdio.h>
void main()
{
double score=0,sum=0,min,max;
int count=0;
do
{
scanf("%lf",&score);
if(score>=0.0)
{
sum+=score;
if(count==0)
min=max=score;
else
{
if(score<min)
min=score;
if(score>max)
max=score;
}
count++;
}
}while(count<7);//负数作为输入结束
if(count>2)
printf("评分个数%d,平均分%f\n",count,(sum-max-min)/(count-2));
else
printf("评分个数小于3!不符合评分条件!\n");
}


#include <stdio.h>
int main()
{
int i,a,n,t,sum=0;
printf("input a and n:");
scanf("%d%d",&a,&n);//
for(t=0,i=1;i<=n;i++)//i项序号
{
t=t*10+a;//t为零时变量，来存储a0,a00,a00...
if(i==1)
printf("Sn=%d ",t);
else
printf("+ %d",t);
sum+=t;
}
printf(" = %d\n",sum);
return 0;
}

#include <stdio.h>
int main()
{
int n = 10;
double sum = 0, length = 100;
int i;
for (i = 0; i < n; i++)
{
sum += length;//落地过程行程和
length /= 2.0;//弹起过程
if (i != n - 1)//最后一次反弹不算入总行程
sum += length;
}
printf("sum=%lf, length=%lf\n", sum, length);
return 0;
}

#include <stdio.h>
int main()
{
int i,A,B,C,D;
for(i=1000;i<=9999;i++)
{
A=i/1000;//千位数字
B=(i-A*1000)/100;//百位数字
C=(i-A*1000-B*100)/10;//十位数字
D=i-A*1000-B*100-C*10;//个位数字
if(i-(C*100+D*10+C)==A*100+B*10+C)
printf("%6d\n-%5d\n------\n%6d\n",i,(C*100+D*10+C),A*100+B*10+C);
}
return 0;
}




#include <stdio.h>
int main()
{
int day;
double earn=0;
double pay=0,total=0;//记富翁付出的钱
for(day=0,pay=0.01,earn=0;day<30;day++)
{
total+=pay;//富翁总付出
earn=earn+100000;//穷人付出
pay=pay*2;//富翁后一天应付出
}
printf("%d天后富翁:\n得到:%11.2f\n付出:%11.2f\n损失:%11.2f\n", day,earn,total,total-earn);
return 0;
}

#include <stdio.h>
int main()
{
int i,n;
printf("pls input n: ");
scanf("%ld",&n);
while(n>1)
{
for(i=2; ;i++)//无循环条件即为真
{
if(n%i==0)//i是n的因子
{
printf("%d ",i);
n=n/i;
break;
}
}
}
printf("\n");
return 0;
}



#include <stdio.h>
void main()
{
	double loan,rate,payment,tmp;
	printf("Enter amount of loan: ");
	scanf("%lf",&loan);
	printf("Enter interest rate: ");
	scanf("%lf",&rate);
	printf("Enter monthly payment: ");
	scanf("%lf",&payment);
	loan=loan+loan*rate/100.0/12-payment;
	printf("\nBalance remaining after first payment: $%.2f\n",loan);
	loan=loan+loan*rate/100.0/12-payment;
	printf("Balance remaining after second payment: $%.2f\n",loan);
	loan=loan+loan*rate/100.0/12-payment;
	printf("Balance remaining after third payment: $%.2f\n",loan);
}

#include <stdio.h>
void main()
{
	int y,m,d;
	printf("Enter a date (mm/ad/yyyy):");
	scanf("%d/%d/%d",&m,&d,&y);
	printf("You entered the date %4d%02d%02d\n",y,m,d);
}

#include <stdio.h>
void main()
{
	int ItemNo,year,month,day;
	double price;
	printf("Enter item nummber:");
	scanf("%d",&ItemNo);
	printf("Enter unit price: ");
	scanf("%lf",&price);
	printf("Enter purchase date (mm/ dd/yyyy): ");
	scanf("%d/%d/%d",&month,&day,&year);
	printf("Item\tUnit\tPurchase\n");
	printf("\tPrice\tDate\n");
	//一个制表宽度是8个字符
	printf("%d\t%7.2f\t%d/%d/%d\n",ItemNo,price,month,day,year);
}


#include <stdio.h>
void main()
{
	int part1,part2,part3,part4,part5;
	printf("Enter ISBN: ");
	scanf("%d-%d-%d-%d-%d",&part1,&part2,&part3,&part4,&part5);
	printf("GS1 prefix:%d\n",part1);
	printf("Group identifier:%d\n",part2);
	printf("Publisher code: %d\n",part3);
	printf("Item number: %d\n",part4);
	printf("Check digit: %d\n",part5);
}


#include <stdio.h>
void main()
{
	int part1,part2,part3;
	printf("Enter phone number [(xxx)xxx-xxxx]: ");
	scanf("(%3d)%3d-%4d",&part1,&part2,&part3);
	printf("\nYou entered %03d.%03d.%04d\n",part1,part2,part3);
}

#include <stdio.h>
void main()
{
	int in1,in2,in3,in4,in5,in6,in7,in8,in9,in10,in11,in12,in13,in14,in15,in16;
	int Row1,Row2,Row3,Row4;
	int Col1,Col2,Col3,Col4;
	int Dia1,Dia2;
	printf("Enter the numbers from 1 to 16 in any order :\n");
	scanf("%d%d%d%d%d%d%d%d%d%d%d%d%d%d%d%d",&in1,&in2,&in3,&in4,&in5,&in6,&in7,&in8,	&in9,&in10,&in11,&in12,&in13,&in14,&in15,&in16);
	Row1=in1+in2+in3+in4;
	Row2=in5+in6+in7+in8;
	Row3=in9+in10+in11+in12;
	Row4=in13+in14+in15+in16;
	Col1=in1+in5+in9+in13;
	Col2=in2+in6+in10+in14;
	Col3=in3+in7+in11+in15;
	Col4=in4+in8+in12+in16;
	Dia1=in1+in6+in11+in16;
	Dia2=in4+in7+in10+in13;
	printf("Row sums:%6d%6d%6d%6d\n",Row1,Row2,Row3,Row4);
	printf("Column sums:%6d%6d%6d%6d\n",Col1,Col2,Col3,Col4);
	printf("Diagonal sums:%6d%6d\n", Dia1,Dia2);
}

#include <stdio.h>
int main()
{
	int a,b,c,d;
	printf("Enter two fractions separated by a plus sign:");
	scanf("%d/%d+%d/%d",&a,&b,&c,&d);
	printf("The sum is %d/%d\n",(a*d+c*b),(b*d));
}




