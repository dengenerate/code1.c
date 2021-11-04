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
