# Spring Boot REFRESH TOKEN CUSTOM

계정 등록
```
curl http://localhost:8080/register -d '{ "username" : "test", "password" : "test", "role" : "ROLE_ADMIN" }' -H "Accept: application/json" -H "Content-Type: application/json" | json_pp
```

access token 발급:
```
curl localhost:8080/authenticate -d '{ "username" : "test", "password" : "test", "role" : "ROLE_ADMIN" }' -H "Accept: application/json" -H "Content-Type: application/json" | json_pp
```
응답 예시

```
{
    "token": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJ0ZXN0IiwiaXNBZG1pbiI6dHJ1ZSwiZXhwIjoxNjE4MjI0MDE2LCJpYXQiOjE2MTgyMjQwMTZ9.tGQRwqW-Eo-51maw9VG6YsuSZdMbBdhbD9ofvUXVVqH_F9kNHZoKokx4ltqIDAhnkwc9sZJfZe0zznewL60Yxg"
}
```

리소스 요청
```
curl localhost:8080/helloadmin -H "Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJ0ZXN0IiwiaXNBZG1pbiI6dHJ1ZSwiZXhwIjoxNjE4MjI0MDE2LCJpYXQiOjE2MTgyMjQwMTZ9.tGQRwqW-Eo-51maw9VG6YsuSZdMbBdhbD9ofvUXVVqH_F9kNHZoKokx4ltqIDAhnkwc9sZJfZe0zznewL60Yxg" | json_pp
```

refresh token:

```
curl localhost:8080/refreshtoken -H "Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJ0ZXN0IiwiaXNBZG1pbiI6dHJ1ZSwiZXhwIjoxNjE4MjI0MDE2LCJpYXQiOjE2MTgyMjQwMTZ9.tGQRwqW-Eo-51maw9VG6YsuSZdMbBdhbD9ofvUXVVqH_F9kNHZoKokx4ltqIDAhnkwc9sZJfZe0zznewL60Yxg" -H "isRefreshToken: true" | json_pp
```

docker :
```
docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root --name mysql-temp mysql:latest --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```
# reference
- https://www.javainuse.com/webseries/spring-security-jwt/chap7