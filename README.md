# PC端连接超时或连接不上的问题及解决方案

## 解决方案来源

来自 [lejianwen](https://github.com/lejianwen/rustdesk-api/issues/92) 的解决方案

## 修改位置

在 `src/common.rs` 文件中，找到 `async fn key_exchange` 函数，在函数开头添加 `return Ok(());`

### 原代码

```rust
async fn key_exchange(conn: &mut Stream, key: &str, log_on_success: bool) -> ResultType<bool> {
    return Ok(());
    let rs_pk = get_rs_pk(key);
    let Some(rs_pk) = rs_pk else {
        bail!("Handshake failed: invalid public key from rendezvous server");
    };
```

### 修改代码

```rust
async fn key_exchange(conn: &mut Stream, key: &str, log_on_success: bool) -> ResultType<bool> {
    return Ok(());    /*←←←←←←←←←*/
    let rs_pk = get_rs_pk(key);
    let Some(rs_pk) = rs_pk else {
        bail!("Handshake failed: invalid public key from rendezvous server");
    };
```
