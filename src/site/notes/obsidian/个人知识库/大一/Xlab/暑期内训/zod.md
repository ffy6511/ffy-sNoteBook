---
{"dg-publish":true,"permalink":"/obsidian///xlab//zod/","created":"2024-08-24T21:23:19.352+08:00","updated":"2024-09-08T15:25:05.470+08:00"}
---

# 作用
- Zod 是一个 TypeScript 和 JavaScript 的**数据验证库**，用于**定义和验证**数据结构；
- 非常适合用于确保数据的类型和结构正确；
- 🌰：例如在 API 请求、表单验证、配置文件验证等场景中

# 基本用法
1. 导入Zod:
```ts
import  { z }  from "zod";
```

2. 创建特定模式：
```ts
const mySchema = z.string( );
```
>描述了一个值必须是字符串类型。

3. 解析数据
```ts
mySchema.parse("tuna") ; // 返回 “tuna"
```
>`"tuna"` 是一个有效的字符串，符合 `mySchema` 的要求，所以 `parse` 方法返回 `"tuna"`
同理，如果不符合·mySchema`的要求，就抛出报错

4. 安全解析
```ts
mySchema.safeParse("tuna"); // => { success: true; data: "tuna" }
```

```ts
mySchema.safeParse(12); // => { success: false; error: ZodError }
```

与 `parse` 方法类似，但它不会抛出错误，而是返回一个**结果对象**

## 对象结构

- 作用：
	- 通过 `z.infer`，你可以自动生成类型，而不必手动编写；
	- 这避免了代码中的重复，并确保你的数据验证逻辑和类型注解保持一致。
- 🌰
```ts
const User = z.object({ username: z.string(), }); //定义了一个名为 `User` 的模式，它是一个对象结构

type User = z.infer<typeof User>; // { username: string }
```
