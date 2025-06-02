---
title: "ÔN TẬP CUỐI KỲ"
date: "2025-04-11"
updated: "2025-15-05"
categories:
  - "Nguyễn Văn Ngọc Anh"
coverImage: "/images/ad7c897fda40ccb96276b1a566441503.jpg"
coverWidth: 16
coverHeight: 9
excerpt: Bài ôn cuối kỳ.
---
# Tổng hợp kiến thức Hệ phân tán

## Câu 1: Hệ thống tập trung, phân tán, phi tập trung khác nhau như thế nào?

### Hệ thống tập trung (Centralized)
- Mọi xử lý, lưu trữ và điều phối nằm tại một máy chủ trung tâm.
- Người dùng phải kết nối đến server này để sử dụng dịch vụ.
- **Ví dụ:** Hệ thống ngân hàng truyền thống, website sử dụng một server duy nhất.

### Hệ thống phân tán (Distributed)
- Gồm nhiều máy tính độc lập, kết nối qua mạng, phối hợp xử lý chung.
- Các node có thể cùng chia sẻ dữ liệu và tài nguyên.
- **Ví dụ:** Google Search, Netflix, hệ thống lưu trữ HDFS.

### Hệ thống phi tập trung (Decentralized)
- Không có máy chủ trung tâm; các node đều ngang hàng, tự xử lý và ra quyết định.
- Thường dùng thuật toán đồng thuận để hoạt động đồng bộ.
- **Ví dụ:** Blockchain (Bitcoin, Ethereum), mạng BitTorrent.

### Khác biệt chính:
- **Tập trung:** Có một điểm điều phối duy nhất.
- **Phân tán:** Nhiều node phối hợp nhưng có thể có nút chủ.
- **Phi tập trung:** Không có nút điều phối, các node độc lập hoặc đồng thuận.

---

## Câu 2: Các đặc tính của hệ phân tán

1. **Tính minh bạch (Transparency):** Che giấu sự phân tán khỏi người dùng.
2. **Tính mở rộng (Scalability):** Mở rộng về kích thước, địa lý, quản lý.
3. **Tính chịu lỗi (Fault Tolerance):** Hoạt động ổn định khi có lỗi xảy ra.
4. **Đồng thời (Concurrency):** Nhiều tiến trình cùng chạy và truy cập tài nguyên.
5. **Không có đồng hồ toàn cục:** Dùng logic clock (Lamport, vector clock).
6. **Tính độc lập (Autonomy):** Mỗi node có thể tự quản lý tài nguyên riêng.
7. **Khó duy trì trạng thái toàn cục:** Cần thuật toán đồng thuận.

---

## Câu 3: Vai trò và sự cố nút chủ (Master Node)

- **Vai trò:** Quản lý, điều phối node khác; chia việc, quản lý metadata.
- **Ví dụ:** HDFS - NameNode là nút chủ.
- **Sự cố:** Hệ thống có thể ngừng nếu không có dự phòng → cần failover.

---

## Câu 4: Gossip Protocol

- **Hiệu quả:** Giảm tải so với broadcast.
- **Chịu lỗi tốt:** Không phụ thuộc nút trung tâm.
- **Tự động lan truyền:** Thông tin tự động được nhân rộng.
- **Phù hợp:** Mạng phân tán lớn.

---

## Câu 5: Yếu tố cốt lõi của hệ phân tán

- Nhiều node độc lập (vật lý hoặc ảo).
- Giao tiếp qua mạng.
- Không có đồng hồ chung.
- Đồng thời.
- Chia sẻ tài nguyên.
- Xử lý lỗi.

---

## Câu 6: Lý do sử dụng hệ phân tán

- Hiệu năng cao.
- Tăng tính sẵn sàng.
- Mở rộng linh hoạt.
- Tiết kiệm chi phí.
- Phân bố địa lý.
- Tính mô-đun.

---

## Câu 7: Định nghĩa hệ phân tán

Hệ phân tán là tập hợp các máy tính độc lập, kết nối qua mạng để phối hợp thực hiện nhiệm vụ chung, người dùng cảm giác như một hệ thống duy nhất.

---

## Câu 8: Hình ảnh cần đăng blog

