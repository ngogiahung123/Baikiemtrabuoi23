# BÀI LÀM –(CHỦ ĐỀ QUẢN LÝ MODEL AI)

- **Mã đề:**
- **Họ tên: Ngô Gia Hưng**
- **Lớp: CNTT3**
- **Link repository: https://github.com/ngogiahung123/Baikiemtrabuoi23**
- **Hệ điều hành (Windows/macOS):**

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
pwd
ls -Force
mv .\tai_lieu_ban_giao.txt .\docs
mkdir backup
cp .\data\chi_phi_model_thang_11.xlsx .\backup
rm .\model_cache_01.tmp
cd .\logs
ls
cd ..

```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
    Directory: C:\Users\LEGION\CNTT\MiniPrjoect\starter-kit\quan-ly-model-ai


Mode                 LastWriteTime         Length Name                          
----                 -------------         ------ ----                          
d-----        10/11/2026   1:47 CH                backup                        
d-----        10/11/2026   1:44 CH                data                          
d-----        10/11/2026   1:46 CH                docs                          
d-----        10/11/2026   1:43 CH                evidence                      
d-----        10/11/2026   1:44 CH                logs                          
d-----        10/11/2026   1:41 CH                web                           
-a----        10/11/2026   1:41 CH             96 .env                          
-a----        10/11/2026   1:41 CH           2665 bai_lam.md                    


    Directory: C:\Users\LEGION\CNTT\MiniPrjoect\starter-kit\quan-ly-model-ai\bac
    kup


Mode                 LastWriteTime         Length Name                          
----                 -------------         ------ ----                          
-a----        10/11/2026   1:41 CH           5815 chi_phi_model_thang_11.xlsx   


    Directory: C:\Users\LEGION\CNTT\MiniPrjoect\starter-kit\quan-ly-model-ai\dat
    a


Mode                 LastWriteTime         Length Name                          
----                 -------------         ------ ----                          
-a----        10/11/2026   1:41 CH           5815 chi_phi_model_thang_11.xlsx   


    Directory: C:\Users\LEGION\CNTT\MiniPrjoect\starter-kit\quan-ly-model-ai\doc
    s


Mode                 LastWriteTime         Length Name                          
----                 -------------         ------ ----                          
-a----        10/11/2026   1:41 CH            204 tai_lieu_ban_giao.txt         


    Directory: C:\Users\LEGION\CNTT\MiniPrjoect\starter-kit\quan-ly-model-ai\log
    s


Mode                 LastWriteTime         Length Name                          
----                 -------------         ------ ----                          
-a----        10/11/2026   1:41 CH           1234 inference.log                 


    Directory: C:\Users\LEGION\CNTT\MiniPrjoect\starter-kit\quan-ly-model-ai\web


Mode                 LastWriteTime         Length Name                          
----                 -------------         ------ ----                          
d-----        10/11/2026   1:41 CH                images                        
-a----        10/11/2026   1:41 CH            644 app.js                        
-a----        10/11/2026   1:41 CH            567 index.html                    
-a----        10/11/2026   1:41 CH            460 style.css                     


    Directory: C:\Users\LEGION\CNTT\MiniPrjoect\starter-kit\quan-ly-model-ai\web
    \images


Mode                 LastWriteTime         Length Name                          
----                 -------------         ------ ----                          
-a----        10/11/2026   1:41 CH            339 logo-ai-hub.png               



```

## 4.3. Lọc log vận hành Model AI

### a) Lệnh lọc các dòng ERROR

```shell
Get-Content .\logs\inference.log | Select-String "ERROR" > .\logs\loi_model.txt
Get-Content .\logs\loi_model.txt -head 2
```

### 2 dòng đầu tiên trong logs/loi_model.txt

```text
2026-11-10 08:27:45 ERROR POST /v1/chat/completions model=CLAUDE-35
2026-11-10 08:31:12 ERROR POST /v1/audio/transcriptions model=WHISPER-V3
```

### b) Lệnh đếm số dòng WARNING và kết quả

```shell
(Get-Content .\logs\inference.log | Select-String "WARNING").count
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
=== BAO CAO VAN HANH MODEL AI ===

2026-11-10 08:09:18 WARNING POST /v1/embeddings model=LLAMA-2-OLD
2026-11-10 08:16:05 WARNING GET /v1/fine-tune/jobs-legacy
2026-11-10 08:38:29 WARNING GET /images/model-card-v1.png
2026-11-10 09:01:44 WARNING POST /v1/completions model=DAVINCI-002
2026-11-10 09:14:02 WARNING GET /v1/quota/expired-key




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 
```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, hình ảnh (`![Alt](path)`), mô tả có **in đậm**, _in nghiêng_ và `inline code`, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | -------------------------- | --------------------------- | -------------- |
| 1   | Network  |              logo.png               |      Điền lại đúng đường dẫn đến ảnh          |
| 2   |          Console                  |        app.js:18 Uncaught ReferenceError: hienThiBangModelA is not defined                     |     Điền lại tên gọi đúng để xuất hiện bảng           |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:Tôi là sinh viên năm nhất chưa biết cách fix lỗi**
- **Expected: Bây tôi muốn xuất hiện bảng giao diện hiển thị**
- **Actual: Trang wed hiện tại chưa hiển thị cái j và tôi phát hiện lỗiapp.js:18 Uncaught ReferenceError: hienThiBangModelA is not defined trong Console**
- **Log: app.js:18 Uncaught ReferenceError: hienThiBangModelA is not defined**

### Câu tìm kiếm Google

```text
site:stackoverflow.com "Uncaught ReferenceError"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/chi_phi_model_thang_11.xlsx`, không cần ghi vào đây.
