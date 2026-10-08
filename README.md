# Bài 3: Đóng gói trang Web HTML tĩnh với Docker & Nginx Alpine

## 1. Giới thiệu
Dự án sử dụng Nginx Alpine để đóng gói và phục vụ một trang HTML tĩnh siêu gọn nhẹ thông qua Docker.

## 2. Cấu trúc thư mục
```
├── Dockerfile
├── index.html
└── README.md
```

## 3. Nội dung các tệp tin

### `index.html`
```html
<h1>Hello Docker Session 09!</h1>
```

### `Dockerfile`
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

## 4. Hướng dẫn Build và Chạy Container

### Bước 1: Build Docker Image
Chạy lệnh sau tại thư mục chứa `Dockerfile`:
```bash
docker build -t my-html-app:v1 .
```

### Bước 2: Chạy Container
Khởi chạy container trên cổng `8081` của máy chủ (host) ánh xạ vào cổng `80` của container:
```bash
docker run -d -p 8081:80 --name html-app my-html-app:v1
```

### Bước 3: Kiểm tra kết quả
Sử dụng `curl` hoặc mở trình duyệt web truy cập `http://localhost:8081`:
```bash
curl http://localhost:8081
```

**Kết quả mong đợi:**
```html
<h1>Hello Docker Session 09!</h1>
```

## 5. Dọn dẹp tài nguyên (khi cần)
Dừng và xóa container:
```bash
docker stop html-app
docker rm html-app
```
Xóa image:
```bash
docker rmi my-html-app:v1
```
