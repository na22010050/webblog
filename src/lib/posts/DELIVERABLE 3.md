---
title: "📋DELIVERABLE 3 – WEBSITE"
date: "2025-05-27"
updated: "2025-30-05"
categories:
  - "Nguyễn Văn Ngọc Anh"
  - "Trịnh Phúc Lương"
coverImage: "/images/hp-15s-fq-gen-12_1.png"
coverWidth: 16
coverHeight: 9
excerpt: Bài viết trình bày tiến độ phát triển hệ thống quản lý phòng khám da liễu.
---

## 1. Tóm tắt tiến độ dự án

Dự án quản lý phòng khám da liễu đã đạt được nhiều cột mốc quan trọng trong quá trình phát triển. Dưới đây là tổng kết tiến độ hiện tại:

### Các tính năng chính đã được triển khai:
- Thiết lập cơ sở dữ liệu phân tán CockroachDB và cấu hình kết nối với Laravel.
- Xây dựng mô hình dữ liệu hoàn chỉnh cho hệ thống phòng khám.
- Tạo RESTful API và giao diện web tương ứng bằng Blade Template.
- Thực hiện phân quyền người dùng (admin, bác sĩ, bệnh nhân, nhân viên).
- Đảm bảo sao chép và phân mảnh dữ liệu được xử lý tự động qua CockroachDB.

### Những phần đã hoàn thành:
- Cấu hình và khởi tạo CockroachDB, bao gồm tạo các bảng chính.
- Tạo giao diện người dùng (admin, bác sĩ, bệnh nhân).
- Triển khai logic cho quản lý cuộc hẹn, hồ sơ bệnh án, thuốc và hóa đơn.
- Giao tiếp giữa Laravel và cơ sở dữ liệu hoạt động ổn định.

### Những phần đang được phát triển:
- Cải tiến trải nghiệm người dùng (UX/UI).
- Thêm xác thực JWT cho các API công khai.
- Tự động hóa triển khai bằng CI/CD.

### Vấn đề và cách giải quyết:
- **Vấn đề**: Một số hàm Laravel không tương thích trực tiếp với CockroachDB do giới hạn PostgreSQL.  
  **Giải pháp**: Tránh dùng foreign key và thay thế bằng logic xử lý trong Laravel.
- **Vấn đề**: Ký tự không hợp lệ trong file `.env` gây lỗi khi kết nối.  
  **Giải pháp**: Xóa và viết lại tay nội dung file để đảm bảo encoding chuẩn UTF-8.

## 2. 📸Demo hoạt động của hệ thống

Hệ thống đã được kiểm thử thành công với các tính năng chính như:
- Tạo lịch hẹn
- Tạo hồ sơ bệnh án
- Xuất hóa đơn
- Phân quyền người dùng

Các ảnh chụp màn hình về giao diện hệ thống và các truy vấn trên CockroachDB được đính kèm dưới đây:

![Giao diện tạo lịch hẹn](images/screenshot_appointment.jpeg)  
![Truy vấn CockroachDB](images/screenshot_cockroachdb_query.jpeg)

*Ghi chú*: Các ảnh chụp màn hình và video demo (nếu có) sẽ được đăng tải trên website/blog hoặc kênh YouTube.

## 3. Mã nguồn (Code Snippets)

Ví dụ: Tạo một cuộc hẹn – `AppointmentController.php`

```php
public function store(Request $request)
{
    $validated = $request->validate([
        'patient_id' => 'required|exists:patients,id',
        'doctor_id' => 'required|exists:doctors,id',
        'datetime' => 'required|date',
    ]);

    Appointment::create($validated);
    return response()->json(['message' => 'Appointment created successfully']);
}













```
## 4. Danh sách tính năng đã hoàn thành

Hệ thống quản lý phòng khám da liễu đã hoàn thành các tính năng cốt lõi sau, đáp ứng đầy đủ nhu cầu quản lý và vận hành:

- **Quản lý cuộc hẹn**:  
  - Tạo, xem, sửa, và xóa lịch hẹn giữa bệnh nhân và bác sĩ một cách dễ dàng.  
  - Đảm bảo lịch hẹn không bị trùng lặp nhờ kiểm tra trong Laravel.

- **Quản lý tài khoản**:  
  - Tạo, xem, sửa, và xóa tài khoản cho Admin và Bác sĩ.  
  - Giao diện quản lý tài khoản thân thiện, hỗ trợ phân quyền chi tiết.

- **Hồ sơ y tế**:  
  - Lưu trữ và quản lý thông tin khám chữa bệnh của từng bệnh nhân.  
  - Hỗ trợ bác sĩ ghi chú và cập nhật chẩn đoán.

- **Hóa đơn**:  
  - Tạo, xuất, và quản lý hóa đơn thanh toán.  
  - Hỗ trợ xuất hóa đơn dưới dạng PDF (đang phát triển thêm).

- **Phân quyền người dùng**:  
  - Tùy chỉnh quyền truy cập cho từng vai trò (Admin, Bác sĩ, Bệnh nhân, Nhân viên).  
  - Đảm bảo an toàn và bảo mật thông tin người dùng.

- **Hệ thống phân tán**:  
  - Tự động sao chép và phân mảnh dữ liệu thông qua **CockroachDB**.  
  - Đảm bảo tính sẵn sàng cao và khả năng phục hồi khi có sự cố.

![Giao diện quản lý tài khoản](images/screenshot_admin_management.jpeg)  
*Hình: Giao diện quản lý tài khoản Admin và Bác sĩ*

## 5. Kế hoạch tiếp theo

Để hoàn thiện hệ thống và chuẩn bị cho triển khai thực tế, các bước tiếp theo bao gồm:

### Các mục tiêu sắp tới:
- **Tối ưu hóa giao diện người dùng**:  
  - Cải thiện UX/UI để tăng trải nghiệm cho người dùng cuối, đặc biệt là giao diện bệnh nhân.  
  - Thêm các tính năng tương tác như thông báo trực tiếp.

- **Tự động hóa triển khai**:  
  - Tích hợp **CI/CD** thông qua GitHub Actions hoặc các công cụ tương tự.  
  - Đảm bảo quy trình triển khai nhanh chóng và không có lỗi.

- **Tài liệu hướng dẫn**:  
  - Viết tài liệu chi tiết cho người dùng và quản trị viên.  
  - Bao gồm hướng dẫn cấu hình CockroachDB và sử dụng API.

### Các vấn đề cần giải quyết:
- **Bảo mật dữ liệu**:  
  - Kích hoạt **CockroachDB secure mode** để bảo vệ dữ liệu trong môi trường thực tế.  
  - Thêm xác thực **JWT** cho các API công khai.

- **Hiệu năng hệ thống**:  
  - Kiểm tra khả năng xử lý với số lượng bản ghi lớn (stress test).  
  - Tối ưu hóa truy vấn SQL để tăng tốc độ phản hồi.

- **Logging chi tiết**:  
  - Thêm báo cáo lỗi và hệ thống giám sát (ví dụ: ELK Stack hoặc Sentry).  
  - Theo dõi hoạt động hệ thống để phát hiện và khắc phục sự cố nhanh chóng.

![Kế hoạch phát triển](images/screenshot_roadmap.jpeg)  
*Hình: Minh họa kế hoạch phát triển tiếp theo*