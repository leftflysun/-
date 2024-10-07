#include<iostream>
 using namespace std;

 int main() {

     //变量的定义
     //语法：数据类型  变量名 = 初始值
     
     int a = 10;
     
     cout << "a = " << a << endl;
     
     system("pause");
     
     return 0;
 }
注意：C++在创建变量时，必须给变量一个初始值，否则会报错



 //1、宏常量
 #define day 7

 int main() {

     cout << "一周里总共有 " << day << " 天" << endl;
     //day = 8;  //报错，宏常量不可以修改
     
     //2、const修饰变量
     const int month = 12;
     cout << "一年里总共有 " << month << " 个月份" << endl;
     //month = 24; //报错，常量是不可以修改的


​     
     system("pause");
     
     return 0;
 }



//加减乘除
int main() {

	int a1 = 10;
	int b1 = 3;
	
	cout << a1 + b1 << endl;
	cout << a1 - b1 << endl;
	cout << a1 * b1 << endl;
	cout << a1 / b1 << endl;  //两个整数相除结果依然是整数
	
	int a2 = 10;
	int b2 = 20;
	cout << a2 / b2 << endl; 
	
	int a3 = 10;
	int b3 = 0;
	//cout << a3 / b3 << endl; //报错，除数不可以为0


	//两个小数可以相除
	double d1 = 0.5;
	double d2 = 0.25;
	cout << d1 / d2 << endl;
	
	system("pause");
	
	return 0;
}



int main() {

	//选择结构-单行if语句
	//输入一个分数，如果分数大于600分，视为考上一本大学，并在屏幕上打印
	
	int score = 0;
	cout << "请输入一个分数：" << endl;
	cin >> score;
	
	cout << "您输入的分数为： " << score << endl;
	
	//if语句
	//注意事项，在if判断语句后面，不要加分号
	if (score > 600)
	{
		cout << "我考上了一本大学！！！" << endl;
	}
	
	system("pause");
	
	return 0;
}



//函数定义
int add(int num1, int num2) //定义中的num1,num2称为形式参数，简称形参
{
	int sum = num1 + num2;
	return sum;
}

int main() {

	int a = 10;
	int b = 10;
	//调用add函数
	int sum = add(a, b);//调用时的a，b称为实际参数，简称实参
	cout << "sum = " << sum << endl;
	
	a = 100;
	b = 100;
	
	sum = add(a, b);
	cout << "sum = " << sum << endl;
	
	system("pause");
	
	return 0;
}



//函数常见样式
//1、 无参无返
void test01()
{
	//void a = 10; //无类型不可以创建变量,原因无法分配内存
	cout << "this is test01" << endl;
	//test01(); 函数调用
}

//2、 有参无返
void test02(int a)
{
	cout << "this is test02" << endl;
	cout << "a = " << a << endl;
}

//3、无参有返
int test03()
{
	cout << "this is test03 " << endl;
	return 10;
}

//4、有参有返
int test04(int a, int b)
{
	cout << "this is test04 " << endl;
	int sum = a + b;
	return sum;
}

 函数的分文件编写
作用：让代码结构更加清晰

函数分文件编写一般有4个步骤

创建后缀名为.h的头文件

创建后缀名为.cpp的源文件

在头文件中写函数的声明

在源文件中写函数的定义

示例：

//swap.h文件
#include<iostream>
using namespace std;

//实现两个数字交换的函数声明
void swap(int a, int b);
//swap.cpp文件
#include "swap.h"

void swap(int a, int b)
{
	int temp = a;
	a = b;
	b = temp;

	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
}
//main函数文件
#include "swap.h"
int main() {

	int a = 100;
	int b = 200;
	swap(a, b);
	
	system("pause");
	
	return 0;
}



指针的作用： 可以通过指针间接访问内存

内存编号是从0开始记录的，一般用十六进制数字表示



可以利用指针变量保存地址

指针变量的定义和使用
指针变量定义语法： 数据类型 * 变量名；

示例：

int main() {

	//1、指针的定义
	int a = 10; //定义整型变量a
	
	//指针定义语法： 数据类型 * 变量名 ;
	int * p;
	
	//指针变量赋值
	p = &a; //指针指向变量a的地址
	cout << &a << endl; //打印数据a的地址
	cout << p << endl;  //打印指针变量p
	
	//2、指针的使用
	//通过*操作指针变量指向的内存
	cout << "*p = " << *p << endl;
	
	system("pause");
	
	return 0;
}
指针变量和普通变量的区别

普通变量存放的是数据,指针变量存放的是地址

指针变量可以通过" * "操作符，操作指针变量指向的内存空间，这个过程称为解引用

总结1： 我们可以通过 & 符号 获取变量的地址

总结2：利用指针可以记录地址

总结3：对指针变量解引用，可以操作指针指向的内存

指针所占内存空间
提问：指针也是种数据类型，那么这种数据类型占用多少内存空间？

示例：

