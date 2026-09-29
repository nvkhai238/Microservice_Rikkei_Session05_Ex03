# Session 05 - Bài 3: Pre-Filter ghi log request

Gateway đăng ký với Eureka và dùng URI `lb://CUSTOMER-SERVICE`, vì vậy không
phụ thuộc cổng thực tế của `customer-service`.

`LoggingFilter` là `GlobalFilter` có `@Component`; mỗi request sẽ ghi thời gian
và path theo mẫu `Incoming request at ... to: /api/v1/customers/1`, sau đó tiếp
tục chuỗi xử lý bằng `chain.filter(exchange)`.

## Thứ tự chạy

1. Eureka Server (`8761`).
2. `customer-service` có `spring.application.name=CUSTOMER-SERVICE`.
3. `api-gateway` (`8080`).

```bash
cd api-gateway
gradle bootRun
curl http://localhost:8080/api/v1/customers/1
```
