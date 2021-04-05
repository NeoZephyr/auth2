# 客户端凭据许可

如果没有明确的资源拥有者，第三方软件访问了一个不需要用户授权的数据。在这种场景下授权，就是客户端凭据许可。第三方软件直接通过注册时的 app_id 和 app_secret 换回 access_token。此时，第三方软件可以随时发起请求获取 access_token，因此这种授权不需要刷新令牌

## 授权流程

1. 第三方软件向授权服务请求 access_token，附带 app_id 和 app_secret。此时 grant_type 为 client_credentials
2. 授权服务返回 access_token
3. 第三方软件使用 access_token 访问受保护的资源
