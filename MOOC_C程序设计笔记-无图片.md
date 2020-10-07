---
title:
tags:
notebook:C Programming
---

# MOOC浙大翁凯C语言程序设计

## 目录

[TOC]

### 1.1 第一个程序

#### Hello word!

```c
#include <stdio.h>

int main() {
    // insert code here...
    printf("Hello, World!\n");
    return 0;
}
```

==程序写的顺序是运行步骤，不是逻辑关系的比较==

#### 注释

单行注释：//

多行注释：/*   */

#### 缩进

c语言编译器是不管空格，回车，缩进的，每句代码都只认“;”结尾。

### 2.1 变量

### 2.2 表达式

#### 编程练习解析

**例题一：厘米换算英尺英寸**

如果已知英制长度的英尺foot和英寸inch的值，那么对应的米是( foot + inch/12 ) * 0.3048。现在，如果用户输入的是厘米数，那么对应英制长度的英尺和英寸是多少呢？别忘了一英尺等于12英寸。

**输入格式：**

输入在一行中给出一个正整数，单位是厘米。

**输出格式：**

在一行中输出这个厘米数对应英制长度的英尺和英寸的整数值，中间用空格分开。

**输入样例：**

170

**输出样例：**

5  6

```c
#include <stdio.h>

int main()
{
	int cm = 0;
    scanf("%d", &cm);  //scanf里面的字符串的输入格式有严格要求

    int foot = cm / 30.48;	//会自动将浮点型值变成整型存入foot
    int inch = ((cm / 30.48) - foot) * 12;	//小数部分成12就是inch的值 
  
	printf("%d %d\n", foot, inch);
	return 0;
}
```

**例题二：然后是几点**

如果1106表示11点零6分。如果1106表示11点零6分。现在，编写程序根据起始时间和流逝时间计算出终止时间。读入两个数字，第一个数字以这样的四位数表示当前时间，第二个数字表示流逝时间，计算当前时间经过那么多时间后是几点，结果也表示为四位数字。当小时为个位数时，没有前导的零，即5点30分表示为530。注意，第二个数字表示分钟数可能超过60，也可能是负数。

**输入格式：**

输入在一行中给出两个整数，分别是四位数字表示的起始时间，以及流逝的分钟数，其间以空格间隔。注意：在起始时间中，当小时为个位数时，没有前导的零，即5点30分表示为530。注意，第二个数字表示分钟数可能超过60，也可能是负数。

**输出格式：**

输出四位数字表示终止时间。题目保证起始时间和终止时间在同一天内。

**输入样例：**

1120  110

**输出样例：**

1310

```c
#include <stdio.h>

int main()
{
	int start = 0;
    int t = 0;
    scanf("%d %d", &start, &t);  

    int hour = start / 100;
    int minutes = start % 100;
    start = hour * 60 + minutes;	//将初始时间转换成分钟数

    int end = start + t;	//计算终止时间的分钟数

    int t1 = end / 60;	//计算小时
    int t2 = end % 60;	//计算分钟

    end = t1 * 100 + t2;	//将小时和分钟组成四位数字
 
	printf("%d\n", end);
	return 0;
}
```

**例题三：逆序的三位数**

程序每次读入一个正三位数，然后输出按位逆序的数字。注意：当输入的数字含有结尾的0时，输出不应该带有前导的0。比如输入700，输出应该是7。

**输入格式：**

每次测试是一个3位的正整数。

**输出格式：**

输出按位逆序的数。

**输入样例：**

123

**输出样例：**

321

```c
#include <stdio.h>

int main() 
{
    int x = 0;
    scanf("%d", &x); 

    int a = x / 100;    //取百位数
    int c = x % 10;     //取个位数
    int b = (x % 100) / 10;     //取十位数

    int result = c * 100 + b * 10 + a;	//组成逆序数

    printf("%d\n", result);
    return 0;
}

```

**例题四：BCD**

将符合要求的十进制数转换为BCD码。

**输入格式：**

输入在一行中给出一个在[0，153]范围内的正整数，保证其能有效的转换为BCD数，也就是说这个整数在转换成十六进制数时不会出现A~F的数字。

**输出格式：**

输出对应的十进制数。

**输入样例：**

18

**输出样例：**

12

+ 方法一：

```c
#include <stdio.h>

int main() 
{
    int x = 0;
    scanf("%d", &x);	//以十进制的数读入
    printf("%x\n", x);	//以十六进制的数输出
    return 0;
}
```

+ 方法二：

```c
#include <stdio.h>

int main() 
{
    int x = 0;
    scanf("%d", &x);	//以十进制的数读入

    int a = x / 16;	//取十六进制十位数
    int b = x % 16;	//取十六进制个位数
    
    printf("%d\n", a*10+b);	
    return 0;
}
```

### 3.1 判断

#### if判断

```c
if(条件成立){
    ......
}
```

#### 关系运算

计算两个值之间的关系，叫做关系运算。关系运算的结果只可能是1或0，不会出现其他值。

| 运算符 |    意义    |
| :----: | :--------: |
| **==** |    相等    |
| **!=** |   不等于   |
| **>**  |    大于    |
| **>=** | 大于或等于 |
| **<**  |    小于    |
| **<=** | 小于或等于 |

**优先级**：

+ 所有关系运算符的优先级比算数运算符低，但是比赋值运算高；

```c
7 >= 3 + 4;	//值为1
int r = a > 0;	//先计算a>0的值，再赋给r
```



+ 判断是否相等的==和!=的优先级比其他的低，而连续的关系运算是从左到右进行的。

```c 
5 > 3 == 6 > 4;	//先计算5>3和6>4，再做比较
6 > 5 > 4;	//先算6>5的值为1，在算1>4的值，为0
a == b == 6; //先计算a和b是否相等，相等为1，不等为0；再将0或1与6比较
a == b > 0;	//	先计算a和b是否相等，相等为1，不等为0；再将0或1与0比较
```

#### else

**找零计算器**

```c
#include <stdio.h>

int main() 
{
    //  初始化
    int price = 0;
    int bill = 0;
    //  读入金额和票面
    printf("请输入金额：");
    scanf("%d", &price);
    printf("请输入票面：");
    scanf("%d", &bill);
    //  计算并打印找零
    if (bill >= price) {
        printf("应该找您：%d元。\n", bill-price);
    } else {
        printf("你的钱不够。\n");
    }
    
    return 0;
}
```

**比较两个数的大小**

+ 方案一：

```c
	int a, b;

	printf("请输入两个整数：");
	scanf("%d %d", &a, &b);

	int max = 0;
	if (a > b) {
		max = a;
	} else {
		max = b;
	}

	printf("大的那个是%d。\n", max);
```

+ 方案二

```c
	int a, b;

	printf("请输入两个整数：");
	scanf("%d %d", &a, &b);

	int max = b;
	if (a > b) {
		max = a;
	} 

	printf("大的那个是%d。\n", max);
```

#### if-else注意点

==if和else后面可以没有大括号{}，此时紧跟在if或else后面的那句就是条件成立时所要执行的代码。if后面的( )不能直接加分号”；“==

**计算薪水**

```c
#include <stdio.h>

int main()
{
	const double RATE = 8.25;	//每小时工资为8.25元
	const double STANDARD = 40;	//每周工作40个小时
	double pay = 0.0;
	int hours;

	printf("请输入工作的小时数：");
	scanf("%d", &hours);
	printf("\n");
	if (hours > STANDARD)
		pay = STANDARD * RATE + 
			(hours - STANDARD) * (RATE * 1.5);	//基本工资+1.5倍加班工资
	else
		pay = hours * RATE;
	printf("应付工资：%f\n", pay);

	return 0;
}
```

### 3.2 分支

#### 嵌套的if-else

**三个数比较大小**

```c
#include <stdio.h>

int main()
{
	int a, b, c;
	scanf("%d %d %d", &a, &b, &c);

	int max = 0;

	if ( a > b ) {
		if ( a > c ){
			max = a;
		}else{
			mac = c;
		}
	} else {
		if ( b > c ){
			max = b;
		}else{
			max = c;
		}
	}

	printf("The max is %d\n", max);
	return 0;
}

/*if-else去掉大括号格式
int main() 
{
	int a, b, c;
	scanf("%d %d %d", &a, &b, &c);

	int max = 0;
    
    if ( a > b ) 
        if ( a > c )
            max = a;
        else
            mac = c;
    else 
        if ( b > c )
            max = b;
        else
            max = c;
    
    printf("The max is %d\n", max);
	return 0;
}*/
```

==没有加大括号时，else总是和最近的if匹配，不能只看缩进位置==

==建议if或else后总是使用{},即使只有一句话==

#### 级联的if-else if

**分段函数**

```c
int main()
{
	int f, x;
	scanf("%d", &x);

	if ( x < 0) {
		f = -1;
	}else if ( x == 0 ) { //省去了else后面的{}，并且将下一层级的else前移，使得所有else对称
		f = 0;
	}else {
		f = 2 * x;
	}
	printf("%d\n", f);	//单一出口

	return 0;
}
```

#### if-else的常见错误

- 忘了大括号

- if后面的()后加上了分号    `if  ( age > 60 );`  ❌  分号代表if语句已经结束了。

- 错误使用==和=，if只要求()里的值是零或非零

    ```c
    if ( a = b )	//只要b不是零，if条件就成立，就会有输出。副作用是将a的值改成b
    {
    	printf("A=B");
    }
    ```

#### 代码风格

==在if和else后面必须加上大括号形成语句块==

==大括号内的语句缩进一个tab的位置==

```c
//	代码风格1
if ( x < 0 ) {
	f = -1;
}else if ( x == 0 ) {
	f = 0;
}else {
	f = 2 * x;
}
```

```c
//	代码风格2
if ( x < 0 ) 
{
	f = -1;
}else if ( x == 0 ) 
{
	f = 0;
}else 
{
	f = 2 * x;
}
```

```c
//	代码风格3
if ( x < 0 ) 
{
	f = -1;
}
else if ( x == 0 ) 
{
	f = 0;
}
else 
{
	f = 2 * x;
}
```

#### 多路分支 switch-case

```c
int main()
{
	int type;
	scanf("%d", &type);

	switch ( type ) {	//()中为控制表达式，只能是整数型的结果
	case 1:				//case 后面的常量可以使常数，也可以是常数计算表达式
		printf("你好");
		break;
	case 2:
		printf("早上好");
		break;
	case 3:
		printf("晚上好");
		break;
	case 4:
		printf("再见");
		break;
	default:
		printf("啊，什么啊？");
		break;
	}
	return 0;
}
```

- switch语句可以看作是一种基于计算的跳转，计算控制表达式的值后，程序会跳转到相匹配的case（分支标号）处。分支标号只是说明switch内部位置的路标，只是一个入口，在执行完分支中的最后一条语句后，如果后面没有break，就会顺序执行到下面的case里去，直到遇到一个break，或者switch结束为止。

**成绩转换**

大于等于90分为A；

小于90且大于等于80为B；

小于80且大于等于70为C；

小于70且大于等于60为D；

小于60为E；

```c
int main()
{
	int grade;
	printf("请输入成绩（0-100）：");
	scanf("%d", &grade);
	grade /= 10;
	switch ( grade ) {
	case 10:
	case 9:
		printf("A\n");
		break;
	case 8:
		printf("B\n");
		break;
	case 7:
		printf("C\n");
		break;
	case 6:
		printf("D\n");
		break;
	default:
		printf("E\n");
		break;
	}
	return 0;
}
```

### 4.1 循环

#### while循环

- 当条件满足时进入循环，不断重复循环体内的语句。<u>*注意循环体体内要有改变条件的机会*</u>，否则会出现死循环。
- 循环执行前判断是否继续循环，所以*<u>有可能循环一次也没有被执行</u>*

==**验证**==

测试程序时，常使用边界数据，如有效范围两端的数据、特殊的倍数等，如个位数、10、0、负数等。

**计算数字的位数**

```c
//	计算数字的位数
int main()
{
	int x;
	int n = 0;

	scanf("%d", &x);

	n++;	//用来保证0能够被计数为1位数
	x /= 10;
	while ( x > 0) {
		n++;
		x /= 10;
	}

	printf("%d\n", n);
	return 0;
}
```

#### do-while 循环

在进入循环的时候不做检查，而是在执行完一轮循环体的代码之后，再来检查循环的条件是否满足，如果满足则继续下一轮，不满足则结束循环。

```
do
{
	<循环体语句>
}while(<循环条件>);
```

**计算数字位数-改**

```c
//	计算数字的位数-改
int main()
{
	int x;
	int n = 0;
	scanf("%d", &x);

	do
	{
        n++;
		x /= 10;
	} while ( x > 0 );

	printf("%d\n", n);
	return 0;
}
```

### 4.2 循环应用

#### 猜数游戏

1. 计算机随机想一个数，记在变量number里面；
2. 一个负责计次数的变量count初始化为0；
3. 让用户输入一个数字a；
4. count递增（加一）；
5. 判断a和number的大小关系，如果a大，就输出“大”；如果a小久输出"小"；
6. 如果a和number是不相等的（无论大还是小），程序转回到第3步；
7. 否则，程序输出“猜中”和次数，然后结束。

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    // 初始化
    srand(time(0));
    int number = rand() % 100 + 1;
    int count = 0;
    int a = 0;
    printf("我已经想好了一个1到100之间的数。\n");
    // 进入循环
    do
    {
        printf("请猜这个1到100之间的数：");
        scanf("%d", &a);
        count++;
        if ( a > number ){
            printf("你猜的数大了。");
        } else if ( a < number ) {
            printf("你猜的数小了。");
        }
    } while ( a != number );

    printf("太好了，你用了%d次就猜到了答案。\n", count);
    return 0;
}
```

#### 算平均数

让用户输入一系列的正整数，最后输入-1表示输入结束，然后计算出这些数字的平均数，输出数字的个数和平均数。

1. 初始化变量sum和count为0；
2. 读入number；
3. 如果number不是-1，则将number加入sum，并将count加1，回到第2步；
4. 如果number是-1，则计算和打印处sum/count（注意换算成浮点数来计算）。

```c
#include <stdio.h>
//	计算平均数
int main() 
{
    int number;
    int sum = 0;
    int count = 0;
    
    scanf("%d", &number);
    while ( number != -1 ) {
        sum += number;
        count++;
        scanf("%d", &number);
    }
    
    printf("平均数为%f。\n", 1.0 * sum / count );
    return 0;
}
```

#### 整数逆序

1. 对一个整数做%10的操作，就得到它的个位数；
2. 对一个整数做/10的操作，就去掉了它的个位数；
3. 再对2的结果做做%10的操作，就得到原来数的十位数；
4. 以此类推。

- **输入为700，输出为7**

```c
#include <stdio.h>

int main()
{
    int x = 0;  //接收用户输入的正整数
    int digit = 0;  //存储当前的个位
    int ret = 0;    //计算逆序后的数
    printf("请输入一个正整数：");
    scanf("%d", &x);
    
    while ( x > 0 ) {
        digit = x % 10;
        ret = ret * 10 + digit;
        x /= 10;
    }
    
    printf("逆序后的数为：%d\n", ret);
    return 0;
}
```

- **输入为700，输出为007**

```c
#include <stdio.h>

int main()
{
    int x = 0;  //接收用户输入的正整数
    int digit = 0;  //存储当前的个位
    printf("请输入一个正整数：");
    scanf("%d", &x);
    
    while ( x > 0 ) {
        digit = x % 10;
        printf("%d", digit);
        x /= 10;
    }
    
    printf("\n");
    return 0;
}
```

#### 编程练习解析

**例题一：求符合给定条件的整数集**

给定不超过6的正整数A，考虑从A开始的连续4个数字。请输出所有由他们组成的无重复的3位数。

**输入格式：**

输入在一行中给出A。

**输出格式：**

输出满足条件的3位数，要求从小到大，每行6个整数。整数间以空格分隔，但行末不能有多余的空格。

**输入样例：**

2

**输出样例：**

234 235 243 245 253 254
324 325 342 345 352 354
423 425 432 435 452 453
523 524 532 534 542 543

```c
#include <stdio.h>

int main() 
{
    int a;
    scanf("%d", &a);
    int i, j, k;
    int cnt = 0;
    
    i = a;
    while (i <= a + 3) {
        j = a;
        while (j <= a + 3) {
            k = a;
            while (k <= a + 3) {
                if (i != j) {
                    if (i != k) {
                        if (j != k) {
                            printf("%d%d%d", i, j, k);
                            cnt++;
                            if (cnt == 6) {
                                printf("\n");	// 输出回车
                                cnt = 0;
                            } else {
                                printf(" ");	// 输出空格
                            }
                        }
                    }
                }
                k++;
            }
            j++;
        }
        i++;
    }
    return 0;
}
```

**例题二：水仙花数**

水仙花数是指一个N位正整数（N>=3），它的每个位上的数字的N次幂之和等于它本身。例如：153 = 1^3^+5^3^+3^3^。本题要求编写程序计算所有N位水仙花数。

**输入格式：**

输入在一行中给出一个正整数N（ 3<=N<=7 ）。

**输出格式：**

按递增顺序输出所有N位水仙花数，每个数字占一行。

**输入样例：**

3

**输出样例：**

153

370

371

407

```c
#include <stdio.h>

