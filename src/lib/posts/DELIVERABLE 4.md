---
title: "DELIVERABLE 4 – WEBSITE"
date: "2025-06-02"
updated: "2025-06-01"
categories:
  - "Nguyễn Văn Ngọc Anh"
  - "Trịnh Phúc Lương"
coverImage: "/images/de4.jpg"
coverWidth: 20
coverHeight: 18
excerpt:  Báo cáo đánh giá hệ thống quản lý phòng khám da liễu sử dụng CockroachDB trong môn Ứng dụng Phân tán.
---

---

# Đánh giá hệ thống quản lý phòng khám da liễu

Hệ thống quản lý phòng khám da liễu được xây dựng trên nền tảng Laravel và CockroachDB, triển khai theo kiến trúc phân tán. Dưới đây là báo cáo tổng hợp đánh giá hệ thống theo các tiêu chí của Deliverable 4 trong môn học "Ứng dụng Phân tán".

---

## 1. Đánh giá theo tiêu chí bắt buộc

### 1.1. Fault Tolerance (Khả năng chịu lỗi)

CockroachDB cung cấp khả năng chịu lỗi mặc định thông qua cơ chế replication và bầu chọn leader theo giao thức Raft. Khi một node trong cluster gặp sự cố, hệ thống vẫn tiếp tục hoạt động nhờ vào quorum từ các replica còn lại. Laravel vẫn có thể thực hiện các truy vấn khi một node bị ngắt, với điều kiện cụm vẫn còn quorum.

**Kết luận**: Đạt.

### 1.2. Distributed Communication (Giao tiếp phân tán)

Trong quá trình phát triển, ứng dụng Laravel được cấu hình để giao tiếp với cụm CockroachDB thông qua giao thức PostgreSQL (TCP/IP). Hệ thống đã được thử nghiệm với các node CockroachDB chạy trên nhiều cổng, mô phỏng các máy khác nhau trong mạng cục bộ. Việc truy vấn được phân phối tới các node trong cụm xác nhận khả năng giao tiếp qua mạng giữa các tiến trình.

**Kết luận**: Đạt.

### 1.3. Sharding hoặc Replication

CockroachDB tự động thực hiện sharding dữ liệu theo khóa chính và replication theo từng range. Mỗi range có ba bản sao và được quản lý bằng thuật toán Raft để đảm bảo tính nhất quán mạnh. Người dùng không cần can thiệp thủ công để chia shard hoặc replicate dữ liệu.

**Kết luận**: Đạt.

### 1.4. Simple Monitoring / Logging

Hệ thống sử dụng Laravel để ghi log các hành vi ứng dụng vào `storage/logs/laravel.log`. Ngoài ra, CockroachDB cung cấp giao diện Admin UI tại cổng 8080 để theo dõi số lượng node, trạng thái replication, thời gian phản hồi và các truy vấn chậm.

**Kết luận**: Đạt.

### 1.5. Basic Stress Test
Đã tiến hành kiểm thử tải bằng cách gửi hàng trăm yêu cầu POST và GET tới các route như `/appointments`, `/doctors`, và `/invoices`. Công cụ sử dụng gồm Apache Bench và Postman Runner. Hệ thống phản hồi ổn định, không ghi nhận lỗi 500, thời gian phản hồi trung bình ở mức chấp nhận được.

**Kết luận**: Đạt.

---

## 2. Đánh giá theo tiêu chí tùy chọn

### 2.1. System Recovery (Khả năng tự khôi phục)

Khi một node trong cụm CockroachDB bị tắt, các node còn lại vẫn tiếp tục hoạt động. Sau khi node bị lỗi được khởi động lại, hệ thống tự động đồng bộ dữ liệu và tái gia nhập cluster. Cơ chế này được xác thực trong quá trình thử nghiệm.

**Kết luận**: Đạt.

### 2.2. Leader Election

CockroachDB sử dụng giao thức Raft, cho phép tự động bầu chọn leader trong các range khi leader hiện tại gặp sự cố. Quá trình bầu lại leader diễn ra tự động và không ảnh hưởng đến hoạt động của hệ thống ở tầng ứng dụng.

**Kết luận**: Đạt.

### 2.3. Load Balancing

Hệ thống chưa có cấu hình cụ thể về phân phối truy vấn từ Laravel tới các node theo chiến lược cân bằng tải rõ ràng. Việc này có thể được mở rộng trong các bước tiếp theo bằng cách sử dụng proxy layer hoặc DNS round-robin.

**Kết luận**: Chưa đạt.

### 2.4. Consistency Guarantees

CockroachDB đảm bảo tính nhất quán mạnh (strong consistency) thông qua cơ chế ghi đồng thuận giữa các bản sao trong range. Hệ thống đảm bảo rằng mọi dữ liệu ghi đều tuân theo nguyên tắc serializability.

**Kết luận**: Đạt.

### 2.5. Security Features

Hệ thống hiện đang chạy CockroachDB ở chế độ `--insecure`. Chưa có mã hóa kết nối hoặc xác thực liên cụm. Laravel có sử dụng xác thực người dùng nội bộ, tuy nhiên chưa áp dụng bảo mật mạng tổng thể.

**Kết luận**: Chưa đạt.

---

## 3. Tổng kết

Hệ thống quản lý phòng khám da liễu đã được xây dựng thành công trên nền tảng Laravel và CockroachDB, với nhiều tiêu chí phân tán được đáp ứng. Hệ thống thể hiện rõ đặc điểm của một hệ thống phân tán thông qua khả năng chịu lỗi, cơ chế sao chép dữ liệu, giao tiếp mạng, và phục hồi sau lỗi.

Một số tiêu chí tùy chọn cũng đã được tích hợp như leader election và system recovery. Các phần chưa hoàn thiện như bảo mật mạng hoặc cân bằng tải sẽ được nghiên cứu và bổ sung trong các giai đoạn tiếp theo.


