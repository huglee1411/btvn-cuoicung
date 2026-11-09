

<![endif]-->

# BÀI LÀM – (ĐỀ LUYỆN TẬP SỐ 02)  
  
- **Mã đề:** 02  
- **Họ tên:**  lê gia hưng
- **Lớp:**  cntt3
- **Link repository:**  https://github.com/huglee1411/btvn-cuoicung
- **Hệ điều hành (Windows/macOS):**  windows
  
## 4.2. Thao tác máy tính cơ bản bằng CLI  
  
### Các lệnh đã chạy  
  
```shell  
Get-Location
Get-ChildItem -Force
Move-Item bien_ban_ban_giao.txt docs/
New-Item -ItemType Directory -Name backup
Copy-Item data/ban_ve_thang_11.xlsx backup/
Remove-Item *.tmp
cd logs
Get-ChildItem
cd .. 
Get-ChildItem -Force
```  
  
### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)  
  
```text  
  Directory: C:\Users\LEGION
    5\Downloads\Luyen_Tap_11_9\starter-kit\rap-phim-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/10/2026  12:58 AM                backup
d-----        11/10/2026  12:39 AM                data
d-----        11/10/2026  12:58 AM                docs
d-r---         11/9/2026   3:15 PM                evidence
d-----        11/10/2026  12:40 AM                logs
d-----         11/9/2026   3:08 PM                web
-a----         11/9/2026   3:08 PM             82 .env
-a----         11/9/2026   3:08 PM           2611 bai_lam.md
-a-h--        11/10/2026  12:40 AM            162 ~$ai_lam.md

  
```  
  
## 4.3. Lọc log truy cập website  
  
### a) Lệnh lọc các dòng ERROR  
  
```shell  
Get-Content logs/server.log | Select-String "ERROR" | Out-File logs/loi_error.txt
  
```  
  
### 2 dòng đầu tiên trong logs/loi_error.txt  
  
```text  

  2026-11-01 09:25:40 ERROR POST /api/mua-ve
2026-11-01 09:29:11 ERROR POST /api/thanh-toan-qr
```  
  
### b) Lệnh đếm số dòng WARNING và kết quả  
  
```shell  
  
  (Get-Content logs/server.log | Select-String "WARNING").Count
```  
  
```text  
5
  
```  
  
## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)  
  
### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)  
  
```shell  
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\tong_hop.ps1
  
```  
  
### Nội dung file logs/tong_hop.txt  
  
```text  
# Script: tong_hop.ps1
# Tac gia: Le Gia Hung
# Ngay tao: 2026-11-10
Write-Host "Dang tao bao cao..."
"=== BAO CAO SU CO WEBSITE ===" > logs/tong_hop.txt
Get-Content logs/server.log | Select-String "WARNING" >> logs/tong_hop.txt
(Get-Content logs/server.log | Select-String "ERROR").Count >> logs/tong_hop.txt
Write-Host "Hoan thanh!"
  
```  
  
## 4.5. README.md và bảo vệ thông tin bí mật  
  
> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.  
  
- [x] README.md: Heading 1, mô tả có **in đậm** và _in nghiêng_, bảng, code block, task list, blockquote  
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)  
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)  
  
## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi  
  
### Bảng lỗi  
  
| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |  
| --- | -------------------------- | --------------------------- | -------------- |  
| 1  |network  | lỗi ảnh |sửa lại tên ảnh |  
| 2  | console | thiếu chữ | thêm mỗi từ vẽ |  
  
> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).  
  
### Báo cáo lỗi gửi trưởng nhóm  
  
- **Context:**  Tôi là sinh viên năm nhất chưa fix lỗi hiển thị dữ liệu của web bao giờ
- **Expected:**  Bây giờ trang web xem phim của tôi muốn có đủ dữ liệu ở bảng hiển thị giao diện
- **Actual:**  Dữ liệu trên trang web không có gì và tôi vào tab console thấy thông báo lỗi app.js:18 Uncaught ReferenceError: hienThiBangGia is not
- **Log:**  app.js:18 Uncaught ReferenceError: hienThiBangGia is not
  
### Câu tìm kiếm Google  
  
```text  
site:[stackoverflow.com](http://stackoverflow.com) "Uncaught ReferenceError"
  
```  
  
## 4.7. Excel  
  
> Phần Excel được chấm trực tiếp trên file `data/ban_ve_thang_11.xlsx`, không cần ghi vào đây.   
