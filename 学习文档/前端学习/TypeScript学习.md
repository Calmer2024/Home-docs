# TypeScript

https://www.typescriptlang.org/zh/docs/handbook/typescript-from-scratch.html

阮一峰的 TypeScript 教程：https://typescript.p6p.net/typescript-tutorial/intro.html



使用ts-node包

#### **1. 核心思想：什么是 TypeScript？**



- **JavaScript 的超集**：你可以将 TypeScript 视为 “带有类型的 JavaScript”。任何合法的 JavaScript 代码也是合法的 TypeScript 代码。
- **静态类型系统**：这是 TypeScript 最核心的功能。它允许你在代码编写阶段就为变量、函数参数、返回值等指定类型。
- **编译到 JavaScript**：浏览器和 Node.js 无法直接运行 TypeScript。你需要一个编译器（`tsc`）将 `.ts` 文件编译成纯净、兼容性良好的 `.js` 文件。

一句话总结：**TypeScript = JavaScript + 静态类型 + 最新 ES 特性**



#### **2. 为什么要使用 TypeScript？**



| 痛点 (JavaScript)                                            | 解决方案 (TypeScript)                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| TypeError: Cannot read property 'x' of undefined 在运行时才发现。 | **类型安全**：在代码**编译时**就能发现类型错误，避免大量低级 Bug。 |
| 函数参数传错类型或个数，难以察觉。                           | **明确的函数签名**：参数类型、数量和返回值类型一目了然。     |
| 无法确定一个对象有哪些属性和方法。                           | **强大的代码提示**：IDE（如 VS Code）能根据类型信息提供精准的自动补全和智能提示。 |
| 大型项目代码难以阅读和维护。                                 | **代码即文档**：类型注解本身就是一种清晰、可靠的文档，极大提升了可读性和协作效率。 |



#### **3. 环境搭建**



你需要安装 Node.js 和 npm（通常随 Node.js 一起安装）。

1. **全局安装 TypeScript 编译器**：

   ```bash
   npm i -g typescript
   ```

2. **编译一个 TS 文件**： 创建一个文件 `hello.ts`，然后运行：

   ```bash
   tsc hello.ts
   ```

   这会生成一个 `hello.js` 文件，你可以在浏览器或 Node.js 中运行它。

3. **使用node命令运行该js文件**：

   ```bash
   node hello.js
   ```

4. **使用 ts-node 命令简化操作**：

   ```bash
   #先全局安装 ts-node 包
   npm i -g ts-node
   
   #再使用 ts-node 命令直接运行ts代码
   ts-node hello.ts
   ```

------



### **4. 核心概念速览**





#### **A. 类型注解 (Type Annotation)**



这是 TypeScript 的基础。使用 `: Type` 的语法来指定类型。

```typescript
// 变量类型注解
let name: string = "张三";
let age: number = 25;
let isStudent: boolean = true;

// 函数参数和返回值类型注解
function greet(person: string, date: Date): string {
  return `你好, ${person}, 今天是 ${date.toDateString()}!`;
}

// 调用时如果类型不匹配，会立即报错
// greet(123); // Error: Argument of type 'number' is not assignable to parameter of type 'string'.
```



#### **B. 常见基础类型**



| 类型        | 描述                                   | 示例                                          |
| ----------- | -------------------------------------- | --------------------------------------------- |
| `string`    | 字符串                                 | `let s: string = "hello";`                    |
| `number`    | 数字                                   | `let n: number = 100;`                        |
| `boolean`   | 布尔值                                 | `let b: boolean = false;`                     |
| `any`       | 任意类型（**慎用！**会失去类型检查）   | `let d: any = 4; d = "four";`                 |
| `unknown`   | 未知类型（`any` 的安全版本）           | `let u: unknown = "hello";`                   |
| `void`      | 通常用于函数，表示没有返回值           | `function log(): void { console.log("Hi"); }` |
| `null`      | `null`                                 | `let n: null = null;`                         |
| `undefined` | `undefined`                            | `let u: undefined = undefined;`               |
| `object`    | 非原始类型（非 `string`, `number` 等） | `let obj: object = { a: 1 };`                 |



#### **C. 数组 (Array) 与元组 (Tuple)**



- **数组**：同一类型元素的集合。

  ```typescript
  let list1: number[] = [1, 2, 3];
  let list2: Array<string> = ["a", "b", "c"];
  ```

- **元组**：固定长度和固定类型的数组。

  ```typescript
  let person: [string, number] = ["李四", 30];
  // person[0] 必须是 string, person[1] 必须是 number
  // person = [30, "李四"]; // Error
  ```



#### **D. 接口 (Interface)**



接口用于**描述对象的结构（Shape）**，是 TypeScript 中最强大的功能之一。

```typescript
// 定义一个接口来描述一个用户的结构
interface User {
  readonly id: number; // readonly 表示只读属性
  name: string;
  email: string;
  isAdmin?: boolean; // ? 表示可选属性
}

// 使用接口作为函数参数的类型
function printUser(user: User): void {
  console.log(`ID: ${user.id}, Name: ${user.name}, Email: ${user.email}`);
}

let myUser: User = {
  id: 1,
  name: "王五",
  email: "wangwu@example.com"
};

printUser(myUser); // OK

// let invalidUser = { id: 2, name: "赵六" }; // Error: Property 'email' is missing.
```



#### **E. 联合类型 (Union Types) 与 类型别名 (Type Aliases)**



- **联合类型**：表示一个值可以是多种类型之一，使用 `|` 分隔。
- **类型别名**：为复杂的类型创建一个新名字，使用 `type` 关键字。

```typescript
// ID 可以是数字或字符串
type ID = string | number;

function printId(id: ID): void {
  // 使用联合类型时，通常需要进行类型收窄
  if (typeof id === "string") {
    console.log(id.toUpperCase());
  } else {
    console.log(id);
  }
}

printId(101);       // 输出: 101
printId("202-abc"); // 输出: 202-ABC
```



#### **F. 泛型 (Generics)**



泛型允许你创建可重用的组件，这些组件可以处理多种类型而不是单一类型。

```typescript
// T 是一个类型变量，它捕获了传入参数的类型
function identity<T>(arg: T): T {
    return arg;
}

// 调用时可以明确指定类型
let outputString = identity<string>("myString");

// 也可以让 TypeScript 自动推断类型
let outputNumber = identity(123);

console.log(typeof outputString); // string
console.log(typeof outputNumber); // number
```