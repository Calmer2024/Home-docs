# React学习

在 React 中，`onClick={() => handleTabChange(item.type)}` 是一种常见的事件处理写法，其设计意图和底层逻辑如下：

### **一、代码含义解析**

```jsx
<button onClick={() => handleTabChange(item.type)}>
  切换标签页
</button>
```

- **箭头函数** `() => handleTabChange(item.type)`：
  定义了一个匿名函数，当点击事件触发时，该函数会调用 `handleTabChange`，并传递参数 `item.type`。
- **参数传递** `item.type`：
  将当前作用域下的 `item.type` 值作为参数传递给处理函数。

### **二、为什么需要这样写？**

#### 1. **解决参数传递问题**

- **场景**：当需要将动态数据（如列表项的 `type`）传递给事件处理函数时，直接写 `onClick={handleTabChange(item.type)}` 会导致函数 **立即执行**，而非在点击时触发。
- **箭头函数的作用**：延迟执行 `handleTabChange`，直到点击事件发生。

#### 2. **避免闭包陷阱**

- **问题示例**（循环中直接使用变量）：

  ```jsx
  {items.map((item) => (
    <button 
      key={item.id}
      onClick={handleTabChange(item.type)} // ❌ 渲染时立即执行！
    >
      {item.name}
    </button>
  ))}
  ```

- **正确写法**：

  ```jsx
  {items.map((item) => (
    <button 
      key={item.id}
      onClick={() => handleTabChange(item.type)} // ✅ 点击时执行
    >
      {item.name}
    </button>
  ))}
  ```