### re是否有用过（Python正则匹配包），如何匹配空格

```python
pattern  = r'str' # Define the pattern you want to search for 
text  = 'Your text here, containing the string you want to find'
matches = re.findall(pattern, text)
re.match(pattern,str,flags)
##falgs:re.I,re.M,是否区分大写，是否多行匹配
##.*匹配0个或者多个
##.*?匹非贪婪匹配匹配一个
##（*.）匹配成功会独立成组，通过组索引访问matched.group(index:1-n)
re.search(pattern, string, flags=0)#返回第一个成功匹配的
##search与match区别
# re.match 与 re.search的区别
# re.match 只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回 None，而 re.search 匹配整个字符串，直到找到一个匹配。
#re.sub用于替换字符串中的匹配项。
#re.sub(pattern,fun,str,count = 0,flags)
#将匹配数字×2
str = 'ghgh12'
def double(matched):
    value =  int(matched.group('value'))
    return str(value*2)
re.sub(('?P<value>\d+'),double,str)

compile函数用于编译正则表达式，生成一个正则表达式（ Pattern ）对象，供 match() 和 search() 这两个函数使用

```

### 自己写好的Python包如何给别人使用，需要怎么配置
1、新建一个文件夹
2、建立一个包，写核心代码
3、写setup.py文件
整个目录为
-my-wheel
--mywheel
---__init__.py
---example.py
--setup.py 
4、安装包 python install setup.py
5、使用包
from mywheel.eample import fun
6、上传pypi
### 元组长度可变吗，如何定义一个长度为1的元组，如何对元组进行迭代

```python
不可变
a = (1,)##要加，
for i range(len(a))
  a[i-1]
  ###元组特点 与string类型相似1、与字符串一样，元组的元素不能修改。
# 2、元组也可以被索引和切片，方法一样。
# 3、注意构造包含 0 或 1 个元素的元组的特殊语法规则。
# 4、元组也可以使用+操作符进行拼接。
      
  ```
### 将py文件打包成可执行的.exe文件
pyinstaller -i ico.png -F -w demo.py
-i 指定打包文件的图标
-F dist目录只生成一个exe文件

### Python异常机制

- 异常类
- raise 引发异常
- 处理异常 捕获异常进行处理
- 最终快 final执行所有操作之后的异常处理
  