int main() 
{
    int n;
    scanf("%d", &n);
//  计算遍历范围first-first*10
    int first = 1;
    int i = 1;
    while (i < n) {
        first *= 10;
        i++;
    }
    int j = first;  //  记录遍历开始的值
//  遍历
    while (j < first * 10 ) {
        int t = j;  //  用t来代替j去分解计算
        int sum = 0;
        do {
            int d = t % 10; //  取t的个位数
            t /= 10;    //  t去掉个位数
            //  计算当前位的n次方
            int p = 1;
            int k = 0;
            while (k < n) {
                p *= d;
                k++;
            }
            sum += p;	//	求和
        } while (t > 0);
        if (sum == j) {
            printf("%d\n", j);
        }
        j++;
    }
    return 0;
}
```

**例题三：九九乘法表**

任意给定1位正整数N，输出从1 * 1到N * N的部分口诀表。

**输入格式：**

输入在一行中给出一个正整数N（ 1<=N<=9 ）。

**输出格式：**

输出下三角乘法表，其中等号右边的数字占4位、左对齐。

**输入样例：**

9

**输出样例：**

1\*1=1  

1\*2=2	2\*2=4  

1\*3=3	2\*3=6    3\*3=9  

1\*4=4    2\*4=8    3\*4=12  4\*4=16  

1\*5=5    2\*5=10  3\*5=15  4\*5=20  5\*5=25  

1\*6=6    2\*6=12  3\*6=18  4\*6=24  5\*6=30  6\*6=36  

1\*7=7    2\*7=14  3\*7=21  4\*7=28  5\*7=35  6\*7=42  7\*7=49  

1\*8=8    2\*8=16  3\*8=24  4\*8=32  5\*8=40  6\*8=48  7\*8=56  8\*8=64  

1\*9=9    2\*9=18  3\*9=27  4\*9=36  5\*9=45  6\*9=54  7\*9=63  8\*9=72  9\*9=81  

```c
#include <stdio.h>

int main() 
{
    int n;
    scanf("%d", &n);
    int i, j;
    
    i = 1;
    while (i <= n) {
        j = 1;
        while (j <= i) {
            printf("%d*%d=%d", j, i, i * j);
            if (i * j < 10) {
                printf("   ");
            } else {
                printf("  ");
            }
            j++;
        }
        printf("\n");
        i++;
    }
    return 0;
}

```

**例题四：统计素数并求和**

统计给定整数M和N区间内素数的个数并对它们求和。

**输入格式：**

输入在一行中给出2个正整数N和M（ 1<=M<=N<=500 ）。

**输出格式：**

在一行中顺序输出M和N区间内素数的个数以及它们的和，数字间以空格分隔。

**输入样例：**



**输出样例：**

7

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    int m,n;
    scanf("%d %d", &m, &n);
    int cnt = 0;
    int sum = 0;
    //  1不是素数
    if (m == 1) {
        m = 2;
    }
    //  判断素数，用i从m遍历到n，检测区间内的数字是否是素数
    for (int i = m; i <= n; i++) {
        int isPrime = 1;	//	标志位
        for (int j = 2; j < i; j++) {
            if (i % j == 0) {
                isPrime = 0;
                break;
            }
        }
        //  判断i是否是素数
        if (isPrime) {
            cnt++;
            sum += i;
        }
    }
    printf("%d %d\n", cnt, sum);
    return 0;
}
```

### 5.1 for循环

for循环像一个计数循环：设定一个计数器，初始化它，然后在计数器到达某个值之前，重复执行循环体，而每执行一轮循环，计数器值以一定的步进进行调整，比如加1或者减1。

**for = 对于**

- for ( count=10; count>0; count-- )

- 就读成：对于一开始的count=10，当count>0时，重复做循环体，每一轮循环在做完循环体内语句后，使得count减1。

#### 计算阶乘n!（从1乘到n）

```c
#include <stdio.h>

int main() 
{
    int n;
    scanf("%d", &n);
    int fact = 1;
    //	计算阶乘
    int i = 1;
    for ( i=1; i<=n; i++) {//i=1是初始条件，i<=n是循环继续的条件，i++是循环每一轮要做到动作
        fact *= i;
    }
    printf("%d!=%d\n", n, fact);
    return 0;
}
```

==执行完一次循环后，i加1，比较当前i是否小于n，若小于或等于，则进入循环体==

**小套路**

- 做求和的程序时，记录结果的变量初始化为0；而做求积的变量时，记录结果的变量应该初始化为1。

- 若循环控制变量i只在循环里被使用，在循环外面它没有任何用处时，可以把变量i的定义写到for语句里面去。

    `for ( int i=1; i<=n; i++ )`	<u>***只有C99支持***</u>

#### 计算阶乘n!（从n乘到1）

```c
#include <stdio.h>

int main() 
{
    int n;
    scanf("%d", &n);
    int fact = 1;
    //	计算阶乘
    int i = n;	//记录n的初试值，用来输出所求是何数的阶乘
    for ( n=n; n>1; n--) {	//n=n可以省略，写成 for ( ; n>1; n--)
        fact *= n;
    }
    printf("%d!=%d\n", i, fact);
    return 0;
}
```

#### 循环的计算和选择

- `for ( i=0; i<n; i++ )`和`for ( i=1; i<=n; i++ )`的循环次数是一样的；不同的是，前者循环结束后i=n，后者i=n+1。
- for循环与while循环是等价的，任何一个for循环都可以改写成while循环
- for中的每一个表达式都是可以省略的，`for ( ; 条件;  )`==`while ( 条件 )`

#### Tips for loops

- 如果有固定的次数，用for
- 如果必须执行一次，用do-while
- 其他情况用while

### 5.2 循环控制

**素数**

```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
    int x = 0;
    printf("请输入一个正整数：");
    scanf("%d", &x);
    
    int i = 0;
    int isprime = 1;    //x是素数
    for ( i=2; i<x; i++) {
        if ( x % i == 0 ) {
            isprime = 0;
            break;
        }
    }
    if ( isprime == 1) {
        printf("是素数。\n");
    } else {
        printf("不是素数。\n");
    }
    return 0;
}
```

利用`break;`语句可以跳出for循环或while或do-while。

`continue；`语句用来跳过这一轮循环剩下的语句进入下一轮循环。

<img src="https://zmq20200506.oss-cn-shanghai.aliyuncs.com/images/20200506234629.png?Lingting_Gun" style="zoom:30%;" />

#### 循环嵌套

**输出100以内的素数**

```c
#include <stdio.h>

int main() 
{
    int x;
    for ( x = 1; x <= 100; x++) {
        int i;
        int isprime = 1; //x是素数
        for ( i = 2; i < x; i++ ) {	//正常情况下每层循环用的控制变量不能相同
            if ( x % i == 0) {
                isprime = 0;
                break;
            }
        }
        if ( isprime == 1 ) {
            printf("%d ", x);
        }
    }
    return 0;
}
```

**输出前50个素数**

- for循环

```c
#include <stdio.h>

int main(int argc, const char * argv[]) 
{
    int x = 1;
    int cnt = 0;    //记录输出素数的个数
    
    for ( x = 1; cnt < 50; x++) {	//循环条件可以使cnt
        int isprime = 1;
        for ( i = 2; i < x; i++) {
            if ( x % i == 0) {
                isprime = 0;
                break;
            }
        }
        if ( isprime == 1 ) {
            cnt++;
            printf("%d\t", x);	//自动对齐
            if ( cnt % 5 == 0 ) {
                printf("\n");	//每输出5个结果，换行
            }
        }
    }
    return 0;
}
```

- while循环

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    int x = 1;
    int cnt = 0;    //记录输出素数的个数

    while (cnt < 50) {
        int i;
        int isprime = 1;
        for (i = 2; i < x; i++) {
            if (x % i == 0) {
                isprime = 0;
                break;
            }
        }
        if (isprime == 1) {
            cnt++;
            printf("%d\t", x);
            if (cnt % 5 == 0) {
                printf("\n");
            }
        }
        x++;
    }
    return 0;
}
```

#### 离开多重循环

 **凑硬币--接力break**

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    int x;  //  存储输入值
    int one, two, five; //  1毛，2毛，5m毛的个数
    int exit = 0;   //  是否退出循环标志位
    printf("请输入需要组成的金额：");
    scanf("%d", &x);
    
    for (one = 1; one < x * 10; one++) {
        for (two = 1; two < x * 10 / 2; two++) {
            for (five = 1; five < x * 10 / 5; five++) {
                if (one + two * 2 + five * 5 == x * 10) {
                    printf("%d个1毛，%d个2毛，%d个5毛可以组成%d元。\n", 
                           one, two, five, x);
                    exit = 1;
                    break;
                }
            }
            if (exit) break;
        }
        if (exit) break;
    }
    return 0;
}
```

**凑硬币--goto**

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    int x;  //  存储输入值
    int one, two, five; //  1毛，2毛，5m毛的个数
    printf("请输入需要组成的金额：");
    scanf("%d", &x);

    for (one = 1; one < x * 10; one++) {
       for (two = 1; two < x * 10 / 2; two++) {
           for (five = 1; five < x * 10 / 5; five++) {
               if (one + two * 2 + five * 5 == x * 10) {
                   printf("%d个1毛，%d个2毛，%d个5毛可以组成%d元。\n", 
                          one, two, five, x);
                   goto out;    //  直接跳转到out处
               }
           }
       }
    }
out:
    return 0;
}
```

### 5.3高级循环应用

#### 分数求和

> $$
> f(n)= 1+\frac{1}{2}+\frac{1}{3}+...+\frac{1}{n}
> $$

```c
#include <stdio.h>

int main() 
{
    int n;	// 存储用户输入要求的n的值
    double sum = 0.0;	// 存储累加和
    printf("请输入n的值：");
    scanf("%d", &n);
    
    for (int i = 1; i <= n; i++) {
        sum += 1.0 / i;
    }
    
    printf("f(%d)=%f\n", n, sum);
    return 0;
}
```

$$
f(n)= 1-\frac{1}{2}+\frac{1}{3}-\frac{1}{4}+...+\frac{1}{n}
$$

```c
#include <stdio.h>

int main() 
{
    int n;
    double sum = 0.0;
    printf("请输入n的值：");
    scanf("%d", &n);
    
    double sign = 1.0;	// 用sign来实现正负间隔，同时设为浮点型，保证运算
    for (int i = 1; i <= n; i++) {
        sum += sign / i;
        sign = -sign;
    }
    printf("f(%d)=%f\n", n, sum);
    return 0;
}
```

#### 整数分解

**正序分解整数**

- 输入一个非负整数，正序输出它的每一位数字
- 输入：13425
- 输出：1 3 4 2 5 

```c
#include <stdio.h>

int main() 
{
    int x;
    printf("请输入需要拆分的非负整数：");
    scanf("%d", &x);
//  求出用来取最高位的除数mask
    int mask = 1;
    int t = x;
    while (t > 9) {     //  保证只有一位数时，mask为1
        mask *= 10;
        t /= 10;
    }
//  printf("t = %d，mask = %d\n", t, mask);  //  测试当前t和mask的值
//  顺序输出整数
    do {
        int d = x / mask;
        printf("%d", d);    //  输出当前最高位
        if (mask > 9) {     //  不是最后一位时，在输出位后输出一个空格
            printf(" ");
        }
        x %= mask;
        mask /= 10;
    } while (mask > 0);
    printf("\n");
    return 0;
}
```

#### 求最大公约数

**枚举法**

```c
#include <stdio.h>

int main() 
{
    int a, b;
    int min;
    scanf("%d %d", &a, &b);
//  找到两个数中较小的那个数
    if (a < b) {
        min = a;
    } else {
        min = b;
    }
//  枚举法求最大公约数
    int ret = 0;
    for (int i = 1; i < min; i++) {
        if (a % i == 0) {
            if (b % i == 0) {
                ret = i;
            }
        }
    }
    printf("%d和%d的最大公约数为%d。\n", a, b, ret);
    return 0;
}

```

**辗转相除法**

1. 如果b等于0，计算结束，a就是最大公约数；
2. 否则，计算a除以b的余数，让a等于b，而b等于那个余数；
3. 回到第一步；

```c
#include <stdio.h>

int main() 
{
    int a, b;
    int t;	//	存储a除以b的余数
    printf("请输入两个数：");
    scanf("%d %d", &a, &b);
//	辗转相除
    while (b != 0) {
        t = a % b;
        a = b;
        b = t;
    }
    printf("最大公约数为%d。\n", a);
    return 0;
}
```

#### 编程练习解析

**例题一：求序列前n项和**

计算序列2/1+3/2+5/3+8/5...的前n项和。注意该序列从第二项起，每一项的分子是前一项分子与分母的和，分母是前一项的分子。

**输入格式：**

输入在一行中给出一个正整数N。

**输出格式：**

在一行中输出部分和的值，精确到小数点后2位。题目保证计算结果不超过双精度范围。

**输入样例：**

20

**输出样例：**

32.66

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    int n;
    double dividend, divisor; // 定义分子和分母
    double sum = 0.0;
    int i;
    int t;
    
    scanf("%d", &n);
    dividend = 2;
    divisor = 1;
    for (i = 1; i <= n; i++) {
        sum += dividend / divisor;
        t = dividend;
        dividend = dividend + divisor;
        divisor = t;
    }
    printf("%f %f\n", dividend, divisor);
    printf("%.2f\n", sum);

    return 0;
}
```

### 6.1 数据类型

#### C语言是有类型的语言

- C语言的变量，必须：
    - 在使用前定义，并且确定类型
- C以后的语言向两个方向发展：
    - C++/Java更加强调类型，对类型的检查更严格
    - JavaScript、Python、PHP不看重类型，甚至不需要事先定义

**类型安全**

- 支持强类型的观点认为明确的类型有助于尽早发现程序中的简单错误
- 反对强类型的观点认为过于强调强类型迫使程序员面对底层，而非实现事务逻辑
- 总的来说，早期的语言强调类型，面向底层的语言强调类型
- C语言需要类型，但是对类型的安全检查并不足够

##### C语言的类型

- 整数
    - char、short、int、long、long long(C99)
- 浮点数
    - float、double、long double(C99)
- 逻辑
    - bool
- 指针
- 自定义类型

##### 类型有何不同

- 类型名称：int、long、double
- 输入输出时的格式化：%d、%ld、%lf
- 所表达的数的范围：char < short < int < float < double
- 内存中所占据的大小：1个字节(char)到16个字节(long double)
- 内存中的表达形式：整型为二进制数（或补码）、浮点型为编码

#### sizeof

- 是一个运算符，给出某个类型或变量在内存中所占据的字节数
    - `sizeof(int)`
    - `sizeof(i)`
- 是静态运算符，它的结果在编译时就决定了
- 不要再sizeof的括号里做运算，这些运算是不会做的

#### 整数

- char：1字节（8比特）
- short：2字节
- int：取决于编译器（CPU），通常的意义是“一个字”
- long：取决于编译器（CPU），通常的意义是“一个字”
- long long：8字节

*<u>计算机的位数或字长是指计算器CPU中的寄存器是多少bit，即每个寄存器最多可以表达多少个bit的数据；同时也是在说内存RAM和CPU之前传输的数据每次可以传输多少比特，即总线每次可以传输多少bit。通常有32bit和64bit，一般计算机中的int可能为32bit(4字节)或64bit(8字节)。</u>*

##### *整数的内部表达

- 计算机内部一切都是二进制
    - 18—>00010010
    - 0—>00010010

##### *二进制负数

- 1个字节可以表达的数：
    - 0000 0000 — 1111 1111（0-255）
- 三种方案
    - 仿照十进制，有一个特殊的标志表示负数【***需要判断特别的标志，导致设计复杂***】
    - 取中间的数为0，如1000 0000表示0，比它小的是负数，比它大的是正数【***每次都需要与10000000做减法，判断自己到底是多少***】
    - 补码

##### *补码

- 考虑-1，我们希望-1 + 1 —> 0。
    - 0—>0000 0000
    - 1—>0000 0001
    - 1111 1111 + 0000 0001 = 1 0000 0000
- 因为0 - 1 —> -1，所以，-1 =
    - (1)0000 0000 - 0000 0001 —> 1111 1111
    -  1111 1111被当作纯二进制看待时，是255，被当作补码看待时是-1
- 同理，对于-a，其补码就是0-a，实际是2^n^-a，n是这种类型的位数

==补码的意义就是拿补码和原码可以加出一个溢出的“零”==

**数的范围**

- 对于一个字节（8位），可以表达的是：
    - 0000 0000 - 1111 1111
- 其中
    - 0000 0000 —> 0
    - 1111 1111 ~ 1000 0000 —> -1 ~ -128
    - 0000 0001 ~ 0111 1111 —> 1 ~ 127

