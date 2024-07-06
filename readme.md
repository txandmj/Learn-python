# A first-level heading

Some basic Git commands are:
```
git status
git add
git commit
```
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

