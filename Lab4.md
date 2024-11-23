# 1. Đăng nhập

![Use case Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aOAIN_gn3GztpyrKI3cyCozTII6nM26qEBM8goWrkIGnBpqdLK4f8B6oA3ydHo6uihWaDLT9ePfB0GX0gXHqTUqKD7mVxfwla9wPcA-GalbmTtkUmf69HvhpqXNoCXxkMbkWYQRQ3oogK99nU0jGJKacLkK4LK7CYZYyC1cevk7kZSb8Ig56u924w0mfAgrKI0RR0LJH3bOtCIzTqqh1x-6k_QKWmSK52Zb0AM8CWmWa7LwO3z8oFHDkJ3P41icqMYw7rBmKK0G00000__y30000)

## Mô tả: Đăng nhập

**Tên ca sử dụng:** Đăng nhập  
**Tác nhân:** Nhân viên, Quản lý  
**Mô tả:** Tác nhân nhập tên đăng nhập và mật khẩu để truy cập hệ thống.  

### Tiền điều kiện  
- Tác nhân đã có tài khoản trong hệ thống.  

### Luồng sự kiện chính  
1. Tác nhân mở giao diện đăng nhập.  
2. Tác nhân nhập tên đăng nhập và mật khẩu.  
3. Hệ thống kiểm tra tính hợp lệ của thông tin đăng nhập.  
4. Nếu thông tin hợp lệ, hệ thống cho phép truy cập.  
5. Nếu thông tin không hợp lệ, hệ thống thông báo lỗi và yêu cầu nhập lại.  

### Hậu điều kiện  
- Tác nhân đăng nhập thành công và có quyền sử dụng hệ thống.  

### Lý do thiết kế  
- Ca sử dụng này là cơ bản và cần thiết cho mọi hệ thống quản lý.  
- Đăng nhập đảm bảo chỉ những người có quyền mới truy cập được hệ thống, đáp ứng yêu cầu về bảo mật và kiểm soát truy cập.  

---

# 2. Nhập thời gian làm việc

![Use case Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aOAINyRXHNaAPPc7L-KfAIGMAxZc5kJaLwQcSXMb9fSavgNdf2ee1IHM5kNdv2W4LnQNfEOgALHpAG01JAM2hgwTWePpniFTlNaAUHaFTwqjK2W1ykPcAgHd9kOfv1nUa0kquE7kzcHDB1hzO3eERybBLoZ9pCElcGJr4FCZ3YzCXZWBwCt32nJI7-vUcmar2xiSH9ytq93cN8MIeaGakw3wiCj1zFaSsr0Ab7cuUpsod9M2tyDT-qiLW4vTNA2G0tGVOPD28099XnVcWtHCpuIRaWsHGJAibiiXDIy55Ay00000__y300000)

## Mô tả: Nhập thời gian làm việc

**Tên ca sử dụng:** Nhập thời gian làm việc  
**Tác nhân:** Nhân viên  
**Mô tả:** Nhân viên nhập thông tin về thời gian làm việc của mình.  

### Tiền điều kiện  
- Nhân viên đã đăng nhập thành công.  

### Luồng sự kiện chính  
1. Nhân viên chọn chức năng nhập thời gian làm việc.  
2. Hệ thống hiển thị biểu mẫu để nhập thông tin thời gian làm việc (ngày, giờ bắt đầu, giờ kết thúc).  
3. Nhân viên nhập thông tin và xác nhận.  
4. Hệ thống kiểm tra tính hợp lệ của thông tin.  
5. Nếu hợp lệ, hệ thống lưu thông tin vào cơ sở dữ liệu.  
6. Nếu không hợp lệ, hệ thống thông báo lỗi và yêu cầu nhập lại.  

### Hậu điều kiện  
- Thông tin thời gian làm việc được lưu trữ để xử lý tiếp.  

### Lý do thiết kế  
- Ca sử dụng này đảm bảo rằng hệ thống nhận được dữ liệu chính xác về thời gian làm việc của nhân viên, là cơ sở để tính toán tiền lương.  
- Thiết kế tập trung vào tính hợp lệ của dữ liệu nhằm tránh sai sót trong bước xử lý sau.  

---

# 3. Phê duyệt thời gian làm việc

