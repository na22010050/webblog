---
title: "Tổng quan về ứng dụng phân tán"
date: "2025-10-26"
updated: "2025-4-30"
categories:
  - "Nguyễn Văn Ngọc Anh"
coverImage: "/images/anh1.jpg"
coverWidth: 16
coverHeight: 9
excerpt: check.
---
## 1. Hệ thống phân tán là gì?

Hệ thống phân tán (Distributed System) là tập hợp nhiều máy tính độc lập, được kết nối qua mạng và phối hợp để cùng thực hiện một nhiệm vụ. Mục tiêu là tạo ra một môi trường hoạt động như một hệ thống duy nhất đối với người dùng cuối.

---

## 2. Các ứng dụng của hệ thống phân tán

- **Dịch vụ web và internet**: Google, Amazon, Facebook, Twitter.
- **Điện toán đám mây**: AWS, Microsoft Azure, Google Cloud Platform.
- **Thương mại điện tử**: Shopee, Lazada, Tiki sử dụng hệ thống phân tán để đảm bảo hiệu suất cao và khả năng mở rộng.
- **Hệ thống tài chính**: Giao dịch chứng khoán, ngân hàng trực tuyến.
- **Giải trí trực tuyến**: Netflix, YouTube.

---

## 3. Các khái niệm chính của hệ thống phân tán

### 3.1 Giải thích các thuật ngữ

- **Scalability**: Khả năng mở rộng hệ thống để xử lý nhiều tải hơn.
- **Fault Tolerance**: Khả năng tiếp tục hoạt động khi một phần hệ thống gặp lỗi.
- **Availability**: Khả năng hệ thống sẵn sàng phục vụ bất kỳ lúc nào.
- **Transparency**: Người dùng không thấy sự phức tạp bên trong (ví dụ: vị trí, lỗi, di chuyển...).
- **Concurrency**: Cho phép nhiều tiến trình hoạt động đồng thời mà không xung đột.
- **Parallelism**: Thực hiện nhiều tác vụ cùng lúc để tối ưu hiệu suất.
- **Openness**: Hệ thống có thể tương thích và tích hợp với các thành phần khác.
- **Vertical Scaling**: Nâng cấp phần cứng cho máy chủ (thêm CPU, RAM).
- **Horizontal Scaling**: Thêm nhiều máy chủ mới vào hệ thống.
- **Load Balancer**: Phân phối tải đều giữa các máy chủ trong hệ thống.
- **Replication**: Sao chép dữ liệu sang nhiều nút để tăng độ tin cậy và hiệu suất.

### 3.2 Ví dụ minh họa

**Ví dụ: Amazon Web Services (AWS)**

- **Scalability**: Cho phép thêm/giảm máy ảo tự động qua auto-scaling group.
- **Fault Tolerance**: Nếu một vùng bị lỗi, vùng khác vẫn hoạt động.
- **Load Balancer**: ELB phân phối lưu lượng truy cập giữa các máy chủ.
- **Replication**: S3 và RDS sử dụng replication để đảm bảo an toàn dữ liệu.
- **Horizontal Scaling**: Thêm nhiều EC2 instance để tăng tải.
- **Transparency**: Người dùng không biết đang truy cập máy chủ nào.

---

## 4. Kiến trúc của hệ thống phân tán

### 4.1 Các mô hình kiến trúc phổ biến

- **Client-Server**: Máy khách gửi yêu cầu, máy chủ xử lý.
- **Peer-to-Peer (P2P)**: Các nút trong mạng bình đẳng, chia sẻ tài nguyên.
- **Multi-tier Architecture (3-tier)**: Gồm frontend, logic trung gian và database.
- **Microservices Architecture**: Hệ thống gồm nhiều dịch vụ nhỏ, độc lập.
- **Service-Oriented Architecture (SOA)**: Các thành phần giao tiếp qua giao thức mạng chuẩn (thường là HTTP, SOAP).

### 4.2 Ví dụ

**Microservices Architecture trong Netflix:**

- Mỗi chức năng (gợi ý, thanh toán, phát video) là một dịch vụ riêng.
- Dễ triển khai độc lập và mở rộng theo nhu cầu.
- Các dịch vụ giao tiếp qua REST hoặc gRPC.

---


