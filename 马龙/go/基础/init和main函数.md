# init和main函数

## init函数

### 作用

init函数用于包的初始化

### 特点

- 每个包可以拥有多个`init()`函数
- 包的每个源文件也可以拥有多个`init()`函数
- `init()`函数不能被其他函数调用，而是在main函数执行之前，自动被调用
- 对同一个go文件的`init()`调用顺序是从上到下的
- 对同一个package中不同文件是按文件名字符串比较“从小到大”顺序调用各文件中的`init()`函数
- 对于不同的`package`，如果不相互依赖的话，按照main包中”先`import`的后调用”的顺序调用其包中的`init()`，如果`package`存在依赖，则先调用最早被依赖的`package`中的`init()`，最后调用`main`函数
- 如果`init`函数中使用了`println()`或者`print()`你会发现在执行过程中这两个不会按照你想象中的顺序执行。这两个函数官方只推荐在测试环境中使用，对于正式环境不要使用

## main函数

### 作用

`main()`是默认的程序入口函数

### 特点

- `main()`函数只能用于`main`包中，且只能定义一个

## 共同点

两个函数在定义时不能有任何的参数和返回值，且Go程序自动调用。