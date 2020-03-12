## 1. 基本数据类型

aaa

## 2. 表达式

aaa

## 3. 语句

aaa

## 4. 函数

aaa

## 5. 类

aaa

## 6. 容器

aaa

## 7. IO操作

### 7.1. 文件操作

```
#include <fstream>
```
打开或创建文本
```
string file_path = "../data/filename.txt";
fstream text_file;
text_file.open(file_path, ios::out); //打开文件并清空内容
text_file.open(file_path, ios::out | ios::app);//打开文件，并保留文件原有内容，定位到文件末尾
```
- ios::in读
- ios::out写
- ios::app每次写操作前，定位到文件末尾
- ios::ate打开文件时，定位到文件末尾
- ios::trunc清空内容

打开或创建带序号文本
```
int i = 1;
char file_path[50];
sprintf(file_path, "../data/file%d.txt", i);
fstream text_file;
text_file.open(file_path, ios::out);
```
遍历读取文本信息

方法一

按词读取
```
string str;
while (text_file >> str)
{
    cout << str << endl;
}
```
按行读取
```
string str;
while(getline(text_file, str))
{
    cout << str << endl;
}
```
方法二

按词读取
```
string str;
while (!text_file.eof())
{
    text_file >> str;
}
```
按行读取
```
string str;
while (!text_file.eof())
{
    getline(text_file, str);
    cout << str;
}
```
向文本写入信息
```
string str1 = “hello”;
string str2 = “world”;
text_file << str1 << “ ”<< str2 << endl;
```
关闭文本
```
text_file.close();
```

## 8. 异常处理

aaa

## 9.日志

aaa

## 10. 内存管理

aaa

## 11. 并发

aaa

## 12. 泛型

aaa

## 13. 重载

aaa

## 14. 模板

aaa

## 15. 编程规范

子程序一般情况下代码长度不宜超过200行

### 15.1. 命名规则

- 文件：全部小写，中间以下划线连接file_name.cpp
- 函数：每个单词首字母大写FunctionName ()
- 类：首字母大写ClassName
- 枚举类型：首字母大写EnumeratorTypes
- 局部变量：全部小写，以下划线连接local_variable_name
- 类的成员变量：全部小写，以下划线连接，以下划线结尾 class_variable_name_
- 结构体的成员变量：全部小写，以下划线连接struct_variable_name
- 全局变量：g_做前缀，全部小写，以下划线连接g_global_variable_name
- 常量：k做前缀，首字母大写kConstantName
- 宏：全部大写，以下划线连接MACRO_TYPE
- 名字空间：全部小写，以下划线连接namespace_names

### 15.2. #include头文件引用顺序

1. 自身.cpp文件的.h文件
2. 系统.h文件
3. 本项目内其他自定义的.h文件

## 16. 随记

### 16.1. 打印时间

```
auto now = std::chrono::system_clock::now();
std::time_t t = std::chrono::system_clock::to_time_t(now);
std::cout << std::put_time(std::localtime(&t), "%Y-%m-%d %H:%M:%S") << " ";
```