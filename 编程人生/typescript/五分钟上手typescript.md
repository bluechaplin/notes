# 五分钟上手typescript

## 安装ts

两种方式

- 通过`npm`（Node.js包管理器）或者`yarn`全局安装，记得是要配置了环境变量
- 安装`Visual Studio`的TypeScript插件

使用`npm`

```powershell
npm install -g typescript
```

使用`yarn`

```powershell
yarn global add typescript
```

## 编写

新建`greeter.ts`，输入以下内容

```typescript
function greeter(person) {
    return "Hello, " + person;
}

let user = "Jane User";

document.body.innerHTML = greeter(user);
```

## 编译

`ts`代码并不能直接被解释器执行，需要通过`typescript`引擎编译成`java script`之后才可以执行

在命令行上，运行`TypeScript`编译器：

```powershell
tsc greeter.ts
```

执行完了之后，我们能看到一个greeter.js的文件

## 特性

### 类型注解

`TypeScript`里的类型注解是一种轻量级的为函数或变量添加约束的方式。

比如上面的`greeter`函数，如果我们希望约束接收的参数类型为字符串类型，我们就可以在参数后面加上一个类型约束，如下

```typescript
function greeter(person: string) {
    return "Hello, " + person;
}

let user = "Jane User";

document.body.innerHTML = greeter(user);
```

这时候如果方法调用者不遵循我们约束的参数类型，编译就会看到错误

```typescript
function greeter(person: string) {
    return "Hello, " + person;
}

let user = 100;

document.body.innerHTML = greeter(user);
```

![image-20211227170822708](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112271708800.png)

需要注意的是，虽然编译的时候发生了错误，但是`greeter.js`还是被创建出来了，只是这种情况下代码的执行情况大概率会跟预期的不相符

### 接口

在`ts`中，我们可以使用接口类型来描述多字段的对象。在`ts`中，只要两个对象类型内部的结构兼容，那这两个类型就是兼容的，这意味着我们在实现接口的时候只需要保证包含了接口要求的类型就可以了，而且无需明确的使用`implements`语句

```typescript
interface Person {
    firstName: string;
    lastName: string;
}

function greeter(person: Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}

let user = { firstName: "Jane", lastName: "User" };

document.body.innerHTML = greeter(user);
```

### 类

TypeScript支持JavaScript的新特性，比如支持基于类的面向对象编程。

让我们创建一个`Student`类，它带有一个构造函数和一些公共字段。 注意类和接口可以一起共作，程序员可以自行决定抽象的级别。

还要注意的是，在构造函数的参数上使用`public`等同于创建了同名的成员变量。

```typescript
class Student {
    fullName: string;
    constructor(public firstName, public middleInitial, public lastName) {
        this.fullName = firstName + " " + middleInitial + " " + lastName;
    }
}

interface Person {
    firstName: string;
    lastName: string;
}

function greeter(person : Person) {
    return "Hello, " + person.firstName + " " + person.lastName;
}

let user = new Student("Jane", "M.", "User");

document.body.innerHTML = greeter(user);
```

## 运行

在`greeter.html`里输入如下内容：

```html
<!DOCTYPE html>
<html>
    <head><title>TypeScript Greeter</title></head>
    <body>
        <script src="greeter.js"></script>
    </body>
</html>
```

浏览器打开`greeter.html`
