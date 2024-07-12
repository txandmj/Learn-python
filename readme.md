[函数的传参机制：](###函数的传参机制：)

### 整型
整型能最大到4300位，比Java，C语言的整型最大数大很多

在编程中，存贮数据的基本单位是字节（byte）1 byte = 8 bit

- 字节数随着数字增大而增大（Java是不变的，整型占4个字节）

- 每次增量为4个字节
### Bool类型：大写True, False
- Bool类型可以和其他数据进行比较，比如数字，字符串等。在比较时，python会将True视为1，False视为0.

- 在python中，非0被视为真值，0值被视为假值
### Str类型
使用引号（‘ 或者“）包起来，创建字符串
- Str就是string的缩写，在使用type()查看数据类型时，字符串类型显示的是str

- 通过+号可以进行字符拼接,一定是字符串的拼接，不可以int + str，这种情况需要数据转换

- 不支持单字符类型，单字符也是作为字符串使用。‘a’ = “a” 是字符串

- 用3个单引号'''内容'''或者双引号"""内容"""可以使字符串内容保持原样输出，比如输出一段代码

- 在字符串前面加r可以使整个字符串不被转义。eg print(r"jack\ntom\tjon") 转义符失效 输出：jack\ntom\tjon

## 字符串驻留机制：

Python仅保存一份相同且不可变字符串，不同的值被存放在字符串的驻留池中，python的驻留机制对相同的字符串只保留一份拷贝，后续创建相同字符串时，不会开辟新空间，而是把该字符串的地址赋给新创建的变量

驻留机制几种情况讨论：
-	字符串是由26个英文字母大小写，0~9， _组成
-	字符串长度为0或者1时
-	字符串在编译时进行驻留，而非运行时
-	[-5，256]的整数数字

```
a = “abc123_”, b=“abc123_” -> id(a) = id(b)
a = “abc123#”, b=“abc123#” -> id(a) != id(b) 因为有#
a = “”, b=“” -> id(a) = id(b)
a= “#’, b=”#” -> id(a) = id(b)
a = “-5”, b=“-5” -> id(a) = id(b)
a= “2257’, b=”2257” -> id(a) != id(b)
```

但是pycharm对其进行了优化导致a = “abc123#”, b=“abc123#” id(a) = id(b)

好处：当需要值相同的字符串时，可以直接从字符串池里拿来使用，避免频繁的创建和销毁，提升效率和节约内存
## 类型转换
### 隐式类型转换
1.	python变量的类型不是固定的，会根据变量当前值在运行时决定的，可以通过内置函数type()查看
2.	在运算时，数据类型会自动向高精度转换，float的精度高于int
### 显示类型转换
1.	如果需要对变量数据类型进行转换，只需要将数据类型作为函数名即可，这种方式就是显示转换/强制转换
2.	int(x), float(x),str(x)
3.	不管什么值的int, float都可以转换成str, str(x)将对象x转换为字符串
4.	int -> float，会增加小数部分；反之，去除小数部分
5.	str -> int / float 使用int(x),float(x),在将str类型转成基本数据类型时，要确保str值能够转成有效的数据，比如我们可以把“1234”转成一个整数，但是不能把“hi”转成一个整数。
6. i = 11.0 print(int(i)) print(type(i)) type of i is float

## 运算符
优先级：算数运算（(), **, *, @, /, //, %, +, -）> 位运算(>>, <<, &, ^, |) > 比较运算(is, is not, in, not in, <, <=, >, >=, !=, ==) > 逻辑运算(not x, and, or) > 赋值运算
## 标识符
1.必须以字母大小写，0-9，_组成
2. 数字不可开头
3. 不可以使用关键字，但可以包含关键字
4. 区分大小写，不能包含空格

**规范：**
1.	变量要小写，若有多个单词，使用下划线分开，常量（eg.PI）全部大写
2.	函数名一律小写，若有多个单词，使用下划线分开。另外，私有函数以双下划线开头
3.	类名，使用大驼峰命名，首字母都大写

## 算术运算符
1.	/: 返回结果是小数
2.	//: 返回是商的整数部分，向下取整 9//2=4，-9//2=-5
3.	%: 对应公式 a % b = a - a // b * b, 
```chatinput
-10 % 3 = -10 -(-10) # 3 * 3 = -10 + 4 * 3 = 2
10 % (-3) = -2
-10 % (-3) = -1
``` 
4. **: 阶乘
## 逻辑运算符（整数0为False, 非0值为True）
1.	And (x and y) 与：如果x为False,返回x(此时，不进行y运算),否则返回y. eg a = 10, b = 20, a and b -> 20
2.	Or (x or y) 或：如果x为True,返回x(此时，不进行y运算)，否则返回y. eg a = 10, b = 20, a or b x and y 10
3.	Not (not x) 非：如果x为True，返回False。如果x为False，返回True. Not(a and b) -> False
## 赋值运算符
Python特殊语法，两变量交换 x,y = y,x

## 原码反码补码
1.	二进制的最高位是符号位：0：正数；1：负数
2.	正数三码合一
3.	负数的反码=原码符号位不变，其他位取反
4.	负数的补码=它的反码+1，负数的补码=补码-1
5.	0的反码，补码都是0
6.	计算机在运算的时候，是以补码的方式运算的
7.	看运算结果的时候，要看原码

## 位运算
1.	~ 按位取反：即1变0，0变1. 记得“计算机在运算的时候，是以补码的方式运算的，看运算结果要看原码"
2.	& 按位与：参与运算的两个值，如果两个相应位都为1，则该位为1，否则为0
3.	^按位异或：当两对应的二进位相异时，结果为1
4.	|按位或：只要对应的二个二进位有一个为1，结果位就为1

## For循环： 
```python
for <变量> in <范围/序列>： 
    <循环操作语句>
```

内置函数range(start, stop, step) 
start default vale is 0, step default value is 1. (左闭右开)

range(10) 等价于[0,1,2…9] 

range(1, 9, 2) print result->1,3,5,7

**For循环还可以配合else使用**

语法格式： 
```python
for <variable> in <sequence> :
      <statements>
else:
    <statements>
```

当for循环正常完成遍历后，就会进入else。如果for循环被打断，如break，则不执行else
## while 循环
```python
while condition:
      statements
else: （同for循环使用规则）
    statements
```
## 函数
**函数注意事项和使用细节：**
1.	同一个文件，允许两个函数名相同的函数，以就近原则进行调用。即使两个同名函数，一个有形参，一个无形参，调用函数时传入实参，也是依据就近原则，而不是根据有无参数传入，来选择函数的调用
2.	调用函数时，根据函数定义的参数位置来传递参数，这种传参方式就是位置参数，传递的实参和定义的形参顺序和个数必须一致，同时定义的形参，不需要指定数据类型，会根据传入的实参决定
3.	函数可以有多个返回值，eg return n1 + n2, n1 - n2
4.	函数支持关键字参数，即：函数调用时，可以通过“形参名=实参值”形式传递参数，这样可以不受参数传递顺序的限制
def book_info(name, price, author, amount):
```python
      def book_info(name, price, author= "cao", amount = 1000):
          print(f"name->{name} price->{price} author->{author} amount -> {amount}")
      book_info("hongloumeng", 60, amount = 30000, author = "caoxueqin")
```
   
5.	函数支持默认参数/缺省参数。定义函数时，可以给参数提供默认值，调用函数时，指定了实参，则以指定为准，没有指定参数，则以默认值为准。默认参数，需要放在参数列表后。
```python
def book_info2(name = '<English>', price = 66.8, author = 'Lily', amount = 800) :
	print(f"name->{name} price->{price} author->{author} amount -> {amount}")
book_info2() #输出默认值
book_info2('<study python>') #name替换成《study python》
def book_info3(name, price, author = 'Lily', amount = 800): #默认参数author,amount必须放在参数列表后面
	print(f"name->{name} price->{price} author->{author} amount -> {amount}")
book_info3('python', 999) #python赋给name, 999赋给price

```
6.	函数支持可变参数/不定长参数，应用场景：当调用函数时，不确定传入多少个实参的情况（*args）。传入的多个实参，会被组成一个元组（tuple），元组可以储存多个数据项
```python
def sum(*args):
	print(f"args -> {args} type -> {type(args)}") # type: tuple
	total = 0
	for ele in args:
		total =+ ele
	return total
```
7.	函数的可变参数/不定长参数，还支持多个关键词参数，也就是多个“形参名 = 实参值”。传入多个关键字参数，会被组成一个字典（dict），字典可以储存多个”键=值”
8.	Python调用另一个.py文件。Import f1
### 函数的传参机制：
- **数值和字符串的传参机制：** 字符串和数值类型是不可变数据类型，当对应的变量的值发生了变化时，它对应的内存地址会发生改变

- **函数作为参数传递：** 
  1.	函数作为参数传递，传递的不是数据，而是业务处理逻辑
  2.	一个函数，可以接收多个函数作为参数传入
  
### Lambda匿名函数：
  如果我们有这样一个需求，需要将函数作为参数进行传递，但是这个函数只使用一次，这时，我们可以考虑使用lambda函数
1.	函数的定义：
- def关键字，可以定义带有名称的函数，可以重复使用
- lambda关键字，可以定义匿名函数（无名称），匿名函数只能使用一次
- 匿名函数用于临时创建一个函数，只使用一次的场景
2.	匿名函数基本语法:

- lambda形参列表：函数体（一行代码）
- lambda关键字，表示定义匿名函数
- 形参列表：比如num1, num2表示接收两个参数,这时候形参列表不能用（）
- 函数体：完成的功能，只能写一行，不能写多行代码
```python
#编写一个函数，接收一个匿名函数和两个数，通过匿名函数计算，返回两个值的最大值
def f1(fun, num1, num2):
	return fun(num1, num2)
#匿名函数，不需要return，运算结果就是返回值
max_val = f1(lambda a, b: a if a > b else b, 12, 10) #f1(fun, num1, num2)
print(max_val)

```

### 全局变量和局部变量
1.	未在函数内部重新定义n1,那么默认使用全局变量n1
2.	在函数内部重新定义了n1，那么根据就近原则，使用的就是函数内部重新定义的n1，但不改变函数外部的n1
3.	在函数内部使用global关键字，可以标明指定使用全局变量，这时n1会发生变化（应用场景，作为计数器）
## 数据容器：列表，元组，字符串，set, direct
### 列表：列表[下标]
- 列表长度：len(list, tuple, bytes, str, set, direct)
- 创建空列表：list1 = [] or list2 = list()
- 列表的元素可以有多个，而且数据类型没有限制（数字，字符串，甚至嵌套列表），允许有重复元素，并且是有序的
- Index也可以从尾部开始，最后一个元素的索引为-1，往前一位为-2，以此类推
- 通过 列表[index] = 新值 对数据进行更新，使用 列表.append(value) 来添加元素， del 列表[index] 删除元素 
```python
list_a = [100, 200, 300, 400, 600]
print(len(list_a)) #5
print(max(list_a)) #600
print(min(list_a)) #100
list_a.append(900) 
print(list_a) #[100, 200, 300, 400, 600, 900]
print(list_a.count(100)) #1
list_b = [1, 2, 3]
list_a.extend(list_b) #[100, 200, 300, 400, 600, 900, 1, 2, 3]
print(list_a)
print(list_a.index(300)) #2
list_a.reverse() #[3, 2, 1, 900, 600, 400, 300, 200, 100]
print(list_a)
list_a.insert(1, 666) #[3, 666, 2, 1, 900, 600, 400, 300, 200, 100]
print(list_a)
list_c = [ele * ele for ele in range(1, 11)]
print(list_c) #[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

i = 0
list_a = list()
while i < 5:
    list_a.append(float(input()))
    i = i + 1
print(list_a) #[22.0, 15.0, 2.0, 4.0, 5.0]
```
**列表是可变序列** 列表的元素是可以修改的，修改后，列表变量指向地址不变，只是数据内容变化。
**注意** _**数值和字符串是不可变数据类型，所以它们的赋值逻辑不一样。**_
```python
a = 100
b = a
b = 0 
print(a) #a = 100. a是不变的，b指向0的地址。但是list就不同，会发生变化
```
**列表生成式：[列表元素的表达式 for 自定义变量 in 可迭代对象]**
```python
print([ele * 2 for ele in range(1, 5)]) #[2,4,6,8]
```

### 元组（tuple）可以存放多个不同类型数据，元组是不可变序列
- tuple不可变是指当你创建了tuple时候，它就不能改变了，也就是说它也没有append(), insert()这样的方法，但它也有获取某个索引值的方法，但是不能重新赋值
- 定义：创建一个元组，只要把逗号分隔的不同的数据项，使用圆括号括起来即可
- 使用：元组名[index]
- 元组的遍历： while, for

**使用细节：**

+ 	空元组，tuple_a = () or tuple_a = tuple();
- 元组的元素可以有多个，而且数据类型没有限制 （整型，str, float, tuple）
- 元组index 也是从0开始，必须在指定范围内使用，不能越界
- 可以修改元组内list的内容（包括修改，增加，删除等）

```python
Tuple_a = (2, "jack", [1,2,3])
print(tuple_a[2]) #[1,2,3]
print(tuple_a[2][0]) #1
Tuple_a[2][0] = "hello" #改list，list是可变序列
Tuple_a[2] = [22,33] #错，元组不可改
del tuple_a[2][1] #[1,3]
Tuple_a[2].append("hi") #list添加元素
```

- Index也可以从尾部开始，最后一个元素的索引为-1
- 定义只有一个元素的元组，需要带上逗号 tuple_h = (100,) 如不带逗号，type 是int
- Tuple 比list的好处：在项目中，尤其是多线程环境中，有经验的程序员会考虑使用不变对象（一方面因为对象状态不能修改，所以可以避免由此引起的不必要的程序错误；另一方面一个不变对象自动就是线程安全的，这样就可以省掉处理同步化的开销。可以方便的被共享访问）。所以，如果不需要对元素进行增删改的情况下，可以考虑元组。元组在创建时间和占用的空间上都优于列表。元组能够对不需要修改的数据写保护
### 字符串：是由Unicode码构成的不可变序列
1.	字符串字面值有三种写法： 1）单引号：‘允许包含有“双”引号‘； 2）： 双引号：“允许包含有‘双’引号”； 3）三重引号：可以跨越多行，并不改变格式
2.	字符串是字符的容器
3.	字符串遍历 while/ for, 同list, tuple
4.	字符串有效下标从0开始。尾部开始最后一个字符为-1
5.	字符串不可变序列，不可修改元素 eg. str_a[2] = “he” #错，在不改变地址时，改变str

**常用方法：**
```python
str_names = "jack tom mary hsp nono tom"
print(f"str_name include {len(str_names)} chars", end = "")
str_name_new = str_names.replace("jack", "HHH", 1)#without 1 means replace all "jack"
print(f"old name is '{str_names}', new one is '{str_name_new}'")
str_name_split = str_names.split(" ") #list
print(str_name_split) #['jack', 'tom', 'mary', 'hsp', 'nono', 'tom']
print(str_names.count("tom")) #2
print("123tom321".strip("132")) #tom
print("123t123om321".strip("123")) #t123om
print("123tom321".strip("13")) #23tom32
print("hspHSP".upper()) #HSPHSP
print("hspHSP".lower()) #hsphsp
#大写英文单词的首字母，string.capitalize() or string.title()
str_names = "tom jack mary nono smith hsp"
str_names_list = str_names.split(" ")
print(len(str_names_list))
str_names_replace = str_names.replace("hsp", "LAOHAN")
print(str_names_replace)
str_names_upper = ""
#string.capitalize() 整个字符串，只有首字母大写
for ele in str_names_list:
    if ele.isalpha():
        str_names_upper += ele.capitalize() + " " #字符串最后多了一个空格，需要删除
str_names_upper = str_names_upper.strip(" ")
print(str_names_upper)
#string.title() 所有单词首字母大写
str_names_upper2 = str_names.title()
print(str_names_upper2)
list_name = ["jack", "lisa", " hsp", "paul", "smith", "kobe"]
#切最后三个元素
list_name_slice2 = list_name[-3::] #["paul", "smith", "kobe"]
print(list_name_slice, list_name_slice2)
```
 **字符串比较：**

- 规则：首先比较两个字符串的第一个字符，如果相等则继续比较下一个字符，依次比较下去，直到两个字符串中的字符不相等时，其比较结果就是两个字符串的比较结果，后续字符不再比较
- 比较原理：比较的是其ordinal value(原始值/码值)，调用内置函数ord可以得到指定字符的ordinal value。与内置函数ord对应的是内置函数chr，调用内置函数chr时指定ordinal value可以得到其对应的字符
### 切片：从一个序列中，取出一个子序列,不影响原序列
**序列：内容连续，有序，可使用索引的一类数据容器。list, tuple, str**

**基本语法：序列[start: end: step] 左闭右开**

step:依次取出元素的间隔。step = N, 每次跳过N-1个元素. start默认为0； end默认为最后一位 ；step 默认为1。如果step为负数，则代表反向取，即从右向左 
```python
str_old = "123456"
str_new = str[-1::-1] #654321
str_new = str[-1:-6:-1] #65432 左闭右开
str_new = str[-3::] #切最后三个元素
```

### 集合：是由**不重复**元素组成的无序容器
- 集合对象支持合集(union,|)，交集(intersection, &)，差集(difference, - )等数学运算
- 定义：只要用逗号分隔的不同的数据项，用{}

**注意事项：**
- 集合取出数据是无序的，但是每次取出的顺序是不变的
- 集合不支持索引
- 既然集合不支持索引，所以对集合遍历不能使用while，只能使用for对集合进行遍历
- 创建空集合只能用set(),不能用{}。{}是创建空字典

**集合操作：** 
```python
basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
print(len(basket)) #4, 去重后的长度
print('apple' in basket) #true x in s:检测x是否为s中的成员
basket.add('grape') #添加元素add，不一定添加在尾部，是无序的
print(basket)
basket.remove('apple') #remove ele. 如果数据不存在，则会报错
ele = basket.pop() #pop() 从集合中随机移除一个元素，会影响原集合
print(basket) #移除了banana

book_1 = {'aaa', 'bbb'}
book_2 = {'111', '222', 'aaa'}
book_3 = book_1.union(book_2) #= book_3 = book_1 | book_2
print(book_3) #{'222', 'bbb', 'aaa', '111'}
book_4 = book_1.intersection(book_2) #book_4 = book_1 & book_2
print(book_4) #{'aaa'}
book_5 = book_1 - book_2 #求差值 = book_1.difference(book_2)
print(book_5) #{'bbb'}
```
**集合生成式：{集合元素的表达式 for 自定义变量 in 可迭代对象}**
```python
print({ele * 2 for ele in range(1, 5)})
```
**_集合生成式与列表生成式的区别：_**集合使用{ }，列表使用[ ] 
   
### 字典：是一种映射类型，即key-value的映射关系
- 创建一个字典，只要把逗号分隔的不同的元素，用{}括起来，存储的元素是一个个的：键值对（集合虽然也是用{}括起来，但是它存的是单元素）
dict_a = {key:value, key:value,…}. 
- 通过Key取出对应的value语法：dict_a[key]

**注意事项：**
1.	字典中的key通常是***字符串和数字***，value可以是任意数据类型
2.	字典不支持index
3.	既然字典不支持索引，所以不能用while，只支持for。三种方式：
      - 依次取出key, 再通过dict[key]取出对应的value
      - 依次取出value: for value in dict_c.values() :
      - 依次取出键值对： for k, v in dict_c.items() :
4.	创建空字典：dict_c = {} or dict_c = dict()
5.	Key必须是唯一的，如果你指定了多个相同的key, 后面的k-v会覆盖前面的

常用操作：
```python
dict_a = {'one': 1, 'two': 2, 'three': 3}
print(len(dict_a)) # 3 长度
#d[key]: 返回key对应的v
print(dict_a['three'])
#d[key] = value:赋值（key存在），添加k-v（key不存在）
dict_a['three'] = 1000
dict_a['four'] = 4
print(dict_a) #{'one': 1, 'two': 2, 'three': 1000, 'four': 4}
#delete k-v
del dict_a['four']
print(dict_a) #{'one': 1, 'two': 2, 'three': 1000}
#pop(key[, default): 如果k存在，则将其移除并返回其值，否则返回default，不存在，keyError
val = dict_a.pop('one')
print(val, "***", dict_a) #1 *** {'two': 2, 'three': 1000}
val2 = dict_a.pop('two~','hhhhhh')#k不存在，将hhhhh赋给key当默认值
print(val2, "***", dict_a) #hhhhhh *** {'two': 2, 'three': 1000}
#keys():返回所有的keys
print(dict_a.keys())
# key int d:判断字典中是否有key
print('two' in dict_a) #True
#d.clear()清空字典
```
**字典生成式：zip()**

{Key的表达式：value的表达式 for 表示key的变量，表示value的变量 in zip(可迭代对象，可迭代对象)}
```python
english_list = ['red', 'yellow', 'black']
chinese_list = ['红','黄','黑']
dict_b = {ele1: ele2.upper() for ele1, ele2 in zip(chinese_list, english_list)}
print(dict_b) #{'红': 'RED', '黄': 'YELLOW', '黑': 'BLACK'}
#employee info
employee = {"0001" : {"name" : "Jack", "age" : 22, "entry_time" : "2022-2-3", "salary" : 10000},
            "0002" : {"name" : "Nancy", "age" : 32, "entry_time" : "2018-7-3", "salary" : 20000},
            "0003" : {"name" : "Jack", "age" : 22, "entry_time" : "2022-2-3", "salary" : 10000}}
print(f"0001 employee name: {employee['0001']['name']}")
employee['0004'] = {"name" : "HAN", "age" : 42, "entry_time" : "2024-2-3", "salary" : 50000}
print(employee)
del employee['0001']
print(employee)
for key in employee.keys():#所有员工薪水增加20%
    employee[key]['salary'] += employee[key]['salary'] * 0.2
print(employee)
#遍历员工信息
for k,v in employee.items():
    print(f"employee {k}' info: name is {v['name']}, age is {v['age']}, "
          f"entry time is {v['entry_time']}, salary is {v['salary']}")
```

### Python传参机制
1.	python数据类型主要有int/float/str/bool/list/tuple/set/dict, 数据类型分为两大类，一种是可变数据类型，一种是不可变数据类型
2.	可变数据类型：当该数据类型的变量的值发生了变化，如果它的内存地址不变，那么这个数据类型就是可变数据类型。包括list, set, dict
3.	不可变数据类型：当该数据类型的变量的值发生了变化，如果它的内存地址改变了，那么这个数据类型就是不可变数据类型. str, int, bool, float, tuple

## 模块
- 模块是一个py文件，后缀名.py
- 模块可以定义函数，类和变量，模块也可能包含可执行的代码

**模块的作用**
- 当函数，类和变量很多事，可以很好的进行管理
- 开发中，程序员可以根据业务需要，把同一类型的功能代码，写道一个模块文件中，即方便管理，也方便调用
- 一个模块就是一个工具包，供程序员开发使用，提高开发效率
- python自带标准模块库，每个模块可以帮助程序员快速实现相关功能

**模块导入-基本语法**

[from 模块名] import(函数|类|变量|*) [as 别名]，[]是可选项
- 导入一个或者多个模块 -> import 模块，建议一行导入一个模块 -> 使用：模块.XX,.表示层级关系，即模块中的XX
- 导入模块的指定功能 -> from 模块 import 函数，类，变量... -> 使用：直接使用，不需要再带模块名
- 导入模块的全部功能 -> from 模块 import * -> eg. from math import * -> 使用：直接使用，不需要再带模块名
- 给导入的模块或者功能取别名 -> import 模块 as 别名 or from 模块 import 函数，类，变量... as 别名 -> 使用时，用 别名.XX or 别名

**自定义模块细节：**

- 使用__name__可以避免模块中测试代码的执行
- 使用__all__可以控制 from 模块 import * 时，哪些功能被导入，注意：import 模块，不受__all__限制(import 模块-> 霸道导入，from 模块 import -> 选择导入)

## 包
- 从结构上看，包就是一个文件夹，在该文件夹下包含了一个__init__.py文件，该文件可以用于包含多个模块文件，从逻辑上看，包可以视为模块集合
- 导入包及使用的基本语法

    导入：import 包名.模块

    使用：包名.模块.功能

**注意事项：**

- 导入包基本语法： import 包名.模块 | from 包名 import 模块
- 导入包的模块的指定功能 -> from 包名.模块 import 函数，类，变量... -> 使用：直接使用
- 导入模块的全部功能 -> from 包名.模块 import * -> eg. from hsp.module01 import * -> 使用：直接使用
- __init__.py 通过 __all__ 控制允许导入的模块 -> 在__init__.py 中增加 __all__ = [允许导入的模块列表]，注意只对from 包 import *方式生效，对import xx 方式不生效
- 包可以有多个层级 -> 包下还可以再创建包 -> 使用时，通过 .来确定层级关系
- 快捷键alt+enter（选择解决方案） | shift+alt+enter（直接导入） 可以快捷的导入
# OOP快速入门
## 类和对象的区别和联系
- 类是抽象的，概念的，代表一类事物，比如人类，猫..，即它是数据类型
- 对象是具体的，实际的，代表一个具体事物，即是实例
- 类是对象的模板，对象是类的一个个体，对应一个实例
```python
class Cat:
    name = None
    age = None
    color = None
cat1 = Cat()
cat1.name = "Lily"
cat1.age = 2
cat1.color = "white"
print(f"cat1's info: name is {cat1.name}, age is {cat1.age}, color is {cat1.color}")
```
## 属性/成员变量
**定义：类中定义的变量（属性）。属性是类的一个组成部分，一般是字符串，数值，也可以是其他类型（list, dict...）**
注意事项：
- 属性的定义语法同变量，属性名 = 值，如果没有值，可以None，是python的内置常量，通常被用来代表空值的对象
- 如果给属性指定的有值，那么创建的对象，属性就有值
## 类的定义和使用
- 基本语法： 
```
class 类名：
    field members
    methods
```
- 创建对象 -> 对象名 = 类名(), eg cat1 = Cat()
- 访问属性 -> 对象名.属性名, eg cat.name
 ## 对象的传递机制


## 对象的布尔值
Python一切皆对象，所有对象都有一个布尔值，通过内置函数bool()可以获取对象的布尔值

下面对象的布尔值为False：

1，	False

2，	0

3，	None

4，	空字符串

5，	空列表

6，	空字典

7，	空元组

8，	空集合

## 成员方法：
类除了有一些属性外，还会有一些行为，这时就要用成员方法才能完成
**基本语法：**
```commandline
def 方法名（self, 形参列表）：
	方法体
	
# 定义成员方法需要写上 self，表示当前对象本身，如果不写，要加上 @staticmethod
# 当我们通过对象调用方法时，self会隐式的传入
# 在方法内部，需要使用self，才能访问到成员变量或者成员方法, eg self.name | self.eat()
```

**注意事项：**
1.	Python支持对象动态的添加方法
2.	普通方法的调用：通过对象调用；静态方法的调用：通过对象调用 | 通过类名调用
3.	哪个对象调用，self就代表那个对象
## 对象作为参数传递
**传递的是地址，在方法体内对对象进行修改，会影响原对象的参数，但是地址不变，指向的还是原地址**
## 作用域
1.	在面向对象编程中，主要的变量就是成员变量（属性）和局部变量
2.	局部变量一般指在成员方法中定义的变量，作用域是在它的方法中
3.	作用域的分类：属性作用域为整个类
4.	属性和局部变量可以重名，访问时带上self，表示访问的属性，没有带self，则是访问局部变量
## 构造方法（构造器）
```
def __init__ (self, 参数列表)
	
	代码…
```
1.	在初始化对象时，会自动执行__init__方法
2.	在初始化对象时，将传入的参数，自动传递给__init__方法
3.	构造方法是py预定义的，名称是__init__

**注意事项：**
1.	一个类里只有一个__init__方法，即使写了多个，也只有最后一个生效
2.	Python可以动态的生成对象属性

```commandline
class Person:
	def __init__ (self, name, age):
		self.name = name
		self.age = age
p1 = Person(“tim”, 30)
print(f”p1 name is {p1.name} age is {p1.age}”)
#p1的属性就动态生成为name = tim, age = 30
```

3.	构造方法不能有返回值
# 面向对象编程三大特征：封装，继承和多态
## 封装 encapsulation 
把抽象出的数据[属性]和对数据的操作[方法]封装在一起，数据被保护在内部

程序只有通过被授权的操作，才能对数据进行访问
### 封装的好处
1. 隐藏实现细节
2. 可以对数据进行验证（比如age: 1~120）,保证安全合理
3. 可以保护数据隐私（eg salary）,要求授权才可以访问

### 私有成员
-	默认情况下，类中的变量和方法都是公有的，它们的名称前都没有下划线
-	公共的变量和方法，在类的外部，类的内部，都可以正常访问
1.	如何将属性/方法进行私有化
-	类中的变量或方法以双下划线__开头命名，私有的属性或者方法只能在本类内部使用，类的外部无法使用
2.	如何访问私有的属性/方法
 - 提供公共的方法，用于对私有成员/方法的操作
### 封装的注意事项：
- python语言的动态特性，会出现伪私有属性的情况，并不是真正的对象类定义内的属性

## 继承
继承可以解决代码复用。当多个类存在相同的属性和方法时，可以从这些类中抽象出父类，在父类中定义这些相同的属性和方法，所有子类不需要重新定义它们。好处：提高代码复用性、维护性和扩展性
基本语法：
```
class DerivedClassName(BaseClassName):
<statement - 1> 
.
.
<statement - N> 
```
- 派生类会自动拥有基类定义的属性和方法
- 基类习惯上也叫父类
- 派生类习惯上也叫子类

**注意事项：**
1.	子类继承了所有的属性和方法，非私有的属性和方法可以在子类直接访问，但是私有属性和方法不能在子类直接访问，必须通过父类提供的公共方法去访问
2.	object是所有类的基类，ctrl+ H 查看
3.	允许多重继承 eg. class C(A, B):
4.	在多重继承中，如果有同名的成员，遵守从左到右的继承优先级（即：写左边的父类优先级高，写在右边的父类优先级低）

**调用父类成员的方法：**
1.	如果子类和父类出现同名的成员，可以通过父类名、super()访问父类成员
2.	基本语法：

1）访问父类成员方式1
-	访问成员变量：父类名.成员变量
-	访问成员方法：父类名.成员方法（self）

2）访问父类成员方式2
-	访问成员变量：super().成员变量
-	访问成员方法：super().成员方法()

**注意事项：**
1.	子类不能直接访问父类私有方法和属性
2.	访问不限于直接父类，而是建立从子类向上级父类的查找关系 A->B->C
3.	建议使用super()的方式，因为如果使用父类名方式，一旦父类变化，类名统一需要修改

## 重写override
即子类继承父类的**属性和方法**后，根据业务需要，再重新定义同名的属性或方法

## 类型注解
- 随着项目越来越大，代码也就会越来越多，容易忘记某一个方法的参数类型是什么
- 一旦传入错误类型的参数，python是解释性语言，只有运行时候才能发现问题，这对大型项目来说是一个巨大的灾难
类型注解作用和说明
- 类型提示，防止运行时出现参数类型，返回值类型，变量类型不符合
- 作为开发文档附加说明，方便使用者调用时传入和返回参数类型
- 加入后并不会影响程序的运行，不会报错，只会提醒
- pycharm支持类型注解，参数类型错误会黄色提示
```python
def fun1(a: str): #给形参a进行类型注解
    for ele in a:
        print(ele)
#ctrl + p 参数类型提示
#如果错了，会出现异常
fun1("100")
```
### 变量的类型注解 - 变量：类型
```python
n1: int = 10
n2: float = 10.1
is_pass: bool = True
name: str = "Nancy"
```
### 实例对象类型注解
```python
cat: Cat = Cat()
```
### 容器类型注解
```python
my_list: list = [1, 2, 3]
my_tuple: tuple = ("run", "walk", "laugh")
my_set2: set = {"run", "walk", "laugh"}
my_dict2: dict = {"jack": 100, "nancy": 89}
```
### 容器详细类型注解
```python
# 详细注解都是在[]内
my_list2: list[int] = [100, 200, 300]
my_tuple2: tuple[str, str, float, int] = ("hi", "hello", 11.1, 100)
my_set2: set[str] = {"run", "walk", "laugh"}
my_dict2: dict[str, int] = {"jack": 100, "nancy": 89}
```
### 在注释中使用注解
```python
#type: 类型注解
n3 = 89.9 #type: float
my_list3 = [1, 2, 3] #type: list[int]
email = "aaaaa" #type: str
```
## 函数（方法）类型注解
```python
def 函数名（形参名：type, 形参名：type,...) -> 返回值类型：
    statement

def fun1(name: str):
    for ele in name:
        print(ele)

fun1("nancy")

def fun2(a: int, b: int) -> int:
    return a + b
print(fun2(10, 20))
```
## Union类型
- 可以定义联合类型注解
- 在变量/方法都可以使用Union联合类型注解
- 使用的时候，需要先导入Union: from typing import Union

**基本语法：**
- union[type, type, ...] -意味着满足其中之一即可
```python
from typing import Union

a: Union[int, str] = "hi"

my_list: list[Union[int, str]] = [1,2,3,"hi"]

def cal(num1: Union[int, float], num2: Union[int, float]) -> Union[int, float]:
    return num1 + num2
```
## 多态
即多种状态，不同的对象调用相同的方法，表现出不同的状态，称为多态

多态通常作用在继承关系上
（一个父类，具有多个子类，不同的子类对象调用相同的方法，产生不同的状态）
```python
class Animal:
    def cry(self):
        pass
class Cat(Animal):
     def cry(self):
         print("meow")
class Dog(Animal):
    def cry(self):
        print("bark")
#子类对象可以传递给父类类型
def func(animal: Animal):
    animal.cry()

cat = Cat()
dog = Dog()

func(cat) #meow
func(dog) #bark
```
**多态的好处：**
- 增加了程序的灵活性，无论对象是谁，使用者都是同一种形式去调用。eg func(animal)
- 增加了程序的可扩展性，通过继承Animal类创建了一个新类，使用者无需更改自己的代码，还是用func(animal)去调用
### isinstance函数
- isinstance()用于判断对象是否为某个类或其子类的对象
- 基本语法：
```python
isinstance(object, classinfo)
object: 对象
classinfo: 可以是类名，基本类型或者由它们组成的元组
num = 9
print(isinstance(num, (str, int, tuple))) #True
```
Exercise:
```python
class A:
    i = 10
    def sum(self):
        return self.getI() + 10
    def sum1(self):
        return self.i + 10
    def getI(self):
        return self.i
    
class B(A):
    i = 20
    def getI(self):
        return self.i

b = B() #对象为B
#当调用对象成员的时候，会和对象本身动态关联，self指B
print(b.sum()) # 30 20 + 10 = 30
print(b.sum1()) # 30 20 + 10 = 30
```
```python
class Employee:
    __name = None
    __sal = None

    def __init__(self, name, sal):
        self.__name = name
        self.__sal = sal

    def get_annual(self):
        return self.__sal * 12
    def set_name(self,name):
        self.__name = name
    def get_name(self):
        return self.__name
    def set_sal(self, sal):
        self.__sal = sal
    def get_sal(self):
        return self.__sal

class Worker(Employee):
    def work(self):
        #因为Worker类中并没有get_name()这个方法，所以可以用self.get_name(),此方法可以去找父类方法
        #如果本类中有此方法，则必须要用super().get_name()去调用父类的方法
        print(f"normal employee {self.get_name()} is working...")
class Manager(Employee):
    __bonus = None
    #多了bonus属性，需要再次定义构造器
    def __init__(self, name, sal, bonus):
        super().__init__(name, sal)
        self.__bonus = bonus

    def manage(self):
        print(f"manager {self.get_name()} is managing")

    def __get_annual(self):
        return super().get_annual() + self.__bonus
#获取任何员工的年工资
def show_emp_annual(employee: Employee):
    print(f"{employee.get_name()}'salary is {employee.get_sal()}")
#如果是普通员工，调用work, 经理调用manage方法
def working(e: Employee):
    if(isinstance(e, Worker)):
        e.work()
    elif(isinstance(e, Manager)):
        e.manage()
    else:
        print("invalid")

work = Worker("Tim", 10000)
show_emp_annual(work)
working(work)
m = Manager("nancy", 20000, 100000)
show_emp_annual(m)
working(m)
```
## 魔术方法 Magic method
- 在python中，所有以双下划线__包起来的方法称为魔术方法，不需要调用可以自动执行
- 在类或对象的某些事件发生时会自动执行，让类具有神奇的“魔力”
- 常用的运算符，for循环，以及类操作等都是运行在魔术方法之上的
常用操作：
- __str__: 打印对象默认返回：类型名 + 对象内存地址，子类往往重写__str__，用于返回对象的属性信息
- 重写__str__，print(obj) or str(obj),都会自动调用__str__
- __eq__: ==是比较运算符，对象之间进行比较，比较的是内存地址是否相等，即是否是同一个对象
- 重写__eq__，可以用于判断对象内容/属性是否相等
# 对象
万物皆对象，类本身也是对象
```python
class Monster:
    name = None
    age = None
    def hi(self):
        print(f"hi(){self.name} - {self.age}")
print(Monster)
#通过class对象，可以引用属性（没有创建实例对象也可以访问/引用）
print(f"Monster.name: {Monster.name} Monster.age: {Monster.age}")
#通过类名如何调用非静态成员方法
Monster.hi(Monster)
```
## 静态方法
- @staticmethod 将方法转换为静态方法
- 静态方法不会接收隐式的第一个参数，要声明一个静态方法，语法：
```python
class C:
    @staticmethod
    def f(arg1, arg2, arg3...):
        statement
        
    @staticmethod
    def hi():
        print("hi")
```
- 静态方法既可以由类调用（C.f()),也可以由实例中调用（C().f())
# 抽象类
1. 默认情况下，python不提供抽象类，python附带一个模块，该模块为定义抽象基类提供了基础，该模块名称为abc
2. 当我们需要抽象基类时，让类继承ABC(abc模块的ABC类)，使用@abstractmethod声明抽象方法
（@abstractmethod用于声明抽象方法的装饰器，在abc模块中），那么这个类就是抽象类
3. 抽象类的价值更多作用是在于设计，是设计者设计好后，让子类继承并实现抽象类的抽象方法
```python
from abc import ABC, abstractmethod
class Animal(ABC):
    def __init__(self, name, age):
        self.name = name
        self.age = age
    @abstractmethod
    def cry(self):
        pass
#抽象类（含有抽象方法），不能实例化
#TypeError: Can't instantiate abstract class
#animal = Animal("tiger", 2)
class Tiger(Animal):
    def cry(self):
        print("ao~")

tiger = Tiger("TT", 2)
tiger.cry()
```

