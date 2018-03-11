# jwt-boot-auth
secure spring-boot APIs with JWT

#### 请求hello接口，由于没有登录，会收到403错误
curl http://localhost:8080/hello

#### 注册一个新用户
curl -H "Content-Type: application/json" -X POST -d '{
    "username": "admin",
    "password": "password"
}' http://localhost:8080/users/signup

#### 登录，会返回token，在http header中，Authorization: Bearer 后面的部分就是token
curl -i -H "Content-Type: application/json" -X POST -d '{
    "username": "admin",
    "password": "password"
}' http://localhost:8080/login

#### 用登录成功后拿到的token再次请求hello接口

将请求中的XXXXXX替换成拿到的token,这次可以成功调用接口了

curl -H "Content-Type: application/json" \
-H "Authorization: Bearer XXXXXX" \
"http://localhost:8080/hello"