```c
#include <stdio.h>

int main() 
{
    char c = 255;
    int i = 255;
    printf("c=%d，i=%d\n", c, i);
    //  c其实是：11111111，对c来说它的最高位为1
    //  i其实是：00000000 00000000 00000000 11111111，对i来说最高位不是1
    return 0;
}
```

<img src="/Users/kungfu/Desktop/截屏2020-03-0815.23.20.png" alt="截屏2020-03-0815.23.20" style="zoom:60%;" />

##### 整数的范围

- char：1字节：-128 ~ 127
- short：2字节：-32678 ~ 32767
- int：取决于编译器（CPU），通常的意义是“一个字”
- long：4字节：-2^32-1^ ~   2^32-1^-1
- long long：8字节

##### unsigned

- 如果一个字面量常数想要表达自己是unsigned，可以在后面加u或U
    - 255U
- 用l或L表示long（long）
- *unsigned的初衷并非是为了扩展数能表达的范围，而是为了做纯二进制运算，主要是为了移位

##### 整数越界

- 整数是以纯二进制方式进行计算的，所以：
    - 1111 1111 + 1 —> 1 0000 0000 —> 0
    - 0111 1111 + 1 —> 1000 0000  —> -128
    - 1000 0000 - 1 —> 0111 1111 —> 127

##### 整数的输入输出

只有两种形式：int或long long

- %d：int和比int小的char或short输出时，都是%d
- %u：unsigned int、unsigned char、unsigned short

==当把小于int的变量传给printf时，编译器会把这个变量转换为int传进去==

- %ld：long和long long输出时，都是%ld
- %lu：unsigned long、unsigned long long

##### 8进制和16进制

- 一个以0开始的数字字面量是8进制
- 一个以0x开始的数字字面量是16进制
- %0用于输出8进制，%0x或%0X用于输出16进制

==8进制和16进制知识如何把数字表达为字符串，与内部如何表达数字无关，计算机内部都是表达为2进制==

##### 整数类型的选择

- 为什么整数要有那么多种？
    - 为了准确表达内存，做底层程序的需要
- 没有特殊需要，就选int
    - 现在的CPU的字长普遍是32位或64位，一次内存读写就是一个int，一次计算也是一个int，选择更短的类型不会更快，为了剥离多余位，有时甚至可能更慢
    - *现代的编译器一般会设计内存对齐，所以更短的类型实际在内存中可能也占据一个int的大小（虽然sizeof告诉你更小）
- unsigned与否只是输出的不同，内部计算是一样的

#### 浮点类型

|  类型  | 字长 |                            范围                            | 有效数字 |
| :----: | :--: | :--------------------------------------------------------: | :------: |
| float  |  32  |  ±(1.20×10^-38^~3.40×10^38^)，0，±inf(∞)，nan(非有效数字)  |    7     |
| double |  64  | ±(2.20×10^-308^~1.79×10^308^)，0，±inf(∞)，nan(非有效数字) |    15    |

- -10^-38^ ~ 0 ~ 10^-38^中间的数无法用float表达，不包括0
- -10^-308^ ~ 0 ~ 10^-308^中间的数无法用double表达，不包括0

|  类型  | scanf |            printf            |
| :----: | :---: | :--------------------------: |
| float  |  %f   | %f，%e或%E(输出为科学计数法) |
| double |  %lf  | %f，%e或%E(输出为科学计数法) |

在%和f之间加上.n可以致电过输出小数点后几位数字，但这样的输出是四舍五入的：`printf("%.16f\n", a)	//	在小数点后输出16位的数字`

```c
#include <stdio.h>

int main() 
{
    printf("%.3f\n", -0.0049);	//	输出为：-0.005
    printf("%.30f\n", -0.0049);	//	输出为：-0.004899999999999999841793218991
    printf("%.3f\n", -0.00049);	//	输出为：-0.000
    return 0;
}
```

 

```c
#include <stdio.h>

int main() 
{
    printf("%f\n", 12.0 / 0.0);	//	输出为：inf
    printf("%f\n", -12.0 / 0.0);	//	输出为：-inf
    printf("%f\n", 0.0 / 0.0);	//	输出为：nan
    return 0;
}
```

##### 浮点运算精度

```c
float a, b, c;

a = 1.345f;
b = 1.123f;
if (c == 2.468)
    printf("相等\n");
else
    printf("不相等！c=%.10f，或%f\n", c, c);	
	//	输出为：不相等！c=2.4679999352，或2.468000
```

- ==带小数点的字面量是默认是double而非float，float需要用f或F后缀来表明身份==
- ==f1 ==  f2可能失败，通常用fabs(f1 - f2) < 1e-8或fabs(f1 - f2) < 1e-12，即求两个浮点数的差的绝对值,看他是否小于float能表达的精度==

##### *浮点数的内部表达

<img src="https://zmq20200506.oss-cn-shanghai.aliyuncs.com/images/20200506234717.png?Lingting_Gun" alt="截屏2020-03-0818.00.54" style="zoom:85%;" />

在浮点数内部，不是一个真正的二进制数，而是一个编码的形式：

- 第1个bit用来表达正负
- 2~11个bit用来表达指数部分
- 后面的bit用来表达分数部分

==浮点数在计算时是由专用道硬件部件实现的。计算double和float所用的部件是一样的。==硬件接收到编码后先解码做运算，然后再编码返回给用户。

##### 浮点类型的选择

- 如果没有特殊需要，只使用double
- 现代CPU能直接对double做硬件计算，性能不会比float差，在64位的机器上，数据存储的速度也不比float慢。

#### 字符类型

- char是一种整数，也是一种特殊的类型：字符（character）。
    - printf和scanf里用%c来输入输出字符 

- 输入'1'这个字符给`char c`

```c
char c;
scanf("%c", %c);
```

​	此时输入1

```c
char c;
int i;
scanf("%d", &i);
c = i;
```

​	此时需输入49

```c
 printf("c='%c',c=%d\n", c, c);	//	输出均为：c='1',c=49
```

***因为'1'的ASCII码是49，所以当c == 49时，它代表'1'*** 

`scanf("%d %c", &i, &c);`和`scanf("%d%c", &i, &c);`的区别

输入：`12 1`

```c
int i;
char c;
scanf("%d %c", &i, &c);	//	%d后面有空格
printf("i=%d, c='%c', c=%d\n", i, c, c);	//	输出为：i=12, c='1', c=49
```

```c
int i;
char c;
scanf("%d %c", &i, &c);	//	%d后面有空格
printf("i=%d, c='%c', c=%d\n", i, c, c);	//	输出为：i=12, c=' ', c=32
```

- 若%d后面有空格，则整数要读到空格结束，包括空格，空格后的内容读给%c；若整数后面没有空格，则读接下来的内容默认为字符
- 若%d后面没有空格，则整数读完以后默认继续读下一个字符给%c，下一个字符可能为输入的空格

##### 字符计算

- 一个字符加一个数字得到ASCII码表中那个数之后的字符
- 两个字符的减，得到它们在表中的距离
- 'a'-'A'可以得到两段之间的距离，于是：
    - a + 'a'-'A' 可以把一个大写字母变成小写字母【大变小，小减大】
    - a + 'A'-'a' 可以把一个小写字母变成大写字母【小变大，大减小】

=='A'：65、'a'：97==

##### 逃逸字符

- 用来表达无法印出来的控制字符或特殊字符，它由一个反斜杠“\”开头，后面跟上另一个字符。这两个字符组合起来，组成了一个字符。

| 字符 |      意义      | 字符 |    意义    |
| :--: | :------------: | :--: | :--------: |
|  \b  |    回退一格    | \\"  |   双引号   |
|  \t  | 到下一个表格位 | \\'  |   单引号   |
|  \n  |      换行      | \\\  | 反斜杠本身 |
|  \r  |      回车      |      |            |

#### 类型转换

##### 自动类型转换

- 当运算符的两边出现不一致的类型时，会自动转换成较大的类型
- 
    - char —> short —> int —> long —> long long
    - int —> float —> double
- 对于printf，任何小于int的类型会被转换成int；float会被转换成double
- 但是scanf不会，要输入short，需要%hd；要输入int，需要%d；要输入long或long long，需要%ld；

##### 强制类型转换

- 要把一个量强制转换成另一个类型（通常是较小的类型），需要：
    - （类型）值
        - `(int)10.2`
        - `(short)32`
    - 注意这时候的安全性，小的变量不能总表达大的量
        - `(short)32768`会输出`-32768`，因为short最大为32767
        - `(char)32768`会输出`0`，因为char只有8个bit，而32768 = 10……0(15个0)，对char来说取了最低的8个bit，全都是0。
- ==强制类型转换只是从那个变量计算出了一个新的类型的值，它并不改变那个变量，无论是值还是类型都不改变==

- 强制类型转换优先级高于四则运算

### 6.2 其他运算

#### 逻辑类型

- `#include<stdbool.h>`之后就可以使用bool和true、false

##### 逻辑运算

- 逻辑运算是对逻辑量进行的运算，结果只有0或1
- 逻辑量是关系运算或逻辑运算的结果

| 运算符 |  描述  |   示例   |                            结果                            |
| :----: | :----: | :------: | :--------------------------------------------------------: |
|   ！   | 逻辑非 |    !a    |     如果a是true结果就是false，如果a是false结果就是true     |
|   &&   | 逻辑与 |  a && b  |       如果a和b都是true，结果就是true；否则就是false        |
|  \|\|  | 逻辑或 | a \|\| b | 如果a和b有一个true，结果为true；两个都是false，结果为false |

**优先级**

- ! > && > ||

- 逻辑运算是自左向右进行的，如果左边的结果已经能够决定结果了，就不会做右边的计算，这种事请叫做：短路
    - 对于&&，左边是false时就不做右边了
    - 对于||，左边是true时就不做右边了
    - 所以尽量不要把赋值运算表达式写在右边

#### 条件运算符

- `count = (count > 20) ? count - 10 : count + 10`

- `=`后面`?`前面是条件、`?`后面时条件满足时的值、`:`后面是条件不满足时的值

- 等价于

    - ```c
        if (count > 20) {
            count = count - 10;
        } else {
            count = count + 10;
        }
        ```

==一般不建议使用嵌套的条件表达式==

#### 逗号运算

- 逗号用来连接两个表达式，并以其右边的表达式的值作为它的结果。逗号的优先级是所有运算符中最低的，所以它两边的表达式会优先运算；逗号的组合关系是自左向右，所以左边的表达式会先计算，而右边的表达式的值就留下来作为逗号运算的结果。

    - `i = 3 + 4, 5 + 6;` 输出的i=7
    - `i = (3 + 4, 5 + 6);` 输出的i=11

- 逗号运算一般只在for循环中使用

    - ```c
        for (i = 0, j = 10; i < j; i++, j--)
        ```

### 7.1 函数的定义和调用

#### 初见函数

- ***代码复制***是程序质量不良的表现

**求和**

```c
void sum(int begin, int end) 
{
    int i;
    int sum;
    for (i = begin; i <= end; i++){
        sum += i;
    }
    printf("%d到%d的和是%d。\n", begin, end, sum);
}

int main()
{
    sum(1, 10);
    sum(20, 30);
    sum(35, 45);
    return 0;
}
```

#### 函数的定义和调用

##### 什么是函数

- 函数是一块代码，接收零个或多个参数，做一件事，并返回零个或一个值
-   可以先想象成数学中的函数

##### 函数定义

```c
函数头：返回类型 函数名（参数表）//	参数之间用','分开
{
	函数体
}
```

##### 调用函数

- ()起到了表示函数调用的重要作用
    - 即使没有参数也需要()

- 如果有参数，则需要给出正确的数量和顺序，这些值会被按照顺序依次用来初始化函数中的参数

- 函数知道每一次是哪里调用它，会返回到正确的地方

#### 从函数中返回值

- return停止函数的执行，并送回一个值
    - return后面可以不跟变量`return;`，也可以跟表达式`return 表达式`

- 可以复制给变量
- 可以再传递给函数
- 甚至可以丢掉

**没有返回值的函数**

`void 函数名(参数表)`

- 不能使用带值的`return`
    - 可以没有`return`
- 调用的时候不能做返回值的赋值
- ==如果函数有返回值，就必须使用带值的`return`==

### 7.2 函数的参数和变量

#### 函数原型

**函数先后关系**

- c的编译器自上而下顺序分析你的代码，所以main函数内需要调用的函数需要在上面先定义
- 即，需要先定义函数原型
    - 函数头，以分号';'结尾，就构成了函数的原型
- 函数原型的目的是告诉编译器这个函数长什么样子
    - 名称
    - 参数（数量及类型），可以不写参数的名字，但需要类型`void sum(int , int ); `
    - 返回类型

```c
#include<stdio.h>

void sum(int begin, int end); 	//函数原型，声明

int main()
{
    sum(1, 10);
    sum(20, 30);
    sum(35, 45);
    return 0;
}

void sum(int begin, int end) 	//	实际的函数头
{
    int i;
    int sum;
    for (i = begin; i <= end; i++){
        sum += i;
    }
    printf("%d到%d的和是%d。\n", begin, end, sum);
}
```

#### 参数传递

##### 函数调用

- 如果函数有参数，调用函数时必须传递给它数量、类型正确的值
- 可传递给函数的值是表达式的结果，这包括：
    - 字面量
    - 变量
    - 函数的返回值
    - 计算的结果

##### 类型不匹配

- 调用函数是给的值与参数的类型不匹配是C语言传统上最大的漏洞
- 编译器总是悄悄替你把类型转换好，但是这很可能不是你所期望的
- 后续的语言，C++/Java在这方面很严格

##### 调用函数时，传过去的是什么？

==C语言在调用函数时，永远只能传值给函数==

- 每个函数有自己的变量空间，参数也位于这个独立的空间中，和其他函数没有关系
- 函数参数表中的参数和调用函数时给的值就是***<u>参数和值</u>***的关系

#### 本地变量

- 函数的每次运行，就产生了一个独立的变量空间，在这个变量空间中的变量，是函数的这次运行所独有的，称作 *本地变量*  或 *局部变量*  或 *自动变量*
- 定义在函数内部的变量就是本地变量
- 参数也是本地变量

##### 变量的生存期和作用域

- 生存期：什么时候这个变量开始出现，到什么时候它消亡了
- 作用域：在（代码的）什么范围内可以访问这个变量（这个变量可以起作用）
- 对于本地变量，这两个问题的答案是统一的：大括号内——块

##### 本地变量的规则

- 本地变量是定义在块内的

    - 它可以是定义在函数的块内

        ```c
        swap(a, b)
        {
            int x = 0;
        }
        ```

    - 也可以是定义在语句的块内

        ```c
        if (a < b) {
            int i = 10;
        }
        ```

    - 甚至可以随便拉一个大括号来定义变量

- 程序运行进入这个块之前，其中的变量不存在，离开这个块，其中的变量就消失了

- 块外面定义的变量在里面仍然有效

    ```c
    int main()
    {
        int a = 5;
        int b = 6;
        {
            int i = 0;
            printf("%d\n", a);	//	会输出：5
        }
    }
    ```

- 块里面定义了和外面同名的变量则掩盖了外面的

    ```c
    int main()
    {
        int a = 5;
        int b = 6;
        {
            int a = 0;
            printf("a=%d\n", a);	//	会输出：a=0
        }
    }
    ```

- 不能在一个块内定义同名的变量

- 本地变量不会被默认初始化

- 参数在进入函数的时候被初始化了

#### 其他细节

##### 没有参数时

- 建议将声明写成`void f(void);`
- `void f();`在传统的C中，他表示f函数的参数表未知，并不表示没有参数

##### 逗号运算符

- 调用函数时，圆括号里面的逗号是标点符号，不是运算符：`f(a, b)`;
- 但如果是`f((a,b));`则需要算逗号运算再将计算结果传入函数

##### 函数里的函数？

- ==C语言不允许函数嵌套定义==

##### 关于main

- `int main()`也是一个函数，可以写成`int main(void)`
- `return 0;`是有用的，操作系统可以用来判断程序的运行结果
    - Windows：if errorlevel 1……
    - Unix Bash：echo $?
    - Csh：echo $status

### 8.1 数组

#### 初试数组