**注意事项**
- 抽象类（含有抽象方法），不能实例化
- 抽象类需要继承ABC，并且需要至少一个抽象方法，**两者缺一不可！
```python
#抽象类
class Animal(ABC):
    @abstractmethod
    def cry(self):
        pass
#不是抽象类，没有继承ABC
class Animal():
    @abstractmethod
    def cry(self):
        pass
#不是抽象类，没有@abstractmethod
class Animal(ABC):
    def cry(self):
        pass
```
- 抽象类可以有普通方法
```python
#抽象类
class Animal(ABC):
    @abstractmethod
    def cry(self):
        pass
    def eat(self):
        pass
```
- 如果一个子类继承了抽象类，必须要实现抽象类中的全部抽象方法，否则它仍然是一个抽象类
Exercise:
```python
from abc import ABC, abstractmethod
class Employee(ABC):
    def __init__(self, name, id, salary):
        self.name = name
        self.id = id
        self.salary =salary
    @abstractmethod
    def work(self):
        pass
class CommonEmployee(Employee):
    def work(self):
        print(f"common employee {self.name} is working")
class Manager(Employee):
    def __init__(self, name, id, salary, bonus):
        super().__init__(name, id, salary)
        self.bonus = bonus
    def work(self):
        print(f"manager {self.name} is working")
m = Manager("K", "111111", 100000, 100000)
m.work()
w = CommonEmployee("W", "22222", 10000)
w.work()
```
## 模板设计模式
设计模式：是在大量的实践中总结和理论化之后优选的代码结构，编程风格，以及解决问题的思考方式
模板设计模式：抽象类体现的就是一种模板模式的设计，抽象类作为多个子类的通用模板，子类在抽象类的基础上进行扩展、改造，但是子类总体上会保留抽象类的行为方式
模板设计模式能解决的问题：
- 当功能内部一部分实现是确定，一部分实现是不确定的。这时可以把不确定的部分暴露出去，让子类去实现
- 编写一个抽象父类，父类提供了多个子类的通用方法，并把一个或多个方法留给其子类实现，就是一种模板模式
```python
import time
from abc import ABC, abstractmethod
class Template(ABC):
    @abstractmethod
    def job(self):
        pass
    #计算程序运行时间
    def cal_time(self):
        # *1000 - > 毫秒
        start_time = time.time() * 1000
        self.job()
        end_time = time.time() * 1000
        print(end_time - start_time)

class AA(Template):
    def job(self):
        num = 0
        for i in range(1, 80001):
            num += i

class BB(Template):
    def job(self):
        num = 0
        for i in range(1, 80001):
            num -= i
#if __name__ = '__main__':

aa = AA()
aa.cal_time() #13.9609375
bb = BB()
bb.cal_time() #12.96484375
```
Exercise:
```python
#根据员工年龄进行排序
class Person:
    def __init__(self, name, age, job):
        self.name = name
        self.age = age
        self.job = job
    def __str__(self):
        return f"{self.name} - {self.age} - {self.job}"


p1 = Person("kim", 22, "software developer")
p2 = Person("nancy", 33, "researcher")
p3 = Person("Jon", 18, "deliver")
my_list = [p1, p2, p3]
#方法一： 冒泡排序
# def bubble_sort(my_list: list[Person]):
#     for i in range(0, len(my_list) - 1):
#         for j in range(0, len(my_list) - 1 - i):
#改为根据年龄进行判断
#             if my_list[j].age < my_list[j + 1].age:
#                 my_list[j], my_list[j+1] = my_list[j+1], my_list[j]
#
# print("sort".center(32, '-'))
# bubble_sort(my_list)
#输出排序后结果
# for ele in my_list:
#     print(ele)
#方法二： 根据sort函数进行年龄排序（key为排序函数体，reverse T为从大到小，F为从小到大）
my_list.sort(key = lambda ele: ele.age, reverse = True)
for ele in my_list:
    print(ele)
```
练习魔术方法：__eq__
```python
class Doctor:
    def __init__(self, name, age, job, gender, sal):
        self.name = name
        self.age = age
        self.job = job
        self.gender = gender
        self.sal = sal

    def __eq__(self, other):
        if not isinstance(other, Doctor):
            return False
        return (self.name == other.name and
                self.age == other.age and
                self.job == other.job and
                self.gender == other.gender and
                self.sal == other.sal)
doctor1 = Doctor("tim", 33, "dentist", "male", 10000)
doctor2 = Doctor("tim", 33, "dentist", "male", 10000)
print(doctor1 == doctor2) #True
```
# error, exception
python 有两种不同错误：语法错误（句法错误/解析错误）和异常（正确的语法，但是执行时候检测到的错误）
## 捕获异常
```python
try:
    n1 = 4
    n2 = 0
    res = n1 / n2
except Exception as e:
    print(e) #division by zero
print("continue") #continue
```
## 异常处理
常见语法：
```python
try:
    可能出现异常的代码
    #[Exception as e]是可选项，表示捕获到try中出现的异常，并通过别名e接收
except [异常 as e]:
    对异常处理的代码
[else:]
    没有发生异常，执行的代码
[finally:]
    不管有没有异常，都要执行的代码
Note: []是可选项，可有可无
```
**注意事项：**
- 如果异常发生了，则异常发生后面的代码不会执行，直接进入到except子句
- 如果没有异常发生，则顺序执行try的代码块，不会进入except子句
- 如果希望没有发生异常时，要执行某段代码，则使用else子句
- 如果希望不管是否有异常发生，都执行某段代码，则使用finally子句
- 可以有多个except子句，捕获不同的异常，如果发生异常，只会匹配一个异常。通常把具体的异常放前面，基类异常放后面
- 一个except子句，可以捕获不同的异常
Exercise:
```python
age = 0
while(True):
    try:
        age = int(input("enter age: "))
        break
    except:
        print("enter integer age")
print(age)
```
## 触发异常/抛出异常
raise语句支持强制触发指定的异常
```python
raise NameError('Hi There')
```
## 异常的传递
- 如果一个异常发生了，但是没有捕获处理异常，那么这个异常会抛给调用者
- 如果所有调用者都没有处理，最终会由系统处理
## 自定义异常
- 程序可以通过创建新的异常类命名子句的异常。不论是以直接还是间接的方式，异常都应从Except类派生
- 异常类通常应当保持简单，它往往只提供一些属性，允许相应的异常处理程序提取有关错误的信息
- 大多数异常命名都已“Error"结尾，类似标准异常的命名，但是需要注意不要使用内置异常名
# 文件
是保存数据的地方
输入（读文件）：数据从数据源（文件）到程序（内存）
输出（写文件）：数据从程序（内存）到数据源（文件）
I/O（input/output）类型
主要为文本I/O（通常是记事本可以直接打开的，.py, .txt等）和二进制I/O(图片，视频，音频等)，在处理不同类型文件时，需要用对应的方式打开处理
文件编码（字符编码）：UTF-8最常用
- 创建文件操作
```python
f1 = open("d://a//hi.txt", "w", encoding = "utf-8")
如果我们要创建一个文件，只需要以mode = "w"(write)形式打开文件，如果文件不存在，系统会自动创建文件
注意：encoding = "utf-8" 不能少
```
- 读文件
```python
f = open("d://a//hello.txt", "r", encoding = "utf-8")
# 方式1：
content = f.read() #一次性读取全部内容
content = f.read(6) #规定读取6个字符
# 方式2：
line1 = f.readline() #读取第一行\n
line2 = f.readline() #读取第二行\n
print(line1, end = "")#必须加end = ""，否则输出将换2行，因为print也自带换行
# 方式3：
lines = f.readlines() #['第一行数据\n', '第二行数据\n', '第三行数据\n'...]
for line in lines:#lines是一个list
    print(line, end="")
# 方式4：
for line in f:
    print(line, end="")
f.close()
```
- 写文件
```python
# mode = "w"打开文件，如果文件不存在，会创建，如果文件已经存在，会先截断打开的文件，也就是清空文件（！！！）
# 如果我们希望以追加的方式写入，需要mode="a"
f = open("d://a//hello.txt", "w", encoding = "utf-8")
# 写入10行
i = 0
while i < 10:
    f.write("hi\n")
    i += 1
f.close()
#将内容覆盖成10句“hello"
#将文件在”w"的状态下打开，写入文件就是覆盖
//"a"模式就是在原有文件上追加
f = open("d://a//hello.txt", "a", encoding = "utf-8")
i = 0
while i < 10:
    f.write("python\n")
    i += 1
f.close()
```
- 删除文件
```python
import os
if os.path.exists("d://a//abc.txt"):
    os.remove("d://a//abc.txt")
else:
    print("the file is not exists")
```
## 目录操作
```python
#创建一级目录
import os
if os.path.isdir("d://aaa"):#判断是否存在
    print("direct is exists")
else:
    os.mkdir("d://aaa")#不存在，就创建一级目录
#创建多级目录
import os
if os.path.isdir("d://bbb//ccc"):#判断是否存在
    print("direct is exists")
else:
    os.makedirs("d://bbb//ccc")#创建多级目录
#删除目录
import os
if os.path.isdir("d://aaa"):#判断是否存在
    os.rmdir("d://aaa")#删除一级目录
    os.removedirs("d://bbb//ccc")#删除多级目录
else:
    print("not exists")
```
## 获取文件的相关信息
```python
import os
import time
#time.ctime()是将返回来的时间戳转为字符串形式
f_stat = os.stat("d:/a/hello.txt")
print(f"文件大小{f_stat.st_size} \n"
f"最近访问时间{time.ctime(f_stat.st_atime)} \n"
f"最近的修改时间{time.ctime(f_stat.st_mtime)} \n"
f"文件创建时间{time.ctime(f_stat.st_ctime)}")
```
**注意事项：**
- f.flush():刷新流的写入缓冲区到文件
    - 调用f.write(),内容并没有真正写入文件，而是先积攒到缓存区
    - 当调用flush()时，内容会真正写入到文件
    - 这样做是为了避免频繁操作硬盘，导致效率过低
- f.close():刷新并关闭此流，也就是f.close()内置的flush功能
- with open() as f:在处理文件对象时，子句体结束后，文件会自动关闭
```python
#with子句的方式完成文件拷贝，可以读一部分写一部分
#f.read(),f.write()是直接读取并写入全部文件，对内存压力很大
#使用with子句可以自动关闭文件
f_src_path = "C:/Users/Administrator/Music/无名.mp3"
f_dst_path = "d:/a/无名_new.mp3"
with open(f_src_path, "rb") as f_src:
    with open(f_dst_path, "wb") as f_dst:
        for data in f_src:
            f_dst.write(data)
``` 
