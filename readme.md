# 运行

```bash
yarn dev
```

# API 设计

## 用户功能

### 获取用户信息

- method `get`
- path `/api/user/info`
- response `{errno: 0, data: {...} }` 或 `{ errno: 10001, msg: 'xxx' }`

### 注册

- method `post`
- path `/api/user/register`
- request body `{ username, password, nickname }`
- response `{ errno: 0 }`

### 登录

- method `post`
- path `/api/user/login`
- request body `{ username, password }`
- response `{ errno: 0, token }` -- **JWT** 使用 token

## 问卷功能

### 创建问卷

- method `post`
- path `/api/question`
- request body - 无（点击一个按钮即可创建，title 自动生成）
- response `{ errno: 0, data: { id } }`

### 获取单个问卷

- method `get`
- path `/api/question/:id`
- response `{ errno: 0, data: { id, title ... } }`

### 获取问卷列表

- method `get`
- path `/api/question`
- response `{ errno: 0, data: [...] }`

### 更新问卷信息

- method `patch`
- path `/api/question/:id`
- response `{ errno: 0 }`

PS: 删除是`假删除`，实际是更新 `isDelete` 属性

### 批量彻底删除问卷

- method `delete`
- path `/api/question`
- request body `{ ids: [...] }`
- response `{ errno: 0 }`

### 复制问卷

- method `post`
- path `/api/question/duplicate/:id`
- response `{ errno: 0, data: { id } }`

## 小结

- 使用 Restful API
    - Restful API 是现在设计 API 比较通用的一种方式
- 用户验证使用 JWT
- 同意返回格式 `{ errno, data, msg }`