- 如何写出一个程序计算用户输入的数字的平均数，并输出所有大于平均数的数？

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    int x;
    double sum = 0;
    int cnt = 0;
    int number[100];    //  定义了一个数组number，里面每一个单元都是int型，数组大小为100
    scanf("%d", &x);
    while ( x != -1 ) {
        number[cnt] = x;	//	对数组中的元素赋值
        sum += x;
        cnt++;
        scanf("%d", &x);
    }
    if (cnt > 0) {
        printf("平均数为%f。\n", sum / cnt);
        int i;
        for (i = 0; i < cnt; i++) {	//	遍历数组
            if (number[i] > sum / cnt) {	//	使用数组中的元素
                printf("%d\n", number[i]);
            }
        }
    }
    return 0;
}
```

==上面的程序存在安全隐患，即数组大小可能会不够用==

改进程序

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    int x;
    double sum = 0;
    int cnt = 0;
    int n;
    scanf("%d", &n);
    if (n > 0) {
        int number[n]; //  定义了一个数组number，里面每一个单元都是int型，大小为n
       	scanf("%d", &x);
    	while ( x != -1 ) {
            number[cnt] = x;	//	对数组中的元素赋值
            sum += x;
            cnt++;
            scanf("%d", &x);
    	}
        if (cnt > 0) {
            printf("平均数为%f。\n", sum / cnt);
            int i;
            for (i = 0; i < cnt; i++) {	//	遍历数组
                if (number[i] > sum / cnt) {	//	使用数组中的元素
                    printf("%d\n", number[i]);
                }
            }
   	 	}
    }
    return 0;
}
```

#### 数组的使用

##### 定义数组

- `<类型> 变量名称[元素数量]；`
    - `int grades[10];`
    - `double weight[20];`
- 元素数量必须是整数
- C99之前，元素数量必须是编译时刻确定的字面量

##### 数组

- 是一种容器（放东西的东西），特点是：
    - 其中所有的元素具有相同的数据类型
    - 一旦创建，不能改变大小
    - ==*数组中的元素在内存中是联系依次排列的==

**int a[10]**

- 一个int的数组
- 10个单元：a[0]，a[1]，……，a[9]
- 每个单元就是一个int类型的变量
- 单元可以出现在赋值符号的左边或右边：
    - `a[2] = a[1] + 6;`
- *在赋值符号左边的叫做左值

##### 数组的单元

- 数组的每个单元就是数组类型的一个变量
- 使用数组时放在[]中的数字叫做下标或索引，下标从0开始计数

##### 有效的下标范围

- 编译器和运行环境都不会检查数组下表是否越界，无论是对数组单元做读还是写
- 一旦程序运行，越界的数组访问可能会造成问题，导致程序崩溃
    - segmentation  fault
    - Abort  trap
- 但是也可能运气好，没有造成严重后果
- 所以这是程序员的责任来保证程序只使用有效的下标值：[0, 数组的大小 - 1]

##### 长度为0的数组

- int a[0]，可以存在，但没有任何用处

#### 数组的例子

- 写一个程序，输入数量不确定的[0，9]范围内的整数，统计每一种数字出现的次数，输入-1表示结束 

```c
#include <stdio.h>

int main() 
{
    const int number = 10;  //  命名magic number 10：数组的大小
    int x;
    int count[number];  //  定义数组
    int i;
//  初始化数组
    for (i = 0; i < number; i++) {
        count[i] = 0;
    }
//  读取数字
    scanf("%d", &x);
    while (x != -1) {
        if (x >= 0 && x <= 9) {
            count[x]++; //  数组参与运算
        }
        scanf("%d", &x);
    }
//  遍历数组，输出每个数的个数
    for (i = 0; i < number; i++) {
        printf("%d：%d\n", i, count[i]);
    }
    return 0;
}
```

初始化count数组还可以这样

```c
 int count[number] = {0}; 
```

就可以将count中所有的单元初始化为0

### 8.2 数组运算

#### 数组的集成初始化

```c
int a[] = {2,4,6,7,1,3,5,9,11,13,23,14,32,};
```

- 直接用大括号给出数组的所有元素的初始值
- 不需要给出数组的大小，编译器会替你数数
- ==初始化数组时，最后一个数字后面加上一个','，方面后期加数字，加完数字，最好在后面再加上一个','，这是七八十年代的编程习惯==

```c
int a[10] = {2}; 
```

- 给定数组大小，但只给了数组的第一个单元的值时，后面没有给定是单元会被赋0，此时数组为`{2,0,0,0,0,0,0,0,0,0}`

##### 集成初始化时的定位（only c99）

```c
int a[10] = {[1] = 2, 3, [5] = 7}
```

此时数组为`{0,2,3,0,0,7,0,0,0,0}`

- 用[n]在初始化数据中给出定位

- 没有定位的数据接在前面的位置后面

- 其他位置的值补零

- 也可以不给出数组的大小，让编译器算

    ```c
    int a[] = {[1] = 2, 3, [5] = 7}
    ```

    此时数组为`{0,2,3,0,0,7}`，一共6个单元。定位的最大值就是数组的最大下标

- 特别适合初始数据稀疏的数组

##### 数组的大小

- sizeof给出整个数组所占据的内容的大小，单位是字节

- sizeof(a[0])给出数组中单个元素的大小，于是相除就得到了数组的单元个数

    ```c
    sizeof(a) / sizeof(a[0])
    ```

- 这样的代码，一旦修改数组中初始的数据，不需要修改遍历的代码

##### 数组的赋值

不可以直接把一个数组赋值给另一个数组

- 数组变量本身不能被赋值

- 要把一个数组的所有元素交给另一个数组，必须采用遍历

    ```c
    for (i = 0; i < length; i++){
        b[i] = a[i];
    }
    ```

##### 遍历数组

- 通常都是使用for循环，让循环变量从0到<数组的长度，这样***<u>循环体内</u>***最大的i正好是数组最大的有效长度 

- 常见错误：
    - 循环结束条件是`<=`数组长度，
    - 离开循环后，继续用i的值来做数组元素的下标。*离开循环后的i是数组的长度length，并不是数组最大有效下标，比最大有效下标多1，是无效的下标。*

**在数组中查找数字**

```c
#include <stdio.h>

/*
找出key在数组a中的位置
@param key 要寻找的数字
@param a 要寻找的数组
@param length 数组a的长度
@return 如果找到，返回其在a中的位置；如果找不到则返回-1
*/

int search(int key, int a[], int length);

int main() 
{
    int a[] = {2,4,6,7,1,3,5,9,11,13,23,14,32,};
    int x;
    int loc;
    printf("请输入一个数字：");
    scanf("%d", &x);
    loc = search(x, a, sizeof(a) / sizeof(a[0]));
    if (loc != -1) {
        printf("%d在下标为%d个位置上。\n", x, loc);
    } else {
        printf("%d不在数组中。\n", x);
    }
    return 0;
}

int search(int key, int a[], int length) {
    int ret = -1;
    int i;
    for (i = 0; i < length; i++) {
        if (a[i] == key) {
            ret = i;
            break;
        }
    }
    return ret;
}
```

- 数组作为函数的参数时：
    - 不能在[]中给出数组的大小
    - 不能再利用sizeof来计算素组的元素个数！必须再用另一个参数来传入，如上面的length

#### 数组例子-素数

##### 方法一：整除比较建立素数表

```c
#include <stdio.h>

/*
以数组下标代表数字，相应下标对应的值为1表示该下标的数是素数，为0表示该下标的数不是素数
@param x 要确定是否为素数的数字
@param knownPrime 素数表所在数组
@param lengthOfknownPrimes 素数表所在数组的长度
@return 若x可以被整除，则x不是素数，ret返回0；否则x为素数，ret返回1
*/

int isPrime(int x, int knownPrimes[], int lengthOfknownPrimes);

int main(int argc, const char * argv[]) {
    const int number = 10;
    int prime[number] = {2};
    int count = 1;  //  prime里面已经有一个2了
    int i = 3;  // 2是素数，从3开始判断
    
    //  调试代码：输出一个表头，即表的下标
    {
        printf("\t\t\t\t");
        for (int i = 0; i < number; i++) {
            printf("%d\t", i);
        }
        printf("\n");
    }
    //
    while (count < number) {
        if (isPrime(i, prime, count)) {
            prime[count++] = i; //  等价于先将i的值赋给prime[count]，再将count自加1
        }
        //  调试代码：输出当前的i，count，以及表中各单元的值
        {
            printf("i=%d \tcnt=%d\t", i, count);
            for (int i = 0; i < number; i++) {
                printf("%d\t", prime[i]);
            }
            printf("\n");
        }
        //
        i++;
    }
    for (i = 0; i < number; i++) {
        printf("%d", prime[i]);
        //  5个数字换一行，每个数字自动对齐
        if ((i + 1) % 5) {  //  等价于(i + 1) % 5 != 0，即只要不能整除，条件就为真
            printf("\t");
        } else {
            printf("\n");
        }
    }
    return 0;
}

int isPrime(int x, int knownPrimes[], int lengthOfknownPrimes) {
    int ret = 1;
    int i;
//  遍历已知的素数表，若x可以被整除，则x不是素数；否则x为素数
    for (i = 0; i < lengthOfknownPrimes; i++) {
        if (x % knownPrimes[i] == 0) {
            ret = 0;
            break;
        }
    }
    return ret;
}
```

输出结果为：

```c
			0	1	2	3	4	5	6	7	8	9	

i=3 	cnt=2	2	3	0	0	0	0	0	0	0	0	
i=4 	cnt=2	2	3	0	0	0	0	0	0	0	0	
i=5 	cnt=3	2	3	5	0	0	0	0	0	0	0	
i=6 	cnt=3	2	3	5	0	0	0	0	0	0	0	
i=7 	cnt=4	2	3	5	7	0	0	0	0	0	0	
i=8 	cnt=4	2	3	5	7	0	0	0	0	0	0	
i=9 	cnt=4	2	3	5	7	0	0	0	0	0	0	
i=10 	cnt=4	2	3	5	7	0	0	0	0	0	0	
i=11 	cnt=5	2	3	5	7	11	0	0	0	0	0	
i=12 	cnt=5	2	3	5	7	11	0	0	0	0	0	
i=13 	cnt=6	2	3	5	7	11	13	0	0	0	0	
i=14 	cnt=6	2	3	5	7	11	13	0	0	0	0	
i=15 	cnt=6	2	3	5	7	11	13	0	0	0	0	
i=16 	cnt=6	2	3	5	7	11	13	0	0	0	0	
i=17 	cnt=7	2	3	5	7	11	13	17	0	0	0	
i=18 	cnt=7	2	3	5	7	11	13	17	0	0	0	
i=19 	cnt=8	2	3	5	7	11	13	17	19	0	0	
i=20 	cnt=8	2	3	5	7	11	13	17	19	0	0	
i=21 	cnt=8	2	3	5	7	11	13	17	19	0	0	
i=22 	cnt=8	2	3	5	7	11	13	17	19	0	0	
i=23 	cnt=9	2	3	5	7	11	13	17	19	23	0	
i=24 	cnt=9	2	3	5	7	11	13	17	19	23	0	
i=25 	cnt=9	2	3	5	7	11	13	17	19	23	0	
i=26 	cnt=9	2	3	5	7	11	13	17	19	23	0	
i=27 	cnt=9	2	3	5	7	11	13	17	19	23	0	
i=28 	cnt=9	2	3	5	7	11	13	17	19	23	0	
i=29 	cnt=10	2	3	5	7	11	13	17	19	23	29	

2	3	5	7	11
13	17	19	23	29

Program ended with exit code: 0
```

##### 方法二：倍数删除法构造素数表

- 算法：欲构造n以内的素数表
    1. 令x为2
    2. 将2x，3x，4x直至ax<n的数标记为非素数
    3. 令x为下一个没有被标记为非素数的数，重复2；直至所有的数字都已经尝试完毕

- 伪代码：欲构造n以内的素数表
    1. 开辟`prime[n]`，初试化其所有元素为1，`prime[x]`为1表示x是素数
    2. 令`x = 2`
    3. 如果x是素数，则对于`(i = 2; x * i < n; i++)`令`prime[i * x] = 0`
    4. 令`x++`，如果`x < n`，重复3，否则结束

```c
#include <stdio.h>

int main(int argc, const char * argv[]) {
    const int maxNumber = 21;
    int isPrime[maxNumber];
    int i;
    int x;
    //  都初始化为1
    for (i = 0; i < maxNumber; i++) {
        isPrime[i] = 1;
    }
    //  for test
    {
        printf("\t");
        for (i = 2; i < maxNumber; i++) {
            printf("%d\t", i);
        }
        printf("\n");
    }
    //  for test
    for (x = 2; x < maxNumber; x++) {
        if (isPrime[x]) {
            for (i = 2; i * x < maxNumber; i++) {
                isPrime[i * x] = 0;
            }
        }
        //  for test
        {
            printf("%d\t", x);
            for (i = 2; i < maxNumber; i++) {
                printf("%d\t", isPrime[i]);
            }
            printf("\n");
        }
        //  for test
    }
    for (i = 2; i < maxNumber; i++) {
        if (isPrime[i]) {
            printf("%d\t", i);
        }
    }
    printf("\n");
    return 0;
}
```

输出为：

```c
	2	3	4	5	6	7	8	9	10	11	12	13	14	15	16	17	18	19	20
2	1	1	0	1	0	1	0	1	0	1	0	1	0	1	0	1	0	1	0	
3	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
4	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
5	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
6	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
7	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
8	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
9	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
10	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
11	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
12	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
13	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
14	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
15	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
16	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
17	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
18	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
19	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0	
20	1	1	0	1	0	1	0	0	0	1	0	1	0	0	0	1	0	1	0
        
2	3	5	7	11	13	17	19	
        
Program ended with exit code: 0
```

#### 二维数组

- `int a[3][5];`
- 通常理解为a是一个3行5列的矩阵

##### 二维数组的遍历

```c
for (i = 0; i < 3; i++){
    for (j = 0; j < 5; j++){
         a[i][j] = i * j;
    }
}
```

- `a[i][j]`是一个int，表示第i行第j列上的单元，从0开始计数
- `a[i,j]`不是正确的表达二维数组的方式，它实际上是`a[j]`

##### 二维数组的初始化

```c
int a[][5] = {
    {0,1,2,3,4},	//	{}可以省略
    {2,3,4,5,6}.
}
```

- 初始化时列数必须给出的，行数可以由编译器来数
- 每行一个{}，逗号分隔
- 最后的逗号可以存在，有古老的传统
- 如果省略，表示补零
- 也可以用定位（*C99 ONLY）

##### tic-tac-toe游戏

- 读入一个3×3的矩阵，矩阵中的数字为1表示该位置上有一个X，为0表示为O
- 程序判断这个举证中是否有获胜的一方，输出表示获胜一方的字符X或O，或输出无人获胜

```c
const int size = 3;
int board[size][size];
int i, j;
int numofX;
int numofO;
int result = -1;	//	-1：没人赢，1：X赢，0：O赢

//	读入矩阵
for (i = 0; i < size; i++){
	for (j = 0; j < size; j++){
		scanf("%d", &board[i][j]);
	}
}
```

```c
//	检查行，假设棋盘已摆满
for (i = 0; i < size && result == -1; i++)
{
	numofO = numofX = 0;
	for (j = 0; j < size; j++){
		if (board[i][j] == 1)
		{	
			numofX++;
		} else {
			numofO++;
		}
	}
	if (numofO == size){
		result = 0;
	} else if {
		result = 1;
	}
}
```

```c
//	检查列，假设棋盘已摆满
if (result == -1) {
	for (j = 0; j < size && result == -1; j++) {
		numofO = numofX = 0;
		for (i = 0; i < size; i++){
			if (board[i][j] == 1)
			{	
				numofX++;
			} else {
				numofO++;
			}
		}
		if (numofO == size){
			result = 0;
		} else if {
			result = 1;
		}
	}
}
```

```c
//	检查正对角线
numofO = numofX = 0;
for (i = 0; i < size; i++) {
	if (board[i][j] == 1) {
		numofX++;
	} else {
		numofO++;
	}
}
if (numofO == size) {
	result = 0;
} else {
	result = 1;
}
```

```c 
//	检查负对角线
numofO = numofX = 0;
for (i = 0; i < size; i++) {
	if (board[i][size - i - 1] == 1) {
		numofX++;
	} else {
		numofO++;
	}
}
if (numofO == size) {
	result = 0;
} else {
	result = 1;
}

```

### 9.1 指针

#### 取地址运算

##### 运算符&

- 获取变量的地址，它的操作数必须是变量
    - `int i; printf("%x", &i);`
- 地址的大小是否与int相同取决于编译器，地址与整数并不一定相同，与系统架构有关
    - `int i; printf("%p", &i);` ==取地址用`%p`==
- &不能对没有地址的东西取地址，只能对变量取地址。`&(a+b)`、`&(i++)`、`&(++i)`都是错误的
- 相邻变量取地址

```c
#include <stdio.h>

int main()
{
    int i;
    int p;
    printf("i的地址为：%p\n", &i);
    printf("p的地址为：%p\n", &p);
    
    return 0;
}
```

输出为：

```c
i的地址为：0x7ffeed5e4948
p的地址为：0x7ffeed5e4944
```

==先定义的变量地址大，后定义的变量地址小；因为它们是自上而下存储在内存stack中==

- 数组的地址、数组单元的地址、相邻的数组单元的地址

```c
#include <stdio.h>

int main()
{
    int a[10];

    printf("%p\n", &a);
    printf("%p\n", a);
    printf("%p\n", &a[0]);
    printf("%p\n", &a[1]);
    
    return 0;
}
```