int main() {

	int a = 10;
	
	int * p;
	p = &a; //指针指向数据a的地址
	
	cout << *p << endl; //* 解引用
	cout << sizeof(p) << endl;
	cout << sizeof(char *) << endl;
	cout << sizeof(float *) << endl;
	cout << sizeof(double *) << endl;
	
	system("pause");
	
	return 0;
}
总结：所有指针类型在32位操作系统下是4个字节





空指针和野指针
空指针：指针变量指向内存中编号为0的空间

用途：初始化指针变量

注意：空指针指向的内存是不可以访问的

示例1：空指针

int main() {

	//指针变量p指向内存地址编号为0的空间
	int * p = NULL;
	
	//访问空指针报错 
	//内存编号0 ~255为系统占用内存，不允许用户访问
	cout << *p << endl;
	
	system("pause");
	
	return 0;
}
野指针：指针变量指向非法的内存空间

示例2：野指针

int main() {

	//指针变量p指向内存地址编号为0x1100的空间
	int * p = (int *)0x1100;
	
	//访问野指针报错 
	cout << *p << endl;
	
	system("pause");
	
	return 0;
}
总结：空指针和野指针都不是我们申请的空间，因此不要访问。



const修饰指针
const修饰指针有三种情况

const修饰指针 --- 常量指针

const修饰常量 --- 指针常量

const即修饰指针，又修饰常量

示例：

int main() {

	int a = 10;
	int b = 10;
	
	//const修饰的是指针，指针指向可以改，指针指向的值不可以更改
	const int * p1 = &a; 
	p1 = &b; //正确
	//*p1 = 100;  报错


	//const修饰的是常量，指针指向不可以改，指针指向的值可以更改
	int * const p2 = &a;
	//p2 = &b; //错误
	*p2 = 100; //正确
	
	//const既修饰指针又修饰常量
	const int * const p3 = &a;
	//p3 = &b; //错误
	//*p3 = 100; //错误
	
	system("pause");
	
	return 0;
}
技巧：看const右侧紧跟着的是指针还是常量, 是指针就是常量指针，是常量就是指针常量



指针和数组
作用：利用指针访问数组中元素

示例：

int main() {

	int arr[] = { 1,2,3,4,5,6,7,8,9,10 };
	
	int * p = arr;  //指向数组的指针
	
	cout << "第一个元素： " << arr[0] << endl;
	cout << "指针访问第一个元素： " << *p << endl;
	
	for (int i = 0; i < 10; i++)
	{
		//利用指针遍历数组
		cout << *p << endl;
		p++;
	}
	
	system("pause");
	
	return 0;
}



指针和函数
作用：利用指针作函数参数，可以修改实参的值

示例：

//值传递
void swap1(int a ,int b)
{
	int temp = a;
	a = b; 
	b = temp;
}
//地址传递
void swap2(int * p1, int *p2)
{
	int temp = *p1;
	*p1 = *p2;
	*p2 = temp;
}

int main() {

	int a = 10;
	int b = 20;
	swap1(a, b); // 值传递不会改变实参
	
	swap2(&a, &b); //地址传递会改变实参
	
	cout << "a = " << a << endl;
	
	cout << "b = " << b << endl;
	
	system("pause");
	
	return 0;
}
总结：如果不想修改实参，就用值传递，如果想修改实参，就用地址传递





指针、数组、函数
案例描述：封装一个函数，利用冒泡排序，实现对整型数组的升序排序

例如数组：int arr[10] = { 4,3,6,9,1,2,10,8,7,5 };

示例：

