# 隐式许可

如果第三方软件没有后端服务，就是在浏览器中执行的，这种情况下的授权流程就可以使用隐式许可流程


## 授权流程

1. 用户通过浏览器访问第三方软件，此时，第三方软件相当于是嵌入到浏览器中的应用程序
2. 第三方软件向授权服务请求 access_token
3. 授权服务生成 access_token 返回给第三方软件
4. 第三方软件使用 access_token 访问受保护的资源


## 示例

1. app 生成一个随机的、长度 43 - 128 字符之间的、参数为 code_verifier 的字符串验证码
2. 利用 code_verifier 生成挑战码参数 code_challenge。如果 code_challenge_method 参数值为 plain，则生成的 code_challenge 值就是 code_verifier 的值；如果 code_challenge_method 参数的值为 S256，则将 code_verifier 进行 ascii 编码之后再进行哈希，然后将哈希之后的值进行 base64 编码
3. 向授权服务请求授权码，附带参数 code_challenge，code_challenge_method
4. 授权服务保存 code_challenge，code_challenge_method，返回授权码
5. app 向授权服务请求 access_token，附带参数 code, code_verifier
6. 授权服务重新生成 code_challenge 进行校验，之后返回 access_token