输出为：

```c
0x7ffee37b6920
0x7ffee37b6920
0x7ffee37b6920
0x7ffee37b6924
```

==数组中地址自小到大存储，相邻的地址之间间隔是4==

#### 指针                                                                                                                                                                                     

- 指针就是保存地址的变量

- ```c
    int i;
    int *p = &i;	//去i的地址交给指针p
    ```
    - `*p`表示`p`是一个指针，它指向`int`型的变量

    - `*`的位置可以靠近`int`也可以远离`int`，所以:

        ```c
        int* p, q;
        ```

        ```c
        int *p, q;
        ```

        这两种写法的意思是一样的，都只是定义了`p`是指针，`q`只是一个普通的`int`型变量；要想定义`q`也是指针，需要写成

        ```c
        int *p, *q;
        ```

    - 普通变量的值是实际的值

    - 指针变量的值是具有实际值的变量的地址

##### 作为参数的指针

```c
void f(int *p);	//	f函数要一个int型的指针
```

调用f函数时要交给他一个地址：

```c
int i = 0;
f(&i);	//	取i的地址传进f函数
```

这时f函数里面就拥有访问外面的`i`的能力

```c
#include <stdio.h>
// 测试*和&
void f(int *p);
void g(int k);

int main(void) {
    int i = 6;
    printf("&i=%p\n", &i);	//	i的地址
    f(&i);	//	取i的地址传给f函数
    g(i);	//	取i的值传给f函数
    printf(" i=%d\n", i);
    return 0;
}

void f(int *p) {
    printf(" p=%p\n", p);	//	输出指针p所指的地址
    printf("*p=%d\n", *p);	//	*p用来访问指针p所指的地址的变量，即i
    *p = *p + 1;	//	*p==i，故表示将(i+1)的值赋给i
}

void g(int k) {
    printf(" k=%d\n", k);	//	输出当前i的值

```

输出为：

```c
&i=0x7ffeec8cd958
 p=0x7ffeec8cd958
*p=6
 k=7
 i=7
```

##### 访问那个地址上的变量*

- `*`是一个单目运算符，用来访问指针的值所表示的地址上的变量
- `*p`可以是左值也可以是右值，它表示一个变量
    - 左值：`*p = k + 1;	//	将k+赋给p所指的变量`
    - 右值：`int k = *p;  //  将p所指变量的值赋给变量k`

**左值之所以叫左值**

- 是因为出现在赋值号左边的不是变量，而是值，是表达式计算的结果，如：

    - ```c
        a[0] = 2;	//	数组的[]也是运算符，表示取下标对应的单元
        ```

    - ```c
        *p = 3;
        ```

- 是特殊的值，所以叫左值

==`&`和`*`是相互反作用的关系==

#### 指针的使用

##### 指针应用场景一

**交换两个变量的值：swap**

```c
#include <stdio.h>

void swap(int *pa, int *pb);

int main(void) {
    int a = 5;
    int b = 6;
    swap(&a, &b);	//	传入a，b的地址
    
    printf("a=%d, b=%d\n", a, b);
    return 0;
}

void swap(int *pa, int *pb) {
    int t = *pa;
    *pa = *pb;
    *pb = t;
}
```

##### 指针应用场景二(a)

- 当函数==返回多个值==，某些值就只能通过指针返回
- 传入的参数实际上是需要保存带回的结果的变量

**找出数组中最大值和最小值**

```c
#include <stdio.h>

void minmax(int a[], int length, int *min, int *max);

int main(int argc, const char * argv[]) {
    int a[] = {1,2,3,4,5,6,7,8,9,12,13,14,16,17,21,23,55};
    int min, max;	//	定义两个用来存储最大值最小值的变量
    minmax(a, sizeof(a) / sizeof(a[0]), &min, &max);
    printf("min=%d, max=%d\n", min, max);
    return 0;
}

void minmax(int a[], int length, int *min, int *max) {
    *min = *max = a[0];	//	将两个指针所指变量的值初始化为a[0]的值
    for (int i = 0; i < length; i++) {
        if (a[i] > *max) {
            *max = a[i];	//	将a[i]的值赋给max指针所指变量
        }
        if (a[i] < *min) {
            *min = a[i];	//	将a[i]的值赋给min指针所指变量
        }
    }
}
```

##### 指针应用场景二(b)

- 函数返回运算的状态，结果通过指针返回
- 通常的套路是让函数返回特殊的不属于有效范围内的值来表示出错：
    - -1或0（在文件操作会看到大量的例子）
- 但是当任何数值都是有效的可能结果时，就得分开返回了，即函数返回运算状态，结果通过指针返回
    - 后续的语言（C++，Java）采用了异常机制来解决这个问题

**两个数做除法**

```C
#include <stdio.h>

int divide(int a, int b, int *result);

int main(void) {
    int a = 5;
    int b = 0;
    int c;
    if (divide(a, b, &c)) {
        //  如果divide返回1，则输出结果c，否则没有输出
        printf("%d/%d=%d\n", a, b, c);
    }
    return 0;
}

int divide(int a, int b, int *result) {
    int ret = 1;
    if (b == 0) {
        ret = 0;
    } else {
        *result = a / b;
    }
    return ret;
}
```

##### 指针最常见错误

- 定义了指针变量，还没有指向任何变量，就开始使用指针
    - `int *p = 0;`❌

#### 指针与数组

- 函数参数里面的数组，其实就是指针
    - sizeof(a) == sizeof(int *)，大小就是一个int指针的大小
    - 并且可以用数组的运算符[]进行运算

- 以下四种函数原型是等价的：

    - ```c
        int sum(int *ar, int n);
        ```

    - ```c
        int sum(int *, int);
        ```

    - ```c
        int sum(int ar[], int n);
        ```

    - ```c
        int sum(int [], int);
        ```

##### 数组变量是特殊的指针

- 数组本身就表达地址，所以：

    - 无需用`&`取地址

        - ```c
            int a[10];
            int *p = a;
            ```

    - 但是数组的单元表达的是变量，需要用`&`取地址

        - ```c
            int &p = &a[1];
            ```

        - 注意a的地址就等于a[0]的地址：`a == &a[0]`

- `[]`运算符可以对数组做取值，也可以对指针做

    - `p[0]` 等价于 `*p`，都表示p指针当前所指的变量

- `*`运算符可以对指针做取值，也可以对数组做

    - `*a` 等价于`a[0]` ，但只能访问数组的第一个单元
    - 可以做左值被赋值：`*a = 25;`等价于`a[0] = 25;`

- 数组变量实际上是const的指针，所以不能被赋值，即不能直接让`b[] = a[];`

    - `int b[]; `实际上是 `int *const b;` 所以b数组一旦被创建出来就不能区代表别的数组了

##### 指针与const

- **指针是const**，表示一旦得到某个变量的地址，就一直是指向这个变量，不能再指向其他变量

    - ```c
        int *const q = &i;	// 	q是const
        *q = 26; //	OK
        q++;	// Error
        ```

- 指针所指的是const，表示不能通过指针去修改那个变量（并不能使得那个变量成为const）

    - ```c
        const int *p = &i;
        *p = 26; // Error，(*p)是const，所以p不能修改所指变量的值
        i = 26; // OK，i可以被修改
        p = &j; // OK，p也可以指向别的变量
        ```

- 判断哪个被const了的标志是const在*的前面还是后面

    - const在前面表示不能通过指针去修改那个变量

        ```c
        const int *p = &i;
        ```

        ```c
        int const *p = &i;
        ```

    - const在前面表示指针不能指向别的变量

        ```c
        int *const p = &i;
        ```

- 总是可以把一个非const的值转换成const的

    ```c
    void f(const int *x);//	定义一个不可修改所指变量的指针作为f的输入
    int a = 15;
    f(&a);	//	f不能修改a的值
    
    //	或者直接定义一个不可被修改的变量传入f
    const int b = a;
    f(&b);
    b = a + 1; // Error
    ```

    - 当要传递的参数的类型比地址大的时候，这是常用的手段；既能用比较少的字节数传递值给参数，又能避免函数对外面的变量的修改

##### const数组

```c
const int a[] = {1,2,3,4,5,6};
```

- 数组变量已经是const指针了，这里的const表明数组的每个单元都是const int
- 这类数组必须通过初始化进行赋值，应为一旦定义好，就无法修改了

##### 保护数组值

- 因为把数组传入函数时传递的是地址，所以那个函数内部可以修改数组的值

- 为了保护数组不被函数破坏，可以设置参数为const

    - ```c
        int sum(const int a[], int length);
        ```

### 9.2 指针运算

##### 数组指针运算

```c
#include <stdio.h>

int main(void)
{
    char ac[] = {0,1,2,3,4,5,6,7,8,9};
    char * p = ac;	// 指针p指向char型数组ac的第一个单元ac[0]，等价于char *p = &ac[0]
    char * p1 = &ac[5];
    printf("p  =%p\n", p);
    printf("p+1=%p\n", p + 1);
    //  *p 等价于 ac[0]
    //  *(p+1) 等价于 ac[1]
    //  所以 *(p+1) 等价于 ac[1]
    printf("*(p+1)=%d\n", *(p + 1));	// 输出为：ac[1]
    printf("p1-p=%ld\n", p1 - p);
    printf("\n" );

    int ai[] = {0,1,2,3,4,5,6,7,8,9};
    int * q = ai;	// 指针q指向int型数组ai的第一个单元ai[0]
    int * q1 = &ai[6];
    printf("q  =%p\n", q);
    printf("q+1=%p\n", q + 1);
    printf("*(q+1)=%d\n", *(q + 1));
    printf("q1 =%p\n", q1);
    printf("q1-q=%ld\n", q1 - q);	// 两个指针相减得到的是:(地址的差/sizeof(类型))
                                    // 即在这两个地址中间，能放几个这种类型的东西
    return 0;
}

```

输出为：

```c
p  =0x7ffee9ea593e
p+1=0x7ffee9ea593f
*(p+1)=1
p1-p=5

q  =0x7ffee9ea5910
q+1=0x7ffee9ea5914
*(q+1)=1
q1 =0x7ffee9ea5928
q1-q=6
```

- 指针`p`指向数组`a`后，指向的是数组第一个单元`a[0]`所在的起止地址；`p + 1`的值是`p`的值加上一个数组类型`sizeof(类型)`的大小，

    - ```c
        int a[10];
        int *p = a;
        *(p + 1)——>a[1]
        ```

    - char型的`p + 1`和`p`相差1，int型的`q + 1`和`q`相差4

    - 给一个指针加1表示要让指针指向下一个变量

    - 如果指针不是指向一片连续分配的空间，如数组，则这种运算没有意义

- 指针可以做以下算数运算
    - 给指针加、减一个整数（+，+=，-，-=）
    - 递增递减（++，--）
    - 两个指针相减
        - 两个指针相减得到的是:(地址的差/sizeof(类型))，即在这两个地址中间，能放几个这种类型的东西

##### *p++

- 取出p所指的那个数据来，完事以后顺便把p移到下一个位置去
- *的优先等级虽然高，但是没有++高
- 常用于数组类的连续空间操作
- 在某些CPU上，可以被直接翻译成一条汇编指令，加快运算速度

**遍历输出数组**

数组以-1结尾，做结束标志位

```c
for (p = ac; *p != 1; p++) {
    printf("%d\n", *p);
}
// 或者
for (p = ac; *p != 1; p) {
    printf("%d\n", *p++);
}
// 或者
while (*p != -1) {
    printf("%d\n", *p++);	//	输出当前*p的值，并将p加1
}
```

##### 指针比较

- <，<=，==，>，>=，!= 都可以对指针做
- 比较它们在内存中的地址
- 数组中单元的地址肯定是线性递增的

##### 0地址

- 内存中有0地址，但是0地址通常是个不能随便碰的地址，所以指针不应该具有0值
- 0地址是用来表示特殊的事情
    - 返回的指针无效的
    - 指针没有被真正初始化（先初始化为0）
- NULL是一个预定义的符号，表示0地址
    - 有的编译器对用0来表示0地址不友好，建议尽量用NULL来表示0地址

##### 指针的类型

- 无论指向什么类型，所有的指针的大小都是一样的，因为都是地址
- 但是指向不同类型的指针是不能直接互相赋值的
- 这是为了避免错用指针

##### 指针类型的转换

- `void *`表示不知道指向什么东西的指针
    - 计算时大小视为char*，但两种类型不想通
- 指针也可以转换类型
    - `int *p = &i; void *q = (void *)p;`
- 但这并没有改变p所指的变量的类型，而是让后人用不同的眼光通过p看它所指的变量
    - 即不当它是int型变量了，当它是个void型变量

##### 指针可以用来做什么？

- 需要传入较大的数据时用作参数
- 传入数组后对数组做操作
- 函数返回不止一个结果
    - 需要用函数来修改不止一个变量
- 动态申请内存

#### 动态内存分配

##### malloc()函数

- C99可以用变量做数组定义的大小，C99之前只能用malloc函数

    - ```c
        int *a = (int *)malloc(n * sizeof(int));
        ```

    - 要用malloc需要`#include <stdlib.h>`

    - 向malloc申请的空间的大小是以字节为单位的

    - malloc返回的结果是void *，需要将类型转换为自己需要的类型

        - ```c
            (int *)malloc(n * sizeof(int));
            ```

        - ```c
            (short *)malloc(n * sizeof(short));
            ```

        - ```c
            (double *)malloc(n * sizeof(double));
            ```

**动态申请数组大小**

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) 
{
	// 测试malloc分配数组大小
	int number;
	int *a;
	int i;
	printf("请输入数量：");
	scanf("%d", &number);
	a = (int *)malloc(number * sizeof(int));// malloc申请到的空间是以字节为单位的，所											 //	以要根据类型和个数申请空间
	  										// malloc返回的类型时(void *)，而a是												// (int *)，所以要强制类型转换	
	//	拿a当数组用，读入数据
	for (i = 0; i < number; i++) {
		scanf("%d", &a[i]);
	}
	//	逆序输出每个单元的数据
	for (i = number - 1; i >= 0; i--) {
		printf("%d ", a[i]);
	}
	free(a);	//	释放申请的空间

	return 0;
}
```

##### 没有空间

- 如果申请失败则返回0，或者返回NULL

**测试分配空间**

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    void *p;
    int cnt = 0;
    while ((p = malloc(100 * 1024 * 1024 ))) {
        cnt++;
    }
    printf("分配了%d00MB的空间\n", cnt);
    return 0;
}
```

##### free()

- 用来把申请来的空间还给“系统”
- 申请过来的空间，最终都是要还的，而且***<u>只能还申请来的空间的首地址</u>***
- 写指针程序，一般定义一个指针是就先赋值为0

##### 常见问题

- 申请了没free，会导致长时间运行内存逐渐下降

### 10.1 字符串

字符数组：`char word[] = {'H', 'e', 'l', 'l', 'o', '!'};`

字符串：`char word[] = {'H', 'e', 'l', 'l', 'o', '!', '\0'};`

- 对c语言来说，字符串指的是以0（整数0）结尾的一串字符
    - 0或‘\0’是一样的，但是和‘0’不同
- 0标志着字符串的结束，但它不是字符串的一部分
    - 计算字符串长度的时候不包含这个0
- 字符串以数组的形式存在，以数组或指针的形式访问
    - 更多地是以指针的形式
- `string.h`里有很多处理字符串的函数

字符串变量：

- char *str = "Hello";
- char word[] = "Hello";
- char line[10] = "Hello";

字符串常量/字面量

- "Hello"
- "Hello"会被编译器变成一个字符数组放在某处，这个数组的长度是6，结尾还有表示结束的0
- 两个相邻的字符串常量会被自动连接起来

C语言的字符串是以数组的形态存在的

- 不能用运算符对字符串做运算
- 通过数组的方式可以遍历字符串

字符串在C语言唯一特殊的地方是可以用双引号这种字符串字面量来初始化字符数组，C语言的标准库提供了一系列字符串函数

#### 字符串变量

```c
char *s = "Hello, word!";
```

- `s`是一个指针，初始化为指向一个字符串常量

    - 由于这个常量所在的地方为程序代码段，只能读不能写，所以实际上`s`是`const char *s`，但是由于历史原因，编译器接收不带const的写法
    - 但是试图对`s`所指的字符串做写入会导致严重的后果

- 如果需要修改字符串，应该在一开始就用数组：

    ```c
    char s[] = "Hello, word!";
    ```

    当定义数组时，系统会先在代码段创建一个字符串，然后通过系统程序将创建的字符串拷贝到当前的数组变量里面，用户可以对数组变量里面的字符串进行修改。

**指针还是数组**

- 数组：表示这个字符串就在这里
    - 它作为本地变量，空间会自动被回收
- 指针：表示这个字符串不知道在哪里
    - 作只读字符串，不会去写入它
    - 处理参数（比如数组作为函数参数传进来时，就可以看作是指针）
    - 动态分配空间

==如果要构造一个字符串—>数组==