//冒泡排序函数
void bubbleSort(int * arr, int len)  //int * arr 也可以写为int arr[]
{
	for (int i = 0; i < len - 1; i++)
	{
		for (int j = 0; j < len - 1 - i; j++)
		{
			if (arr[j] > arr[j + 1])
			{
				int temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}
}

//打印数组函数
void printArray(int arr[], int len)
{
	for (int i = 0; i < len; i++)
	{
		cout << arr[i] << endl;
	}
}

int main() {

	int arr[10] = { 4,3,6,9,1,2,10,8,7,5 };
	int len = sizeof(arr) / sizeof(int);
	
	bubbleSort(arr, len);
	
	printArray(arr, len);
	
	system("pause");
	
	return 0;
}
总结：当数组名传入到函数作为参数时，被退化为指向首元素的指针





结构体基本概念
结构体属于用户==自定义的数据类型==，允许用户存储不同的数据类型



结构体定义和使用
语法：struct 结构体名 { 结构体成员列表 }；

通过结构体创建变量的方式有三种：
struct 结构体名 变量名

struct 结构体名 变量名 = { 成员1值 ， 成员2值...}

定义结构体时顺便创建变量

示例：

//结构体定义
struct student
{
	//成员列表
	string name;  //姓名
	int age;      //年龄
	int score;    //分数
}stu3; //结构体变量创建方式3 


int main() {

	//结构体变量创建方式1
	struct student stu1; //struct 关键字可以省略
	
	stu1.name = "张三";
	stu1.age = 18;
	stu1.score = 100;
	
	cout << "姓名：" << stu1.name << " 年龄：" << stu1.age  << " 分数：" << stu1.score << endl;
	
	//结构体变量创建方式2
	struct student stu2 = { "李四",19,60 };
	
	cout << "姓名：" << stu2.name << " 年龄：" << stu2.age  << " 分数：" << stu2.score << endl;


	stu3.name = "王五";
	stu3.age = 18;
	stu3.score = 80;


	cout << "姓名：" << stu3.name << " 年龄：" << stu3.age  << " 分数：" << stu3.score << endl;
	
	system("pause");
	
	return 0;
}
总结1：定义结构体时的关键字是struct，不可省略

总结2：创建结构体变量时，关键字struct可以省略

总结3：结构体变量利用操作符 ''.'' 访问成员



结构体数组
作用：将自定义的结构体放入到数组中方便维护

语法：struct 结构体名 数组名[元素个数] = { {} , {} , ... {} }

示例：

//结构体定义
struct student
{
	//成员列表
	string name;  //姓名
	int age;      //年龄
	int score;    //分数
}

int main() {
	
	//结构体数组
	struct student arr[3]=
	{
		{"张三",18,80 },
		{"李四",19,60 },
		{"王五",20,70 }
	};
	
	for (int i = 0; i < 3; i++)
	{
		cout << "姓名：" << arr[i].name << " 年龄：" << arr[i].age << " 分数：" << arr[i].score << endl;
	}
	
	system("pause");
	
	return 0;
}



结构体指针
作用：通过指针访问结构体中的成员

利用操作符 ->可以通过结构体指针访问结构体属性

示例：

//结构体定义
struct student
{
	//成员列表
	string name;  //姓名
	int age;      //年龄
	int score;    //分数
};


int main() {
	
	struct student stu = { "张三",18,100, };
	
	struct student * p = &stu;
	
	p->score = 80; //指针通过 -> 操作符可以访问成员
	
	cout << "姓名：" << p->name << " 年龄：" << p->age << " 分数：" << p->score << endl;
	
	system("pause");
	
	return 0;
}
总结：结构体指针可以通过 -> 操作符 来访问结构体中的成员

8.5 结构体嵌套结构体
作用： 结构体中的成员可以是另一个结构体

例如：每个老师辅导一个学员，一个老师的结构体中，记录一个学生的结构体

示例：

//学生结构体定义
struct student
{
	//成员列表
	string name;  //姓名
	int age;      //年龄
	int score;    //分数
};

//教师结构体定义
struct teacher
{
    //成员列表
	int id; //职工编号
	string name;  //教师姓名
	int age;   //教师年龄
	struct student stu; //子结构体 学生
};


int main() {

	struct teacher t1;
	t1.id = 10000;
	t1.name = "老王";
	t1.age = 40;
	
	t1.stu.name = "张三";
	t1.stu.age = 18;
	t1.stu.score = 100;
	
	cout << "教师 职工编号： " << t1.id << " 姓名： " << t1.name << " 年龄： " << t1.age << endl;
	
	cout << "辅导学员 姓名： " << t1.stu.name << " 年龄：" << t1.stu.age << " 考试分数： " << t1.stu.score << endl;
	
	system("pause");
	
	return 0;
}
总结：在结构体中可以定义另一个结构体作为成员，用来解决实际问题



结构体做函数参数
作用：将结构体作为参数向函数中传递

传递方式有两种：

值传递

地址传递

示例：

//学生结构体定义
struct student
{
	//成员列表
	string name;  //姓名
	int age;      //年龄
	int score;    //分数
};

//值传递
void printStudent(student stu )
{
	stu.age = 28;
	cout << "子函数中 姓名：" << stu.name << " 年龄： " << stu.age  << " 分数：" << stu.score << endl;
}

//地址传递
void printStudent2(student *stu)
{
	stu->age = 28;
	cout << "子函数中 姓名：" << stu->name << " 年龄： " << stu->age  << " 分数：" << stu->score << endl;
}

int main() {

	student stu = { "张三",18,100};
	//值传递
	printStudent(stu);
	cout << "主函数中 姓名：" << stu.name << " 年龄： " << stu.age << " 分数：" << stu.score << endl;
	
	cout << endl;
	
	//地址传递
	printStudent2(&stu);
	cout << "主函数中 姓名：" << stu.name << " 年龄： " << stu.age  << " 分数：" << stu.score << endl;
	
	system("pause");
	
	return 0;
}
总结：如果不想修改主函数中的数据，用值传递，反之用地址传递



结构体中 const使用场景
作用：用const来防止误操作

示例：

//学生结构体定义
struct student
{
	//成员列表
	string name;  //姓名
	int age;      //年龄
	int score;    //分数
};

//const使用场景
void printStudent(const student *stu) //加const防止函数体中的误操作
{
	//stu->age = 100; //操作失败，因为加了const修饰
	cout << "姓名：" << stu->name << " 年龄：" << stu->age << " 分数：" << stu->score << endl;

}

int main() {

	student stu = { "张三",18,100 };
	
	printStudent(&stu);
	
	system("pause");
	
	return 0;
}