![Use case Diagram](https://www.planttext.com/api/plantuml/png/b94_JiCm6CNtdE8f4nrw0OQg4ZEe28Qknh5i2yUD70SfGinC31m0YQWRY8qf5khWa_W4N86lj9JoNtYnzFpUx_cpdyDYN7lcV5EQZ74_SyWFczJFBKnyoi5gx3FBf72P4zmpAur0Fc6jcnc3exRseinnde7MseZXS8ITFPN2bKMbuXsAfatXqiEJTgCXDLlIRqkSQTBvu6jwAaeKp2hKiUCA9wyNaaglh3yVlwUvql0wzGkgJU7UocyXlxbMhCdM08DT792t0Sqnhs18-m_gc6IofN2jDwHJ5H_9-XdueNNzeAb_g60LRTJWKjzHpglOlSspZVyxSf6DXIsMl_u2003__mC0)

## Mô tả: Phê duyệt thời gian làm việc

**Tên ca sử dụng:** Phê duyệt thời gian làm việc  
**Tác nhân:** Quản lý  
**Mô tả:** Quản lý kiểm tra và phê duyệt hoặc từ chối các bản ghi thời gian làm việc của nhân viên.  

### Tiền điều kiện  
- Quản lý đã đăng nhập thành công.  

### Luồng sự kiện chính  
1. Quản lý chọn chức năng phê duyệt thời gian làm việc.  
2. Hệ thống hiển thị danh sách các bản ghi thời gian làm việc.  
3. Quản lý chọn và xem chi tiết từng bản ghi.  
4. Quản lý thực hiện hành động phê duyệt hoặc từ chối bản ghi.  
5. Hệ thống cập nhật trạng thái phê duyệt của bản ghi.  

### Hậu điều kiện  
- Trạng thái của bản ghi được cập nhật (đã phê duyệt hoặc từ chối).  

### Lý do thiết kế  
- Chức năng này đảm bảo rằng thời gian làm việc được nhân viên khai báo là chính xác và phù hợp với chính sách công ty.  
- Thiết kế hỗ trợ quản lý kiểm tra thông tin chi tiết, đồng thời tối ưu hóa quy trình xử lý và kiểm soát thời gian làm việc.  

---

# 4. Tính toán tiền lương

![Activity Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aOAInyFTxGeb6GztJynBLpWoyU7koK0Qo9sif91OhE2Sav-S7LnPN9AQ2zCGa5XPb9-Je-2SdrS2OgGMWLL2XH6YN4MfoIM9UUavgGWz49EK5Agv5800oN05NLqx1GrleBtpCy6kc0bqHSdXjNaP2YNvXnVcAPHaFjpTcAUGSsp3iOLvwPfW_IIe1vkFwKIGAHYY4BVuFDorj18OC8UtW4pEp0E7qTnCXVJCHA2nXnVaAfG1hMXFrYJ94A0PYmjWmGpr1T4sGSmC8HGgU1H0J8Wul30Px8PkeBg238WSsDQLoK0g4QORQXxHog5-FhQX5DatSCVLSZcavgM0aXu0003__mC0)

## Mô tả: Tính toán tiền lương

**Tên ca sử dụng:** Tính toán tiền lương  
**Tác nhân:** Hệ thống đồng hồ, PayrollController  
**Mô tả:** Hệ thống tự động tính toán tiền lương dựa trên dữ liệu thời gian làm việc và thông tin hợp đồng của nhân viên.  

### Tiền điều kiện  
- Dữ liệu thời gian làm việc đã được phê duyệt.  

### Luồng sự kiện chính  
1. Hệ thống đồng hồ khởi động quá trình tính toán tiền lương.  
2. PayrollController truy xuất thông tin thời gian làm việc và thông tin hợp đồng của nhân viên từ cơ sở dữ liệu.  
3. PayrollController thực hiện tính toán tiền lương dựa trên:  
   - Số giờ làm việc.  
   - Mức lương cơ bản.  
   - Các yếu tố khác như tăng ca, hoa hồng, hoặc phụ cấp.  
4. PayrollController xác định phương thức thanh toán (phiếu lương hoặc giao dịch ngân hàng).  
5. Hệ thống lưu kết quả tính toán lương vào cơ sở dữ liệu để chuẩn bị thanh toán.  

### Hậu điều kiện  
- Thông tin tiền lương của nhân viên được tính toán và lưu trữ thành công.  

### Lý do thiết kế  
- Quá trình tự động hóa tính toán tiền lương giúp tiết kiệm thời gian, giảm thiểu sai sót và đảm bảo tính chính xác.  
- Thiết kế hệ thống phân tách vai trò giữa việc thu thập dữ liệu và tính toán giúp duy trì tính toàn vẹn của dữ liệu và dễ dàng mở rộng trong tương lai.  


---

# 5. Phát hành phiếu lương

![Activity Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO9IG69bKNvEZe9pVbu9Y95QfAIGMAm05KQ8mjHxFDpThb2IyN3tnBnqXSmyXOUxbkP1T1HbvfK4LnQNfEPo5QKcboJcfUUa8io7o2WfL7Cf0066yGgwkdOA6iuPfGzthSnJI7guknjeoU4jG3jAW9OKP6G-tBM_L27ds8PZ2_FIDS5c4AqQR3Qoyy0kGF0XTdlYiWQB14I7H_xX1NaWYnVaPG2L75vOeW1ZevbJo-MGcfS22dK00000__y30000)

## Mô tả: Phát hành phiếu lương

**Tên ca sử dụng:** Phát hành phiếu lương  
**Tác nhân:** PayrollController, Hệ thống in ấn  
**Mô tả:** Hệ thống chuẩn bị và in phiếu lương cho nhân viên.  

### Tiền điều kiện  
- Tiền lương đã được tính toán và lưu trữ.  

### Luồng sự kiện chính  
1. PayrollController chuẩn bị thông tin phiếu lương từ dữ liệu đã lưu.  
2. PayrollController gửi thông tin phiếu lương đến hệ thống in ấn.  
3. Hệ thống in ấn tạo bản cứng của phiếu lương.  
4. Quá trình phát hành phiếu lương hoàn tất và phiếu lương được gửi cho nhân viên.  

### Hậu điều kiện  
- Nhân viên nhận được phiếu lương để đối chiếu và lưu trữ.  

### Lý do thiết kế  
- Quy trình phát hành phiếu lương được thiết kế để đảm bảo nhân viên nhận được bản cứng phiếu lương chính xác và kịp thời.  
- Tối ưu hóa sự phối hợp giữa PayrollController và hệ thống in ấn nhằm giảm thiểu sai sót trong việc phát hành phiếu lương, giúp hệ thống vận hành trơn tru và chính xác.  


---

# 6. Giao dịch trả lương

![Activity Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO9IG69bKNvEZe9pVbu9Y95QfAIGMAm05KQ8mjHxFDpThb2IyN3tnBnqXRpqmulo538EByXB1-joIipB3guiBadDvIfAJIv9p4lFIKLO0P5HKgZcKW0231iKT7Nj53ISCqeVxbgPfv3qS7Stq9x3Mu3Mb6JcAQHd9kOhf005apCqmVg9KWas4ybL88q8BiJ6Y8Uxroha7DwBh56XfEZXhiKAESSs75kObmwra0Y541Czye4X0dBIWZmCasgv75BpKa0H00000F__0m00)

## Mô tả: Giao dịch trả lương

**Tên ca sử dụng:** Giao dịch trả lương  
**Tác nhân:** PayrollController, Hệ thống ngân hàng  
**Mô tả:** Hệ thống thực hiện giao dịch trả lương vào tài khoản ngân hàng của nhân viên.  

### Tiền điều kiện  
- Tiền lương đã được tính toán và phương thức thanh toán là giao dịch ngân hàng.  

### Luồng sự kiện chính  
1. PayrollController chuẩn bị thông tin giao dịch trả lương từ dữ liệu đã lưu.  
2. PayrollController gửi yêu cầu giao dịch trả lương đến hệ thống ngân hàng.  
3. Hệ thống ngân hàng xử lý và hoàn tất giao dịch trả lương.  
4. Hệ thống xác nhận giao dịch hoàn thành và gửi thông báo cho PayrollController.  

### Hậu điều kiện  
- Nhân viên nhận được lương qua tài khoản ngân hàng.  

### Lý do thiết kế  
- Ca sử dụng này đảm bảo quy trình trả lương tự động qua ngân hàng, giúp tăng tính minh bạch và giảm thời gian thực hiện.  
- Việc tích hợp với hệ thống ngân hàng giúp nâng cao độ chính xác và bảo mật của giao dịch, đồng thời giảm thiểu sai sót và tăng hiệu quả trong quá trình trả lương.  