==如果要处理一个字符串—>指针==

##### char *

- 字符串可以表达为`char *`的形式
- `char *`不一定是字符串
    - 它只是表示指向字符的指针，即这里有一个指针，指向一个字节或者一串连续的字节。可能指向的是字符型的数组（就像`int *`一样）
    - 只有它所指的字符数组有结尾的0时，才能说它所指的是字符串

#### 字符串输入输出

```c
char string[8];
scanf("%s", string);
printf("%s", string);
```

- `scanf`读入一个单词（到空格、tab或回车为止，不包括空格，空格只是用来分隔两个字符串的）

- `scanf`是不安全的，因为不知道要读入的内容的长度

    - 在%和s中间加上最多读入字符的个数，这个数字应该比数组大小小一

        ```c
        scanf("%7s", string);
        ```

    - 下一次`scanf`会取前一个`scanf`取剩下的字符，并根据给定字符个数取剩下的字符

##### 常见错误

- 以为`char *`是字符串类型，定义了一个字符串类型的变量string就可以直接用了
    - `char *string;`只是表示定义了一个指针变量，将来要指向某个内存空间的指针，但在一开始该指针没有被初始化
    - 由于没有对string初始化为0，就导致不是每次运行都出错（有可能出现在这台电脑上可以运行，到另一台电脑上就出错的情况）
- 空字符串
    - `char buffer[100] = "";`
        - 这是一个空字符串，buffer[0] == '\0'
    - `char buffer[] = "";`
        - 长度为1，只有一个buffer[0]，里面放不下任何字符串

#### 字符串数组

- ```c
    char **a
    ```

    - a是一个指针，指向另一个指针，那个指针指向一个字符（串）

- ```c
    char a[][]
    ```

    - 二维数组的列需要有具体的数值，否则编译无法通过

    - 可定义成`char a[][10]`

        - 意思是`a`是一个数组，该数组里面的每一个单元都是一个`char[10]`，`a[0]`相当于`char [10]`
        - ==用这种方式定义时，需要确定每个字符串的长度，若里面有单元长度超过10，就会编译失败==

        <img src="/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200322205413652.png" alt="image-20200322205413652" style="zoom:40%;" />

- ```c
    char *a[]
    ```

    - 在这种字符串数组中，`a[0]`相当于`char *`

    <img src="/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200322205506736.png" alt="image-20200322205506736" style="zoom:40%;" />

##### 程序参数

- `main`函数的参数

    ```c
    int main(int argc, char const *argv[])
    ```

    - `argc`是用来告诉用户后面的`argv[]`数组有多少个字符串

- `argv[0]`是命令本身

    - 当使用Unix的符号链接时，反映符号链接的名字

    ```c
    #include <stdio.h>
    
    int main(int argc, char const *argv[])
    {
        int i;
        for (i = 0, i < argc, i++) {
            printf("%d:%s\n", i, argv[i]); // 输出当前argv[]中的每个单元中的值
        }
        return 0;
    }
    ```

    在终端运行该test.c程序：

    ```shell
    (base)KungfudeMacBook-Pro:desktop kungfu$ gcc test.c
    (base)KungfudeMacBook-Pro:desktop kungfu$ ./a.out
    0: ./a.out
    (base)KungfudeMacBook-Pro:desktop kungfu$ ./a.out 123
    0: ./a.out
    1: 123
    (base)KungfudeMacBook-Pro:desktop kungfu$ ./a.out 123 qwer
    0: ./a.out
    1: 123
    2: qwer
    ```

    - 执行`a.out`时，命令行中输入的东西会依次放入`argv[]`数组中

- 若将一个链接`my`指向`a.out`

    ```shell
    (base)KungfudeMacBook-Pro:desktop kungfu$ ln -s a.out my
    (base)KungfudeMacBook-Pro:desktop kungfu$ ls -l my
    lrwxr-xr-x	1 kungfu  staff  5  3 22 21:23 my -> a.out
    (base)KungfudeMacBook-Pro:desktop kungfu$ ./my
    0: ./my
    (base)KungfudeMacBook-Pro:desktop kungfu$ ./my 123
    0: ./my
    1: 123
    ```

- 此时如果执行`./my`，实际上是通过`my`这个链接来执行的`a.out`，而不是直接执行的`./a.out`

- 可以通过查看`argv[]`数组来确认程序执行的方式

### 10.2 字符串函数

#### 单字符输入输出

##### putchar

```c
int putchar(int c);
```

- 向标准输出写入一个字符
- 返回写了几个字符，EOF (end of file)（-1）表示写失败

##### getchar

```c
int getchar(void);
```

- 从标准输入读入一个字符

- 返回类型时int，是为了返回EOF （-1）
    - windows —>按Ctrl+Z就可以收到EOF
    - Unix—>按Ctrl+D就可以收到EOF
    
    ```c
    #include <stdio.h>
    
    int main(int argc, char const *argv[])
    {
        int ch;
        while ((ch = getchar()) != EOF) {
            putchar(ch);
        }
        printf("EOF\n");  
        return 0;
    }
    ```
    
    ```shell
    (base)KungfudeMacBook-Pro:desktop kungfu$ cd Test/
    (base)KungfudeMacBook-Pro:desktop kungfu$ gcc test_getchar.c
    (base)KungfudeMacBook-Pro:desktop kungfu$ ./a.out
    123456 // 输入
    123456 // 输出
    qwerty
    qwerty
    asdfg
    asdfg
    ^C 	   // 此时输入为Ctrl+C
    (base)KungfudeMacBook-Pro:desktop kungfu$ ./a.out
    1qazxsw2
    1qazxsw2
    EOF    // 此时输入为Ctrl+D
    ```

#### 函数STRLEN

##### string.h

- ```c
    #include <string.h>
    ```

##### strlen

```c
size_t strlen(const char *s);
```

- 返回s的字符长度（不包括结尾的0）

![image-20200322221835427](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200322221835427.png)

**自己写一个输出字符串长度的函数**

![image-20200322223634013](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200322223634013.png)

#### 函数STRCMP

```c
int strcmp(const char *s1, const char *s2);
```

- 比较两个字符串，返回：
    - 0：s1 == s2
    - 大于0：s1 > s2，输出s1-s2的差值
    - 小于0：s1 < s2，输出s1-s2的差值

![image-20200323155856510](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200323155856510.png)

**自己写一个比较字符串的函数**

```c
// 数组版本
int mycmp(const char *s1, const char *s2) {
    int idx = 0
    while ((s1[idx] == s2[idx]) && (s1[idx] != '\0')) {
		idx++;
    }
    return s1[idx] - s2[idx];
}
```

![image-20200323161213363](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200323161213363.png)

#### 函数STRCPY

```c
char *strcpy(char *restrict dst, const char *restrict src)
```

- 把src的字符串拷贝到dst
    - restrict表明src和dst不能重叠（C99）
- 返回dst
    - 为了能将代码链起来

##### 复制一个字符串

```c
char *dst = (char *)malloc(strlen(src) + 1); // 先动态分配内存
strcpy(dst, src);
```

**自己写一个拷贝字符串函数**

```c
// 数组版本
char *mycpy(char *dst, const char *src) {
    int idx = 0;
    while (src[idx] != '\0') {
        dst[idx] = src[idx];
        idx++;
    }
    dst[idx] = '\0';
    return dst;
}
```

```c
// 指针版本
char *mycpy(char *dst, const char *src) {
    char *ret = dst;	// 保证返回dst
    while (*src != '\0') {
        *dst = *src;
        dst++;
        src++;
    }
    *dst = '\0';
    return rst;
}
```

```c
// 指针版本_简化
char *mycpy(char *dst, const char *src) {
    char *ret = dst;	// 保证返回dst
    while (*src) {
        *dst++ = *src++;
    }
    *dst = '\0';
    return rst;
}
```

```c
// 指针版本_再简化
char *mycpy(char *dst, const char *src) {
    char *ret = dst;	// 保证返回dst
    while ( *dst++ = *src++) 
        ;
    *dst = '\0';
    return ret;
}
```

#### 函数STRCAT

```c
char *strcat(char *restrict s1, const char *restrict s2);
```

- 把s2拷贝到s1的后面，接成一个长的字符串
- 返回s1
- s1必须具有足够的空间

#### 安全问题

- strcpy和strcat都有可能出现安全问题
    - 如果目的地没有足够的空间，就会出错

##### 安全版本

```c
char *strncpy(char *restrict dst, const char *restrict src, size_t n);
```

```c
char *strncat(char *restrict s1, const char *restrict s2, size_t n);
```

```c
int strncmp(const char *s1, const char *s2, size_t n);
```

#### 字符串搜索函数

##### 字符串中找字符

```c
char *strchr(const char *s, int c);	// 在s中找从左边数过来c第一次出现的位置
```

```c
char *strrchr(const char *s, int c);	// 在s中找从右边数过来c第一次出现的位置
```

- 返回的是指针，指向所找的字符
- 返回NULL表示没有找到

**找第二个字符**

![image-20200323181412648](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200323181412648.png)

**找到字符并将该字符以及该字符以后的东西复制到另一个字符串中去**

![image-20200323182027826](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200323182027826.png)

**输出所找字符前面的字符串，不包括该字符**

![image-20200323182337053](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200323182337053.png)

##### 字符串中找字符串

```c
char *strstr(const char *s1, const char *s2);
```

```c
char *strcasestr(const char *s1, const char *s2);	// 忽略大小写
```

### 11.1 枚举

- 枚举是一种用户定义的数据类型，它用关键字eume以如下语法来声明

    - `enum枚举类型名字{ 名字0, ……, 名字n };`

- 枚举类型名字通常并不真的使用，要用的是大括号里面的名字，因为它们就是常量的符号，它们的类型时int，值则是依次从0到n。如：

    ```c
    enum colors {red, yellow, green};
    ```

    - red的值是0，yellow是1，green是2

- 当需要一些可以排列起来的常量值时，定义枚举的意义就是给了这些常量值名字

```c
#include <stdio.h>

enum color {red, yellow, green};	// 声明一个叫color的新的数据类型，类似int，float

void f(enum color c);	// 用的时候必须带上enum

int main(void) {
    enum color t = red;
    
    scanf("%d", &t);
    f(t);
    
    return 0;
}

void f(enum color c) {
    printf("%d\n", c);
}
```

- 实际上C语言内部，枚举就是以整数来做内部计算和外部输入输出的

##### 套路：自动计数的枚举

```c
enum COLOR {RED, YELLOW, GREEN, NumCOLORS};
```

- 在枚举的最后加上一个变量，作为所有元素个数就计数总和

**声明枚举量的时候可以指定值**

```c
enum COLOR 
{
    RED = 1, 
    YELLOW, 	// YELLOW为2
    GREEN = 5	// 跳过了3和4
};
```

- 虽然枚举类型可以当做类型使用，但是实际上很(bu)少(hao)用
- 如果遇到一些列有意义的排比的数字，用枚举比const int 方便
- 枚举比宏（macro）好，因为枚举有int类型

### 11.2 结构

#### 结构类型

##### 声明结构类型

- 形式一

    ```c
    struct point {
        int x;
        int y;
    };
    
    struct point p1, p2;
    ```

    - p1，p2都是point类型的结构体变量，里面都有x和y的值

- 形式二

    ```c
    struct {
        int x;
        int y;
    } p1, p2;
    ```

    - p1，p2都是无名结构，里面都有x和y的值

- 形式三

    ```c
    struct point {
        int x;
        int y;
    } p1, p2;
    ```

    - p1，p2都是point类型的结构体变量，里面都有x和y的值

==对于第一种和第三种形式，都声明了结构point。但是第二种形式没有声明point，只是定义了两个变量==

##### 在函数内/外？

- 和本地变量一样，在函数内部声明的结构类型只能在函数内部使用
- 所以通常在函数外部声明结构类型，这样就可以被多个函数所使用的了

##### 结构变量

```c
struct date {
    int month;
    int day;
    int year;
};
```

- 这只是在声明一个名为date的结构类型

```c
struct date today;
```

- today才是一个具体的结构变量

##### 结构的初始化

```c
#include <stdio.h>

struct date {
    int month;
    int day;
    int year;
};

int main(int argc, const char * argv[]) {
    struct date today = {3, 24, 2020};
    // 未初始化的值默认为0
    struct date thismonth = {.month = 3, .year = 2020};

    printf("Today's date is %i-%i-%i.\n",
    	today.year, today.month, today.day);
    printf("This month is %i-%i-%i.\n",
    	thismonth.year, thismonth.month, thismonth.day);
    
    return 0;
}
```

输出结果为：

![image-20200324163928678](/Users/kungfu/Library/Application Support/typora-user-images/image-20200324163928678.png)

##### 结构成员

- 结构和数组有点像
- 内容
    - 数组里的单元必须是相同类型的
    - 结构的成员可以是不同类型的
- 访问
    - 数组用`[]`运算符合下标访问其成员
        - `a[0] = 10;`
    - 结构用 `.` 运算符和名字访问其成员
        - `today.day`
        - `student.firstName`
        - `p1.x`
        - `p2.y`

##### 结构运算

- 要访问整个结构，直接用结构变量的名字

- 对于整个结构，可以赋值、取地址，也可以传递给函数参数

    - ```c
        p1 = (struct point){5, 10};	// 相当于p1.x = 5; p1.y = 10;
        ```

        将{5, 10}强制转换成point类型的结构，并赋值给p1

    - ```c
        p1 = p2; // 相当于p1.x = p2.x; p1.y = p2.y;
        ```

    ==数组无法做这两种运算==

##### 结构指针

- 和数组不同，结构变量的名字并不是结构变量的地址，必须使用&运算符取地址给指针

- ```c
    int a[] = {1,2,3};
    int *p = a;	// p可以取到数组a的地址，相当于int *p = &a;
    ```

- ```c
    struct date today = {3, 24, 2020};
    struct date *pDate = &today;
    ```

#### 结构与函数

##### 结构作为函数参数

```c
int numberOfDays(struct date d)
```

- 整个结构可以作为参数的值传入函数
- 这个时候是在函数内部新建了一个结构变量，并复制调用者的结构的值，与数组不同
- 函数也可以返回一个结构

==这些都和数组不同==

**【例题】：计算tomorrow**

```c
#include <stdio.h>
#include <stdbool.h>

struct date {
    int month;
    int day;
    int year;
};

bool isLeap(struct date d);
int numberOfDays(struct date d);

int main(int argc, const char * argv[]) {
    struct date today, tomorrow;
    
    printf("Enter today's day (mm dd yyyy):");
    scanf("%i %i %i", &today.month, &today.day, &today.year);
    
    if (today.day != numberOfDays(today)) {
        tomorrow.day = today.day + 1;
        tomorrow.month = today.month;
        tomorrow.year = today.year;
    } else if (today.month == 12) {
        tomorrow.day = 1;
        tomorrow.month = 1;
        tomorrow.year = today.year + 1;
    } else {
        tomorrow.day = 1;
        tomorrow.month = today.month + 1;
        tomorrow.year = today.year;
    }
    
    printf("Tomorrow's date is %i-%i-%i.\n",
           tomorrow.year, tomorrow.month, tomorrow.day);
    
    return 0;
}

// 判断today是不是本月的最后一天
int numberOfDays(struct date d) {
    int days;
    
    const int daysPerMonth[12] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    
    // 闰年的二月是29天
    if ((d.month == 2) && isLeap(d)) {
        days = 29;
    } else {
        days = daysPerMonth[d.month - 1];   // 数组下标从0开始，取对应月份天数需减一
    }
    
    return days;
}

// 判断本年是不是闰年
bool isLeap(struct date d) {
    bool leap = false;
    
    if (((d.year % 4 == 0) && (d.year % 100 != 0)) || (d.year % 400 == 0)) {
        leap = true;
    }
    
    return leap;
}
```

##### 输入结构

- 没有直接的方式可以一次scanf一个结构

- 如果直接传

    ```c
    #include <stdio.h>
    
    struct point {
        int x;
        int y;
    };
    
    void getStruct(struct point);
    void output(struct point);
    void main() {
        struct point t = {0, 0};
        getStruct(t);
        output(t);
    }
    
    void getStruct(struct point p) {
        scanf("%d", &p.x);
        scanf("%d", &p.y);
        printf("%d %d", p.x, p.y);
    }
    
    void output(struct point p) {
        printf("%d %d", p.x, p.y);
    }
    ```

    - `getStruct`函数中的p和`main`中的y是不同的，在函数读入了p的值以后，没有任何东西回到`main`，所以y还是`{0, 0}`，不会变成输入的值。
    - 问题在于，传入函数的是外面那个结构的克隆体，而不是指针；这与数组做参数传给函数是不同的

