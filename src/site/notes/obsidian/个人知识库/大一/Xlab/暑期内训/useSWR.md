---
{"dg-publish":true,"permalink":"/obsidian///xlab//use-swr/","created":"2024-08-02T22:50:21.834+08:00","updated":"2024-09-08T15:25:05.468+08:00"}
---

`useSWR` 是一个基于 React 的数据请求库

1. **自动数据缓存和重新验证**：
    
    - SWR 会将请求的数据缓存起来，当组件重新渲染时，它会先返回缓存中的数据，同时在后台重新请求数据，并在数据更新后再次渲染组件。
2. **减少网络请求**：
    
    - 通过缓存机制，SWR 可以减少重复的网络请求，提高性能。
3. **简化数据请求逻辑**：
    
    - 使用 SWR 可以让数据请求逻辑更简单，避免手动处理各种状态（加载中、错误、数据更新等）。
4. **自动处理错误重试**：
    
    - SWR 内置了错误重试机制，当请求失败时，它会自动重试请求。
5. **支持本地数据变更（乐观更新）**：
    
    - SWR 支持在本地直接修改缓存中的数据，可以实现乐观更新的效果。
6. **支持分页和滚动加载**：
    
    - SWR 提供了对分页和无限滚动加载的支持。
7. **简单的 API**：
    
    - `useSWR` 提供了一个简单的 API，只需要提供一个 key 和 fetcher 函数即可。

---
🌰:
```js
import useSWR from 'swr'

const fetcher = url => fetch(url).then(res => res.json())

function Profile() {
  const { data, error } = useSWR('/api/user', fetcher)

  if (error) return <div>Failed to load</div>
  if (!data) return <div>Loading...</div>

  return <div>Hello {data.name}!</div>
}

```
在这个示例中：
- `useSWR` 接受两个参数：数据的 key（这里是 API 的 URL）和一个 fetcher 函数（负责获取数据）。
- 返回的数据对象包含 `data` 和 `error` 两个属性，用于分别处理数据和错误状态。
- 组件会首先显示缓存中的数据（如果有），然后在后台重新获取数据并更新。