- Đồng bộ thời gian: Cristian, Berkeley, RBS.
- Đồng hồ logic: Lamport.
- Thuật toán bầu chọn: Bully, Ring.
- Gợi ý: Dùng draw.io hoặc chụp slide bài giảng.

---

## Câu 9: Kỹ thuật và mô hình lập trình phân tán

| Kiểu lập trình     | Kỹ thuật hỗ trợ               |
|--------------------|-------------------------------|
| Thủ tục            | RPC, gRPC                     |
| Hướng đối tượng    | Java RMI, CORBA               |
| Web (RESTful/SOAP) | HTTP, REST API, SOAP, GraphQL |

---

## Câu 10: So sánh Tiến trình, Luồng và Tiến trình nhẹ

| Thành phần     | Ưu điểm                      | Nhược điểm                                |
|----------------|------------------------------|--------------------------------------------|
| Tiến trình     | An toàn, tách biệt           | Switching tốn tài nguyên                   |
| Luồng          | Nhẹ, chia sẻ tài nguyên      | Một lỗi luồng ảnh hưởng toàn tiến trình    |
| Tiến trình nhẹ | Linh hoạt giữa thread/process | Phụ thuộc hệ điều hành                     |

**Hệ thống call bị chặn:**  
- Tiến trình: dừng toàn bộ.  
- Luồng: chỉ luồng bị chặn.  
- Tiến trình nhẹ: tùy hệ điều hành.

---

## Câu 11: Mô hình Client-Server

- **Client:** Gửi request.
- **Server:** Xử lý và gửi response.
- **Ví dụ:** Trình duyệt gửi yêu cầu đến web server.

---

## Câu 12: RPC là gì?

- Gọi hàm từ xa như hàm cục bộ.
- Gồm: marshalling, truyền qua mạng, unmarshalling.
- **Ưu điểm:** Ẩn chi tiết mạng, đơn giản hóa lập trình.

---

## Câu 13: Mô hình phân tầng và Messaging

- **Mục tiêu phân tầng:** Dễ bảo trì, tách biệt chức năng.
- **Messaging bền vững:** Đảm bảo tin nhắn đến đúng, đủ, đúng thứ tự.

---

## Câu 14: Sharding là gì?

- Chia dữ liệu thành nhiều phần nhỏ, phân phối qua nhiều máy.
- **Mục tiêu:** Tăng hiệu năng, giảm tải.

---

## Câu 15: Gói luồng (Thread Package)

- Quản lý luồng: tạo, hủy, đồng bộ, giao tiếp.
- **Ví dụ:** Pthreads (C), `java.util.concurrent`, OpenMP.

---

## Câu 16: Luồng người dùng vs. Luồng nhân

| Loại             | Đặc điểm chính                                               |
|------------------|--------------------------------------------------------------|
| Luồng người dùng | Quản lý bởi thư viện, không tận dụng đa nhân nếu OS không hỗ trợ |
| Luồng kiểu nhân  | Quản lý bởi OS, hỗ trợ đa nhân, chi phí cao hơn             |
| Hybrid           | Kết hợp cả hai loại trên                                     |

---

## Câu 17: Các hàm trong RPC

| Thành phần     | Vai trò                                          |
|----------------|--------------------------------------------------|
| `register()`   | Đăng ký hàm từ xa                                |
| `call()`       | Gửi yêu cầu và nhận kết quả                      |
| `bind()`       | Liên kết tên dịch vụ với địa chỉ mạng            |
| Stub (client)  | Đại diện hàm, đóng gói dữ liệu                   |
| Stub (server)  | Giải mã dữ liệu, gọi hàm thực                    |

---

## Câu 18: Định nghĩa tiến trình, luồng, multithread client/server

- **Tiến trình:** Đơn vị thực thi độc lập.
- **Luồng:** Đơn vị nhỏ hơn, chia sẻ bộ nhớ.
- **Multithread Client/Server:** Gửi và xử lý nhiều yêu cầu đồng thời.

---

## Câu 19: MapReduce trong hệ phân tán

- **Map:** Sinh ra cặp key–value.
- **Reduce:** Tổng hợp theo key.
- **Ứng dụng:** Xử lý dữ liệu lớn (VD: Hadoop).

---

## Câu 20: Ảo hóa (Virtualization)

- Cho phép chạy nhiều máy ảo trên một phần cứng.
- **Mục đích:** Tiết kiệm, linh hoạt, cô lập lỗi, tối ưu tài nguyên.