- 解决方案一

    - 在这个输入函数中，完全可以创建一个临时的结构变量，然后把这个结构返回给调用者

        ```c
        #include <stdio.h>
        
        struct point {
            int x;
            int y;
        };
        
        struct point getStruct(void); // 让getStruct不接受参数，并返回一个point型的变量
        void output(struct point);
        void main() {
            struct point y = {0, 0};
            y = getStruct(); // 用y接收getStruct返回的变量
            output(y);
        }
        
        struct point getStruct(void) {
            struct point p;	// 内部定义一个point型的变量
            scanf("%d", &p.x);
            scanf("%d", &p.y);
            printf("%d %d", p.x, p.y);
            return p; // 返回p，并且在离开函数时清除变量p
        }
        
        void output(struct point) {
            printf("%d %d", p.x, p.y);
        }
        ```

    - 这种方法既费时间又费空间

- 解决方案二

    - 结构指针做为参数
    - K & R (P131)
        - “If a large structure is to be passed to a function, it is generally more efficient to pass a pointer than to copy the whole structure.”

##### 指向结构的指针

```c
struct date *p = &myday; // 定义了一个指针p指定myday，即p指向myday的地址
(*p).month = 12; // 取p所指结构变量的month，并赋值为12
// 等价于
p->month = 12;
```

- 用`->`表示指针所指的结构变量中的成员

```c
#include <stdio.h>

struct point {
    int x;
    int y;
};

struct point *getStruct(struct point *); // getStruct返回的是指针，接收的也是指针

// 两种输出方式
void output(struct point);  // 接收结构体，并输出当前结构体内各成员的值
void print(const struct point *p); // 接收指向结构体的指针，并输出当前结构体内各成员的值

int main() {
    struct point t = {0, 0};
    getStruct(&t); // 将t的地址传给getStruct的指针做运算，并返回指向该结构体的指针
    output(t); // 传结构体
    print(getStruct(&t)); // 传指向结构体的指针
    return 0;
}

struct point *getStruct(struct point *p) {
    scanf("%d", &p->x);
    scanf("%d", &p->y);
    return p;
}

void output(struct point p) {
    printf("%d %d\n", p.x, p.y);

}

void print(const struct point *p) {
    // const表明print不会对传入参数做任何修改
    printf("%d %d\n", p->x, p->y);
}
```

#### 结构中的结构

##### 数组中的结构

```c
struct date dates[100];	// 有一个数组dates由100个date类型的结构变量组成
struct date dates[] = {
    {4,5,2005},
    {2,4,2005},
}; // 注意这里的分号
```

##### 结构中的结构

```c
struct dateAndTime {
    struct date sdate;
    struct time stime;
};
```

##### 嵌套的结构

**矩形**

```c
struct point {
    int x;
    int y;
};

struct rectangle {
    struct point pt1;
    struct point pt2;
};
```

如果有变量`struct rectangle r;`，就可以有：`r.pt1.x`、`r.pt1.y`、`r.pt2.x`、`r.pt2.y`

如果有指针变量定义:

```c
struct rectangle r;
struct rectangle *rp;
rp = &r;
```

则下面四种表达形式是等价的

```c
r.pt1.x
rp->pt1.x
(r.pt1).x
(rp->pt1).x  
// 但是没有rp->pt1->x，因为pt1不是指针
```

### 11.3 联合

#### 类型定义

##### 自定义数据类型(typedef)

- C语言提供了一个叫做==typedef==的功能来声明一个已有的数据类型的新名字。比如:

    ```c
    typedef int Length;
    ```

    - 使得`Length`成为`int`类型的别名
    - 这样的话，Length这个名字就可以代替int出现在变量定义和参数声明的地方了：
        - `Length a, b ,len;`
        - `Length numbers[10];`

##### Typedef

```c
typedef struct ADate { // 在typedef和最后单词Date中间的所有的东西，是原来的类型
    int month;
    int day;
    int year;
} Date; // Date是新的名字，新名字只能是一个单词
```

- 改善了程序的可读性

如：

```c
typedef *char[10] Strings; // Strings是10个字符串的数组的类型
```

#### 联合

```c
union AnElt {
    int i;
    char c;
} elt1, elt2; // elt1和elt2占据的是同一个内存空间

elt1.i = 4;
elt2.c = 'a'; // 存在互相覆盖内存空间的情况
```

**【例题】**

用union得到一个整数内部的各个字节

![image-20200325171351300](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200325171351300.png)

- 以低位在前方式存放，实际为`000004D2`

### 12.1 全局变量

#### 全局变量

- 定义在函数外面的变量是全局变量
- 全局变量具有全局的生存期和作用域
    - 它们与任何函数都无关
    - 在任何函数内部都可以使用它们

##### 全局变量初始化

- 没有初始化的全局变量会得到0值

    - 指针会得到NULL值

- 只能用***编译时刻已知的值***来初始化全局变量

    ```c
    int gAll = f();
    ```

    - `f()`不符合❌

    ```c
    int gAll = 12;
    int g2 = gAll;
    ```

    - `gAll`只能识别为变量，也不符合❌

    ```c
    const int gAll = 12;
    int g2 = gAll;
    ```

    - `gAll`被定义成12，符合条件，但***不建议用一个全局变量去初始化另一个全局变量⚠️***

- 它们的初始化发生在main函数之前

##### 被隐藏的全局变量

- 如果函数内部存在于全局变量同名的变量，则全局变量被隐藏（取代）

#### 静态本地变量

- 在本地变量定义时加上`static`修饰符就成为静态本地变量

- 当函数离开的时候，静态本地变量会继续存在并保持其值

- 静态本地变量的初始化***只会在第一次进入***这个函数时做，以后进入函数会保持上次离开时的值

    ![image-20200325180255593](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200325180255593.png)

- 静态本地变量实际上是特殊的全局变量

- 它们位于相同的内存区域

    ![image-20200325181457617](/Users/kungfu/Library/Application Support/typora-user-images/image-20200325181457617.png)

    - 可以看到静态本地变量和全局变量在同一个内存区域，普通本地变量在另一个内存区域

- 静态本地变量具有全局的生存期，函数内的局部作用域

    - static在这里的意思是局部作用域（本地可访问），即只能在这个函数里面可以访问它

#### 全局变量贴士

##### *返回指针的函数

- 返回本地变量的地址是危险的
- 返回全局变量或静态本地变量的地址是安全的的
- 返回在函数内malloc的内存是安全的的，但容易造成问题
- 最好的做法是返回传入的指针

##### tips

- 不要使用全局变量来在函数间传递参数和结果
- 尽量避免使用全局变量
    - 丰田汽车的案子
- *使用全局变量和静态本地变量的函数是线程不安全的

### 12.2 编译预处理和宏

##### 编译预处理指令

- #开头的是编译预处理指令

- 编译预处理指令不是C语言的成分，但是C语言程序离不开它们

- **#define用来定义一个宏**

    ```c
    #include <stdio.h>
    
    #define PI 3.14159 // 在编译之前会先做一次编译预处理，将所有的PI替换成3.14159
    
    int main(int argc, char const *argv[])
    {
    	printf("%f\n", 2 * PI *3.0);
    	return 0;
    }
    ```

    ![image-20200325220301532](/Users/kungfu/Library/Application Support/typora-user-images/image-20200325220301532.png)

    - `gcc --save-temps main.c`会保留编译过程当中的临时文件

    - `.c`经过编译预处理，产生一个中间结果文件`.i`

        ![image-20200325220906836](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200325220906836.png)

        - `PI` 被替换成了`3.14159`

    - `.i`由C的编译器编译，产生一个`.s`的汇编代码文件

    - `.s`做汇编，变成一个目标代码文件`.o`

    - 目标代码文件经过链接等其他操作，最后形成`a.out`

- ==注意结尾没有分号==，以为这不是Cd语句
- 名字必须是一个单词，值可以是各种东西
- 在C语言的编译器开始编译之前，编译预处理程序（cpp）会把程序中的名字换成值
  
    - 完全的文本替换
- `gcc --save-temps`

##### 宏

- 如果一个宏的值中有其他宏的名字，也会被替换

- 如果一个宏的值超过一行，最后一行之前的行末需要加\

    ```c
    #define PRT printf("%f ", PI); \
    			printf("%f\n", PI2)
    ```

- 宏的值后面出现的注释不会被当作宏的值的一部分

##### 没有值的宏

```c
#define _DEBUG
```

- 这类宏是用于条件编译的，后面有其他的编译预处理指令来检查这个宏是否被定义过了

##### 预定义的宏

- `__LINE__` ：源代码文件的行号，即当前指令所在行的行号
- `__FILE__` ：源代码文件的文件名，包括文件路径
- `__DATE__` ：编译时的日期
- `__TIME__`  ：编译时的时间
- `__STDC__` ：

#### 带参数的宏

##### 像函数的宏

```c
#include <stdio.h>

#define cube(x) ((x) * (x) * (x))

int main(int argc, const char * argv[]) {

    printf("%d\n", cube(5)); // 用5替换x，再用5*5*5替换cube(5)
    return 0;
}
```

##### 带参数的宏的定义原则

- 一切都要括号

    - 整个宏的值要有括号
    - 参数出现的每个地方都要括号

- ```c
    #define RADTODEG(x) ((x) * 57.29578)
    ```

**补充**

- 带参数的宏在大型的代码中使用非常普遍
    - 当它去代替函数时，它的运行效率会比函数来得高
    - 但是由于它导出展开，会导致代码变多，牺牲空间换取了效率
- `#` 和 `##` 都是宏的运算符
    - 甚至可以产生新的函数
- 宏的缺点：在参数的使用中，没有任何类型检查；容易出现类型使用无法检查的问题
    - 可以用inline机制取代带参数的宏
    - inlin是函数，但是没有函数调用时的额外开销，会做参数类型的检查

##### 其他编译与处理指令

- 条件编译
- error
- ……

### 12.3 大程序结构

#### 多个源代码文件   

##### 多个.c文件

- main()函数里面代码太长了适合分成几个函数
- 一个源代码文件太长了适合分成几个文件
- 两个独立的源代码文件不能编译成可执行的程序

#### 项目

- 在Dev C++中新建一个项目，然后把几个源代码文件加进去
- 对于项目，Dev C++的编译会把一个项目中所有的源代码文件都编译后，链接起来
- 有的IDE有分开的编译和构建两个按钮，前者是对单个源代码文件编译，后者是对整个项目做链接

##### 编译单元

- 一个.c文件是一个编译单元
- 编译器每次编译只处理一个编译单元

#### 头文件

- 把函数原型放到一个头文件（以`.h`结尾）中，在需要调用这个函数的源代码文件（`.c`文件）中`#include`这个头文件，就能让编译器在编译的时候知道函数的原型

- 在使用和定义这个函数的地方都应该`#include`这个头文件

- 一般的做法就是任何`.c`都有对应的同名的`.h`，把所有对外公开的函数的原型和全局变量的声明都放进去

    - max.h

        ```c
        // max.h
        int max(int a, int b);	// max()的函数原型
        ```

    - main.c

        ```c
        // main.c
        #include <stdio.h>
        #include "max.h"	//编译预处理时会被替换成max()的函数原型
        
        int main(int argc, const char * argv[]) {
            
            int a = 5;
            int b = 6;
            printf("%d\n", max(a, b));
            
            return 0;
        }
        ```

    - max.c

        ```c
        // max.c
        #include "max.h	// 用来判断对max()的定义是否符合有文件
        
        int max(int a, int b) {
            return a > b ? a : b;
        }
        ```

##### #include

- `#include`是一个编译预处理指令，和宏一样，在编译之前就出来了

- 它会把头文件的全部内容原封不动的插入到它所在的地方

    - 所以也不一定要在.c文件的最前面`#include`

        ![image-20200327165326676](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200327165326676.png)

        - `gcc`可以同时编译多个`.c`文件

        ![image-20200327165440607](/Users/kungfu/Library/Application Support/typora-user-images/image-20200327165440607.png)

        - `gcc --save-temps main.c -c `只对main.c做编译，不做链接 

        ![image-20200327170014274](/Users/kungfu/Library/Application Support/typora-user-images/image-20200327170014274.png)

        - 查看`main.i`的最后50行

        ![image-20200327170255743](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200327170255743.png)

        - 在`main.c`的第二行放入`max.h`，`max.h`第一行的内容是`int max(int a, int b);`

##### ""还是<>

- #includ有两种形式来指出要插入的文件
    - `“ ”`：要求编译器首先在当前目录（.c文件所在的目录）寻找这个文件，如果没有，到编译器指定的目录找
    - `<>`：让编译器只在系统指定的目录去找
    - 一般来说：自己写的头文件用`" "`，系统标准库的头文件用`<>`
- 编译器自己知道自己标准库的头文件在哪里
- 环境变量和编译器命令行参数也可以指定寻找头文件的目录

##### #include的误区

- `#include`不是用来引入库的，这种说法不正确
    - `#include`其实只是将它后面那个头文件所包含的内容原封不动的插入到它所在的那一行来
- `stdio.h`里面只有printf的原型，printf的代码在另外的地方，某个.lib(Windows )或.a(Unix)中
- 现在的C语言编译器默认会引入所有的标准库
- `#include <stdio.h>` 只是为了让编译器知道printf函数的原型，保证调用时给出的参数值是正确的类型

##### 不对外公开的函数

- 在函数前面加上static就使得它成为只能在所在的编译单元(.c文件)中被使用的函数
- 在全局变量前面加上static就使得它成为只能在所在的编译单元(.c文件)中被使用的全局变量

#### 声明

如果在max.c中定义一个int型全局变量gAll，想在main.c中使用这个变量，就需要在max的头文件mac.h中声明gAll

```c
// max.h
int max(int a, int b);	// max()的函数原型
entern int gAll;	// 声明gAll
```

```c
// max.c
#include "max.h	// 用来判断对max()的定义是否符合有文件

int gAll = 12;	// 定义gAll

int max(int a, int b) {
    return a > b ? a : b;
}
```

```c
// main.c
#include <stdio.h>
#include "max.h"	//编译预处理时会被替换成max()的函数原型

int main(int argc, const char * argv[]) {
    
    int a = 5;
    printf("%d\n", max(a, gAll));	// 直接使用gAll
    
    return 0;
}
```

##### 变量的声明

- `int i;` 是变量的定义

- `entern int i;` 是变量的声明

##### 声明和定义

- 声明是不产生代码的东西
    - 函数原型
    - 变量声明
    - 结构声明
    - 宏声明
    - 枚举声明
    - 类型声明
    - inline函数
- 定义是产生代码的东西
    - 函数
    - 全局变量
- 编译器看到声明不会产生代码，而是默默记下这个声明

##### 头文件和声明

- 只有声明可以被放在头文件中
    - 是规则不是法律
- 否则会造成一个项目中多个编译单元里有重名的实体
    - *某些编译器允许几个编译单元中存在同名的函数，或者用weak修饰符来强调这种存在

##### 重复声明

- 同一个编译单元里，同名的结构不能被重复声明

- 如果头文件里有结构的声明，很难做到这个头文件不会在一个编译单元里被`#include`多次

    - 如果项目中除了`main.c`、`max.c`、`max.h` 还有一个`min.h`，并且`min.h`中`#include “max.h”`，如果此时`main.c`中同时`#include “max.h”`和`#include “min.h”`

        ```c
        // max.c
        #include "max.h	// 用来判断对max()的定义是否符合有文件
        
        int max(int a, int b) {
            return a > b ? a : b;
        }
        ```

        ```c
        // max.h
        int max(int a, int b);	// max()的函数原型
        entern int gAll;	// 声明gAll
        
        // 声明Node
        struct Node {
            int value;
            char *name;
        };
        ```

        ```c
        // min.h
        #include "min.h"
        ```

        ```c
        // main.c
        #include <stdio.h>
        #include "max.h"	
        #include "min.h"
        
        int main(int argc, const char * argv[]) {
            
            int a = 5;
            printf("%d\n", max(a, gAll));	// 直接使用gAll
            
            return 0;
        }
        ```

        此时，main.c中的内容就相当于

        ```c
        // main.c
        #include <stdio.h>
        
        // #include "max.h"
        int max(int a, int b);	
        entern int gAll;	
        
        struct Node {
            int value;
            char *name;
        };	
        
        // #include "min.h"  
        // min.h中又#include max.h，导致重复声明
        /*int max(int a, int b);	
        entern int gAll;	
        
        struct Node {
            int value;
            char *name;
        };*/
        
        int main(int argc, const char * argv[]) {
            
            int a = 5;
            printf("%d\n", max(a, gAll));	// 直接使用gAll
            
            return 0;
        }
        ```

- 所以需要“标准头文件结构”

    max.h需要变成

    ```c
    #ifndef _MAX_H_	// 如果当前编译单元中_MAX_H_没有被定义过，就定_MAX_H_；							// 如果已经出现，则不执行定义命令
    #define _MAX_H_
    
    int max(int a, int b);	
    entern int gAll;	
    
    struct Node {
        int value;
        char *name;
    };	
    
    #endif
    ```

##### 标准头文件结构

```c
#ifndef _LIST_HEAD_
#define _LIST_HEAD_
	……
#endif
```

- 后面不加分号

- 运用条件编译和宏，保证这个头文件在一个编译单元中只会被`#include`一次

