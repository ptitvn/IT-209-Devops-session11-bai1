# Java Spring Boot CI with Gradle

Dự án mẫu Java Spring Boot sử dụng Gradle kết hợp với GitHub Actions Workflow để tự động chạy Unit Test khi push lên nhánh `main`.

## Cấu trúc dự án
- **Java Version:** 17
- **Spring Boot:** 3.2.5
- **Build Tool:** Gradle Wrapper (`./gradlew`)
- **CI/CD Workflow:** `.github/workflows/ci.yml`

## Chạy kiểm thử cục bộ (Local Test)
```bash
# Windows
.\gradlew.bat test

# Linux / macOS
chmod +x gradlew
./gradlew test
```