---

## Câu 21: Kiến trúc Server đa luồng

| Kiến trúc           | Mô tả ngắn                                      |
|---------------------|-------------------------------------------------|
| Thread-per-request  | Mỗi request một luồng                           |
| Thread pool         | Dùng sẵn nhóm luồng                             |
| Event-driven (async)| Ít luồng, xử lý bất đồng bộ nhiều yêu cầu       |

---

## Câu 22: Các hướng cài đặt luồng

| Hướng tiếp cận       | Mô tả                                                  |
|----------------------|--------------------------------------------------------|
| User-level thread     | Nhanh, không tận dụng đa lõi nếu OS không hỗ trợ      |
| Kernel-level thread   | Hệ điều hành quản lý, đa lõi, tốn tài nguyên          |
| Hybrid model          | Kết hợp, tận dụng ưu điểm cả hai loại trên            |

---

## Câu 23: DHT, Consistent Hashing và Finger Table

- **DHT:** Bảng băm phân tán.
- **Consistent Hashing:** Hash vòng, ít di chuyển khi thay node.
- **Finger Table:** Tìm kiếm log(N) bước trong Chord.

---

## Câu 24: Không gian phẳng và định danh

- **Không gian phẳng:** Tên không chứa vị trí, cần ánh xạ tên → địa chỉ.
- **Định danh:** Tên duy nhất đại diện đối tượng.

---

## Câu 25: Đồng bộ hóa đồng hồ logic

- **Vấn đề:** Không thể dùng đồng hồ vật lý chung.
- **Mục đích:** Xác định thứ tự sự kiện.
- **Thuật toán:** Cristian, Berkeley, RBS, Lamport, Vector Clock.

---

## Câu 26: Đồng hồ Lamport

- **Giải quyết:** Xác định thứ tự sự kiện trong hệ phân tán.
- **Quy tắc:**
  - Nội bộ: `L = L + 1`
  - Gửi: `L = L + 1`, gửi theo giá trị L
  - Nhận: `L = max(L, L') + 1`

> **Lưu ý:** Lamport chỉ đảm bảo thứ tự tổng quát, không đảm bảo nhân quả.

---

## Câu 27: Bài tập Lamport Clock

- Gán timestamp cho sự kiện.
- So sánh timestamp.
- Vẽ biểu đồ sự kiện và timestamp.

---

## Câu 28: So sánh NTP và PTP – Cách tính thời gian

| Đặc điểm               | **NTP** (Network Time Protocol)                                    | **PTP** (Precision Time Protocol)                                |
|------------------------|--------------------------------------------------------------------|------------------------------------------------------------------|
| **Mức độ chính xác**   | Đến **mili giây**                                                  | Đến **nano giây**                                               |
| **Ứng dụng**           | Đồng bộ qua mạng Internet                                          | Hệ thống thời gian thực, mạng LAN                               |
| **Cách đo thời gian**  | Dựa trên 4 mốc:<br>1. Gửi yêu cầu (T1)<br>2. Server nhận (T2)<br>3. Server gửi lại (T3)<br>4. Client nhận (T4) | Dùng phần cứng chuyên dụng (timestamp hardware) để đo thời gian chính xác |
| **Cách điều chỉnh**    | Tính toán độ trễ → hiệu chỉnh đồng hồ                             | Tính chính xác thời điểm gửi – nhận → hiệu chỉnh chính xác hơn  |

** Ghi nhớ**:  
- **NTP**: phổ biến, đơn giản – dùng cho **Internet**.  
- **PTP**: chính xác cao – dùng trong **công nghiệp, tài chính, hệ thống nhúng**.

---

### Câu 29: Ôn lại Python cơ bản

- **Biến & kiểu dữ liệu**: `int`, `float`, `str`, `list`, `dict`, `set`.
- **Câu lệnh điều kiện**: `if`, `elif`, `else`.
- **Vòng lặp**: `for`, `while`, `break`, `continue`.
- **Hàm**: `def`, tham số, giá trị trả về.
- **List comprehension**: gọn, hiệu quả.
- **Xử lý file**: `open()`, `read()`, `write()`.
- **Try–except**: xử lý ngoại lệ.
- **Import thư viện**: `import math`, `import random`, `import datetime`.