- #pragma once也能起到相同的作用，但不是所有编译器都支持

### 13.1 文件

#### 格式化输入输出

##### printf格式

`%[flags][width][.prec][hlL]type`

**--flag**

|  Flag   |             含义             |
| :-----: | :--------------------------: |
|    -    |            左对齐            |
|    +    | 在前面放+或-/正数前强制输出+ |
| (space) |           正数留空           |
|    0    |            0填充             |

- 左对齐

    ![image-20200327221910852](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200327221910852.png)

- 输出+

    ![image-20200327222425166](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200327222425166.png)

- 0填充

    ![image-20200327223525609](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200327223525609.png)

**--width**

| width或prec |             含义              |
| :---------: | :---------------------------: |
|   number    |        输出最小字符数         |
|      *      |   *处被填充的数为输出字符数   |
|   .number   |        小数点后的位数         |
|     .*      | *处被填充的数为小数点后的位数 |

- `.number`

    ![image-20200327224215287](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200327224215287.png)

- `*` 和 `.*`

    ![image-20200327225442217](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200327225442217.png)

**--hlL(修饰符)**

| 类型修饰 |    含义     |
| :------: | :---------: |
|    hh    |  单个字节   |
|    h     |    short    |
|    l     |    long     |
|    ll    |  long long  |
|    L     | long double |

- hh

    ![image-20200327230242171](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200327230242171.png)

**--type**

| type |        用于        | type |      用于       |
| :--: | :----------------: | :--: | :-------------: |
| i或d |        int         |  g   |      float      |
|  u   |    unsigned int    |  G   |      float      |
|  o   |       八进制       | a或A | 十六进制浮点数  |
|  x   |      十六进制      |  c   |      char       |
|  X   | 大写字母的十六进制 |  s   |     字符串      |
| f或F |       float        |  p   |    指针地址     |
| e或E |        指数        |  n   | 读入/写出的个数 |

- n

    ![image-20200328012206429](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328012206429.png)

    - 和`scanf()`同理

##### scanf

`%[flag]type`

**--flag**

| flag |      含义      | flag |     含义     |
| :--: | :------------: | :--: | :----------: |
|  *   |      跳过      |  l   | long，double |
| 数字 | 最大输入字符数 |  ll  |  long long   |
|  hh  |      char      |  L   | long double  |
|  h   |     short      |      |              |

- `*`

    ```c
    #include <stdio.h>
    
    int main(int argc, char const *argv[])
    {
    	int num;
    	scanf("%*d%d", &num);	// 跳过第一个d
    	printf("%d\n", num);	
    
    	return 0;
    }
    ```

    ![image-20200328014243270](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328014243270.png)

    - `gcc 12_3.c -o test_pass` ：编译12_3.c，编译后的文件叫做test_pass

**--type**

| type | 用于                         | type       | 用于           |
| :--: | ---------------------------- | ---------- | -------------- |
|  d   | int                          | a，e，f，g | float          |
|  i   | 整数，可能为十六进制或八进制 | c          | char           |
|  u   | unsigned int                 | s          | 字符串（单词） |
|  o   | 八进制                       | […]        | 所允许的字符   |
|  x   | 十六进制                     | p          | 指针           |

- `i`

    ```c
    #include <stdio.h>
    
    int main(int argc, char const *argv[])
    {
    	int num;
    	scanf("%i", &num);
    	printf("%d\n", num);	
    
    	return 0;
    }
    ```

    ![image-20200328014120732](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328014120732.png)

    - 分别以十进制，十六进制，八进制读入；以十进制输出

- `[…]`

    如：`[^,]` ：读入 `,`之前的所有东西

##### printf 和 scanf 的返回值

- 读入的项目数

- 输出的字符数（包括末尾的\n换行，也算一个字符）

    ```c
    #include <stdio.h>
    
    int main(int argc, char const *argv[])
    {
    	int num;
    
    	int i1 = scanf("%i", &num);
    	int i2 = printf("%d\n", num);	
    	printf("i1 = %d\ti2 = %d\n", i1, i2);
    
    	return 0;
    }
    ```

    ![image-20200328015934837](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328015934837.png)

- 在要求严格的程序中，应该判断每次调用scanf或printf的返回值，从而了解程序运行中是否存在问题

#### 文件输入输出

##### 重定向

```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int num;

	int i1 = scanf("%i", &num);
	int i2 = printf("%d\n", num);	
	printf("i1 = %d\ti2 = %d\n", i1, i2);

	return 0;
}
```

- 运行test，读取数据，并将输出结果保存在12.out里面

    ![image-20200328145116532](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328145116532.png)

- 打开12.out

    ![image-20200328145149826](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328145149826.png)

- 将输入结果放在12.in里面

    ![image-20200328145339187](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328145339187.png)

- 运行test，将文件12.in里面的内容输入，并得到输出结果

    ![image-20200328145432195](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328145432195.png)

- 运行test，将文件12.in里面的内容输入，并将输出结果放在12.out里面

    ![image-20200328145614464](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328145614464.png)

##### FILE

**打开文件的标准代码**

```c
FILE *fp = fopen("file", "r"); // 打开文件，用来读，如果没有打开文件，返回NULL
if (fp) {
    fscanf(fp, …);
    fclose(fp);
} else {
    …
}
```

![image-20200328151259014](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328151259014.png)

- 12.in里面存放的是12345
- 删除12.in

![image-20200328151422766](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328151422766.png)

##### fopen

| 符号 |                         含义                         |
| :--: | :--------------------------------------------------: |
|  r   |                    打开文件，只读                    |
|  r+  |                打开读写，从文件头开始                |
|  w   |   打开只写；如果不存在则新建，如果存在则原来的清空   |
|  w+  |   打开读写；如果不存在则新建，如果存在则原来的清空   |
|  a   | 打开追加；如果不存在则新建，如果存在则原来的末尾添加 |
|  x   | 加在上面符号的后面，只新建，如果文件已存在则不能打开 |

#### 二进制文件

- 其实所有的文件最终都是二进制
- 文本文件无非是用最简单的方式可以读写的文件
    - more、tail
    - cat
    - vi
- 而二进制文件是需要专门的城程序来读写的文件
- 文本文件的输入输出是格式化，可能经过转码

##### 文本文件 VS 二进制文件

- Unix喜欢用文本文件来做数据存储和程序配置
    - 交互式终端的出现使得人们喜欢用文本和计算机“talk”
    - unix的shell提供了一些读写文本的小程序
- windows喜欢用二进制文件
    - DOS是草根文化，并不继承和熟悉Unix文化
    - PC刚开始的时候能力有限，DOS的能力更有限，二进制更接近底层
- 文本文件
    - 优势：方便人类读写，而且跨平台
    - 缺点：程序输入输出要经过格式化，开销大
- 二进制文件
    - 优势：输入输出直接，程序读写快
    - 缺点：人类读写困难，而且不跨平台
        - int的大小不一致，大小端问题……

##### 程序为什么要文件

- 配置
    - Unix用文本，Windows 用注册表
- 数据
    - 稍微大一点的数据都放在数据库
- 媒体
    - 图片，声音，视频等
    - 这些只能是二进制的
- 现实是，程序通过第三方库来写文件，调用函数把数据都装载到内存中，然后去做输出使用，很少直接读二进制文件

##### 二进制读写

- 读
    - `size_t fread(void *restrict ptr, size_t size, size_t nitems, FILE *restrict stream);`
        - 第一个参数是指针，指向要读写的内存地址
        - 第二个参数是这块内存的大小/一个结构的大小
        - 第三个参数是有几个这样的内存/结构
        - 第四个参数是文件指针
- 写
    - `size_t fwrite(const void *restrict ptr, size_t size, size_t nitems, FILE *restrict stream);`
        - 
- 注意FILE指针是最后⼀一个参数
- 返回的是成功读写的字节数

##### nitem

- 因为⼆二进制⽂文件的读写一般都是通过对⼀一个结构变量的操作来进⾏行的
- 于是nitem就是⽤用来说明这次读写⼏几个结构变量

**例子**



##### 在文件中定位

- `long ftell(FILE *stream);`

- `int fseek(FILE *stream, long offset, int whence);`

    - SEEK_SET:从头开始 

    - SEEK_CUR:从当前位置开始 

    - SEEK_END:从尾开始(倒过来)

        ```c
        fseek(fp, 0L，SEEK_END)
        ```

##### 可移植性

- 这样的⼆二进制⽂文件不具有可移植性
    - 在int为32位的机器上写成的数据⽂文件⽆无法直接在int 为64位的机器上正确读出

- 解决⽅方案之⼀一是放弃使⽤用int，⽽而是typedef具有明确 ⼤大⼩小的类型

- 更好的⽅方案是⽤用⽂文本

### 13.2 位运算

#### 按位运算

##### `&`：按位的与

- 如果 (x)~i~ == 1 并且 (y)~i~ == 1 ，那么(x & y)~i~ = 1 
- 否则 (x & y)~i~ == 0
- 按位与常用于两种应用：
    - 让某一位或某些位为0：x & 0xFE（11111110），让最后一位变成0
    - 取一个数中的一段：x & 0xFF（00000000 00000000 00000000 11111111），取32位int的最后一段

##### `|`：按位的或

- 如果 (x)~i~ == 1 或 (y)~i~ == 1 ，那么(x | y)~i~ = 1 
- 否则 (x | y)~i~ == 0
- 按位或常用于两种应用：
    - 使得一位或几个位为1：x | 0x01（00000001），让最后一位变成1
    - 把两个数拼起来：0x00FF | 0xFF00，变成0xFFFF

##### `~`：按位取反

- (`~`x)~i~ = 1 - (x)~i~
- 把1变成0，把0变成1
    - 7的二进制是0111，（x | 7）可以使得x低三位变成1
    - （x | ~7），就可以使得x低三位变成0

##### `^`：按位的异或

- 如果 (x)~i~ ==  (y)~i~  ，那么(x ^ y)~i~ == 0 
- 否则 (x ^ y)~i~ == 1
- 如果两个位相等，那么结果为0；不相等，结果为1
- 可以做加密运算

#### 移位运算

##### `<<`：左移

- i << j
    - i中所有位向左移动j个位置，右边填入0
    - 所有小于int的类型，移位都以int的当时来做，结果是int
        - `x <<= 1` 等价于 x *= 2
        - `x <<= n` 等价于 x *= 2^n^

##### `>>`：右移   

- i >> j
    - i中所有位向右移动j个位置
    - 所有小于int的类型，移位都以int的当时来做，结果是int
    - 对于unsigned的类型，左边填入0
    - 对于signed的类型，左边填入原来的最高位（符号保持不变）

- *移位的位数不要用负数

#### 位运算例子

##### 输出一个数的二进制

![image-20200328175707259](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328175707259.png)

![image-20200328175615732](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328175615732.png)

#### 位段

- 把一个int的若干为组合成一个结构

    ```c
    struct {
        unsigned int leading : 3; // 占3个比特
        unsigned int FLAG1 : 1; // 占1个比特
        unsigned int FLAG2 : 1; // 占1个比特
        int trailing : 27; // 占27个比特
    };
    ```

    ![image-20200328195509987](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328195509987.png)

- 可以直接用位段成员的名称来访问

    - 比移位、与、或要方便

- 编译器会安排其中的位的排列，不具有可移植性

- 当所需的位超过一个int是，会采用多个int来存放数据

### 14.1  *可变数组（Resizable Array）

#### the Interface

##### array.h

```c
#ifndef _ARRAY_H_
#define _ARRAY_H_

typedef struct {
    int *array;
    int size;
} Array;

Array array_create(int init_size); // 创建一个数组

void array_free(Array *a);    // 回收数组空间

int array_size(const Array *a);    // 数组里目前有多少单元可以用

int *array_at(Array *a, int index);// 访问数组里下标为index的单元并返回指向index的指针

void array_set( const Array *a, int index, int value);  // 在index处写入value
int array_get(Array *a, int index); // 获得index处的值

void array_inflate(Array *a, int more_size);    // 让数组变大
#endif /* _ARRAY_H_ */
```

##### array.c

```c
#include <stdio.h>
#include <stdlib.h>
#include "array.h"

// 定义一个增长块Block
const int BLOCK_SIZE = 5;

// 创建一个数组
Array array_create(int init_size) {
    Array a;
    a.size = init_size;
    a.array = (int *)malloc(sizeof(int) * a.size);
    return a;
}

// 回收数组空间
// 传入的是指向结构体变量的指针
void array_free(Array *a) {
    free(a->array);
    a->array = NULL;
    a->size = 0;
}

// 数组里目前有多少单元可以用
// 封装，将a->size保护起来了
int array_size(const Array *a) {
    return a->size;
}

// 访问数组里下标为index的单元，并返回指向index的指针
int *array_at(Array *a, int index) {
    // 写数据时，若size溢出，自动增长
    if (index >= a->size) {
        // 找到下一个Block，计算出需要增加的个数more_size
        array_inflate(a, (index / BLOCK_SIZE + 1) * BLOCK_SIZE - a->size);
    }
    return &(a->array[index]); // 返回所在位置的指针
}

// 在index处写入value
void array_set( const Array *a, int index, int value) {
    a->array[index]  = value;
}

// 获得index处的值
int array_get(Array *a, int index) {
    return a->array[index];
}

// 让数组变大
void array_inflate(Array *a, int more_size) {
    int *p = (int *)malloc(sizeof(int) * (a->size + more_size));
    for (int i = 0; i < a->size; i++) {
        p[i] = a->array[i];
    }
    free(a->array);
    a->array = p;
    a->size += more_size;
}
```

##### main.c

```c
#include <stdio.h>
#include "array.h"

int main(int argc, const char * argv[]) {
    Array a = array_create(100);
    printf("size of a = %d\n", array_size(&a));
    
    // 一种访问可变数组a中单元的方法
    array_set(&a, 0, 10);
    printf("value of a->array[0] = %d\n", array_get(&a, 0));
    
    // 另一种访问可变数组a中单元的方法
    *array_at(&a, 1) = 20;
    printf("value of a->array[1] = %d\n", *array_at(&a, 1));
    
    array_free(&a);
    
    return 0;
}
```

- `array_at`返回的指针可以用来向index处赋值和取值

- `array_set`是用来向index处赋值的

- `array_get`是用来在index处取值的

- 他们俩合起来可以实现`array_at`的功能

    ![image-20200328215754737](/Users/kungfu/Desktop/MOOC_C程序设计笔记/images/image-20200328215754737.png)

#### 可变数组的缺陷

- it takes time to copy
- it may fail in memory restricted situation ，即可能在有足够内存的情况下无法申请内存

### 14.2 *链表

#### node.h

```c
#ifndef node_h
#define node_h

typedef struct _node {
    int value;
    struct _node *next; // 此时不可以写成Node *next
                        // 因为此时编译器还不知道Node是什么
}Node;

#endif /* node_h */
```

#### main.c

```c
#include <stdio.h>
#include <stdlib.h>
#include "node.h"

// 头结点
typedef struct _list {
    Node *head;
} List;

void add(List *pList, int number);
void print(List *pList);
void find(List *pList, int number);
void delete(List *pList, int number);

int main(int argc, const char * argv[]) {
    List list;
    list.head = NULL;
    int number;
    do {
        scanf("%d", &number);
        if (number != -1) {
            add(&list, number);
        }
    } while (number != -1);
    
    // 遍历输出链表
    print(&list);
    
    // 查找
    find(&list, number);
    
    // 删除
    delete(&list, number);
    
    // free整个链表
    Node *p;
    Node *q = NULL;
    for (p = list.head; p; p = q) {
        q = p->next;
        free(p);
    }
    
    return 0;
}

void add(List *pList, int number) {
    // 申请一个结点存放需要放入的数据
    Node *p = (Node *)malloc(sizeof(Node));
    p->value = number;
    p->next = NULL;
    // 找到最后一个结点
    Node *last = pList->head;
    if (last != NULL) {
        while (last->next != NULL) {
            last = last->next;
        }
        // attach
        last->next = p;
    } else {
        // attach
        pList->head = p;
    }
}

// 输出整个链表
void print(List *pList) {
    Node *p;
       for (p = pList->head; p; p = p->next) {
           printf("%d\t", p->value);
       }
       printf("\n");
}

// 在链表中查找number
void find(List *pList, int number) {
    scanf("%d", &number);
    Node *p;
    int isFound = 0;
    for (p = pList->head; p; p = p->next) {
        if (p->value == number) {
            printf("找到了\n");
            isFound = 1;
            break;
        }
    }
    if (!isFound) {
        printf("没找到\n");
    }
}

// 在链表中删除number
void delete(List *pList, int number) {
    Node *q;
    Node *p;
    for ( q = NULL,p = pList->head; p; q = p, p = p->next) {
        if (p->value == number) {
            if (q) {
                q->next = p->next;
            } else {
                pList->head = p->next; // 删第一个节点，此时q==NULL
            }
            free(p);
            break;
        }
    }
}
```



