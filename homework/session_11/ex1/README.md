# Bài 1: Khởi tạo Workflow chạy Unit Test tự động cho Java Spring Boot với Gradle

## 1. Mục tiêu
- Khởi tạo tệp kịch bản GitHub Actions Workflow cho dự án Java Spring Boot sử dụng Gradle.
- Cấu hình môi trường Java JDK 17 (Temurin) và tự động chạy bài kiểm thử JUnit Test bằng Gradle Wrapper (`./gradlew test`).

## 2. Cấu trúc thư mục dự án
```text
bai1/
├── .github/
│   └── workflows/
│       └── ci.yml
├── gradle/
│   └── wrapper/
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── homework/
│   └── session_11/
│       └── ex1/
│           ├── ci.yml
│           └── README.md
├── src/
│   ├── main/
│   │   ├── java/com/example/demo/
│   │   │   ├── DemoApplication.java
│   │   │   └── controller/HelloController.java
│   │   └── resources/application.properties
│   └── test/
│       └── java/com/example/demo/
│           ├── DemoApplicationTests.java
│           └── HelloControllerTest.java
├── .gitignore
├── build.gradle
├── gradlew
├── gradlew.bat
├── README.md
└── settings.gradle
```

## 3. Nội dung Workflow CI (`.github/workflows/ci.yml`)
```yaml
name: Java Spring Boot CI (Gradle)

on:
  push:
    branches: [ "main" ]

jobs:
  test:
    name: Run Unit Tests
    runs-on: ubuntu-latest

    steps:
      - name: Checkout mã nguồn
        uses: actions/checkout@v5

      - name: Thiết lập môi trường Java JDK 17
        uses: actions/setup-java@v5
        with:
          java-version: '17'
          distribution: 'temurin'

      - name: Cấp quyền cho Gradle Wrapper
        run: chmod +x gradlew

      - name: Thực thi JUnit Test với Gradle
        run: ./gradlew test
```

## 4. Các bước thực hiện
1. **Khởi tạo dự án Spring Boot Gradle** với Java 17 và các dependencies cần thiết (`spring-boot-starter-web`, `spring-boot-starter-test`).
2. **Viết Unit Test** với Spring Boot Test & WebMvcTest (`DemoApplicationTests`, `HelloControllerTest`).
3. **Cấu hình Gradle Wrapper** (`gradlew`, `gradlew.bat`, `gradle-wrapper.jar`).
4. **Khởi tạo Workflow** `.github/workflows/ci.yml` kích hoạt khi push lên branch `main`.
5. **Khởi tạo Git Repository** và đẩy mã nguồn lên GitHub repository: `https://github.com/ptitvn/IT-209-Devops-session11-bai1.git`.
6. **Kiểm tra GitHub Actions**: Job `Run Unit Tests` được kích hoạt tự động và hoàn thành thành công (tích xanh).
