# PC端连接超时或连接不上的问题及解决方案

## 解决方案来源

来自 [lejianwen](https://github.com/lejianwen/rustdesk-api/issues/92) 的解决方案

## 修改位置

在 `src/common.rs` 文件中，找到 `pub async fn secure_tcp` 函数，在函数开头添加 `return Ok(());`

### 原代码

```rust
pub async fn secure_tcp(conn: &mut Stream, key: &str) -> ResultType<()> {
    if use_ws() {
        return Ok(());
    }
    ....
```

### 修改代码

```rust
pub async fn secure_tcp(conn: &mut Stream, key: &str) -> ResultType<()> {
    return Ok(());  /*←←←←←←←←←*/
    if use_ws() {
        return Ok(());
    }
    ....
```
