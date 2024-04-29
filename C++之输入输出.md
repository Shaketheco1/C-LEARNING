# 1. 格式化输出(#include<iomanip>)

* A. 操作符

  ​	1. setw();

```C++
setw(int)     //**指定域宽**
//注意仅对当前相邻的一个输出项有效,输出完毕则返回默认域宽
//such as
float a=9.2;
cout<<"("<<setw(5)<<a<<")"<<endl;
将输出:
(  9.2)//前面两个空格
```

特性:

> * **浮点数的数域包括小数点所占的位置**
> * **数值的输出默认为右对齐,即数据在右,括号填充在左**
> * 字符串中的空格也属于有效字符,且占域宽
> * **setw**() 域宽超出,不会截断数据

​	2.setprecision()

```c++
setprecision(int)     //**设置精度**
//在重新设置前,setprecision都有效
//such as
a=28.92786;
b=21;
c=109.55;
cout<<setprecision(5)<<a<<endl;
cout<<b<<endl;
cout<<c<<endl;
将输出
28.928
21
109.55
```

**特性**

>* **setprecision()**  **的进位规则是"四舍五入"** 
>* **末尾是0则不输出;**
>* **数据精度比指定精度小,则setprecision失效;**
>* **重新设置前都有效**
>* 非整型数值较大则会使用科学计数法输出;

3.setiosflags()

```C++
setiosflags(int)   //格式状态控制:用来控制cout输出定点形式的浮点数;
常见状态标志位
    ios::left   //左对齐
    ios::right	//右对齐
    ios::fixed	//定点形式输出浮点数 与setprecision()配合使用;此时setprecision表示小数点后精度,默认六位
    ios::showpoint  //输出小数点和尾部的零
    多个状态位用"|"连接;
```

**特性**

>* 重新设置失效;否则一直有效;

B. 标准输入输出流函数成员

 ```C++	
 cout.width()
 cout.precision()
 cout.setf()
 //用法与上面操作符类似
 "特别地": setf状态位可以用unsetf()清除;
 ```

# 2.格式化输入

## 1. 与输出类似 //提几个区别点

	 只会读取设置的域宽宽度个字符
	 多出字符会留存在缓冲区中 

# 3.字符读取

1. 读取一个字符

   1. ```c++
      char ch;
      cin>>ch;//会略过空格，且遇到空格换行符结束，也会留结束符在缓冲区中
      ```

   2. ```C++
      char ch;
      cin.get(ch);
      //注意当此前曾经输入过换行符时;记得使用，get（）会留换行符在缓冲区中；
      "cin.getchar()";
      ```

2. 读取一行

   1. ```c++
      char string[100];
      cin.getline(string,100,"/n"); //  "/n"可省略;
      //getline会读取换行符,但不会储存,且读到换行符停止读入;也不会留在缓冲区中
      ```

