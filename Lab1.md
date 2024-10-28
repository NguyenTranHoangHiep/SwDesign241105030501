# 1.Phân tích kiến trúc
## Đề xuất kiến trúc: Kiến trúc MVC
### Lý do lựa chọn:
Kiến trúc Model-View-Controller (MVC) sẽ là một lựa chọn cho hệ thống payroll mới của Acme . MVC cung cấp sự phân tách rõ ràng giữa các phần chính của ứng dụng, giúp quản lý hiệu quả các chức năng riêng biệt trong một hệ thống phức tạp. Điều này rất quan trọng đối với một ứng dụng yêu cầu tích hợp nhiều lớp như hệ thống payroll mới, bao gồm:

- Giao diện desktop(View layer): Đây là phần mà người dùng (nhân viên và quản trị viên payroll) tương tác trực tiếp để nhập dữ liệu, như bảng chấm công, tùy chọn thanh toán, và yêu cầu báo cáo.

- Logic ứng dụng(Application Logic): Đây là các quy tắc và quy trình cần thiết để xử lý lương của các loại nhân viên khác nhau (nhân viên theo giờ, nhân viên hưởng lương, và nhân viên nhận hoa hồng). Tính toán lương phải đúng cho từng loại và đảm bảo thực hiện các lịch trình trả lương chính xác.

- Tích hợp dữ liệu(Data): Hệ thống mới cần tích hợp với một cơ sở dữ liệu payroll mới để quản lý thông tin nhân viên và thời gian làm việc. Đồng thời, phải kết nối với cơ sở dữ liệu DB2 cũ để truy xuất các mã dự án và thông tin liên quan mà không làm gián đoạn quy trình làm việc hiện tại.
### Biểu đồ package mô tả kiến trúc.
 ![Package Diagram](https://www.planttext.com/api/plantuml/png/T98zQWCn48LxdM9muyfD3X3iP0CfR3298KLmCTQEDyBwOwImYE2JfSYHSeLeiygQc5qGAkQz-VHuwFlpQnaYSdmtMdYK9sm8PbjCxBI6vnGYcHby281yBZfJ81inAcTXZOcuzm2ylYXRkpP0HU4KdOULz_kidAy8UQoL_0KCgt-lRjb92a7PPjyBEsL88jUmGPktJNwwAFVE69MjESOZsbfVTXwCrouHPHeTYSbcP96Uo3kEnNeThCA8Gw81qaqF6AWGrjIWJ53TtVnJ2ciEA-QkW-WWlBaMZZfV1uejaGNTrHN4H5MmMDnEDJ4sxlsZEQVje_7FGYp9rjq_-0400F__0m00)
# 2.Cơ chế phân tích
## Đề xuất các cơ chế:
- Bảo mật
- Lưu trữ
- Giao tiếp giữa các module
- Khả năng chịu lỗi
- Kết nối hệ thống cũ
## Lý do lựa chọn:
## 1. Cơ chế Bảo mật
- Xác thực Người Dùng:

Nhân viên chỉ có thể truy cập và chỉnh sửa thông tin của chính họ, đảm bảo tính riêng tư và bảo mật thông tin cá nhân.
- Quản lý Quyền Truy Cập:

Điều này giúp ngăn chặn quyền truy cập trái phép vào thông tin nhạy cảm và đảm bảo rằng chỉ những người có quyền hợp lệ mới có thể truy cập dữ liệu.
- Mã hóa Dữ liệu:

Bảo vệ thông tin tài chính và cá nhân của nhân viên khỏi việc bị xâm phạm, đặc biệt khi dữ liệu có thể bị truy cập trái phép.
## 2. Cơ chế Lưu trữ
- Hệ thống Lưu trữ An toàn:

Để lưu trữ thông tin về khoảng 5,000 nhân viên, hệ thống cần đảm bảo tính toàn vẹn và bảo mật của dữ liệu.
- Sao lưu Dữ liệu:

Việc sao lưu định kỳ giúp bảo vệ thông tin quan trọng khỏi sự cố mất mát, đảm bảo rằng dữ liệu có thể được phục hồi nhanh chóng.
## 3. Cơ chế Giao tiếp giữa các Module
- API RESTful:

Cần có một giao diện hiệu quả để các module trong hệ thống giao tiếp với nhau và với hệ thống cũ, giảm độ phụ thuộc giữa các module.
- Kiểm soát Lỗi và Thông báo:

Điều này giúp duy trì hiệu suất hoạt động của hệ thống và đảm bảo rằng người dùng nhận được thông tin chính xác và kịp thời về tình trạng hoạt động của hệ thống.
## 4. Cơ chế khả năng chịu lỗi
- Kiểm soát Lỗi Tự động:

Để hệ thống có thể tự động phát hiện và xử lý lỗi trong quá trình thanh toán, đảm bảo rằng nhân viên được trả lương đúng hạn.
- Dự phòng Hệ thống:

Các biện pháp dự phòng giúp bảo vệ thông tin nhạy cảm và đảm bảo rằng quy trình thanh toán không bị gián đoạn.
## 5. Cơ chế Kết nối Hệ thống Cũ
- Tích hợp Hệ thống Cũ (DB2):

Acme muốn duy trì hệ thống DB2 cũ để tiết kiệm chi phí, vì vậy cần một cơ chế kết nối cho phép truy cập thông tin mà không cần thay đổi hệ thống hiện tại.
- Chuyển đổi Dữ liệu:

Đảm bảo rằng thông tin từ hệ thống cũ có thể được sử dụng trong hệ thống mới mà không gặp phải vấn đề về tính tương thích, cải thiện tính liên tục trong việc quản lý thông tin.
# 3. Phân tích ca sử dụng Payment
## 1. Boundary (Lớp Giao Diện)

- **Lớp:** `Payment`
  - **Nhiệm vụ:** 
    - Xử lý yêu cầu thanh toán từ nhân viên.
    - Xác thực thông tin thanh toán.
    - Tạo các khoản thanh toán cho nhân viên.
  - **Thuộc tính:**
    - `paymentId: String`
    - `employeeId: String`
    - `amount: Double`
    - `paymentDate: Date`
    - `paymentMethod: Enum {Mail, Direct Deposit, In-Person}`
  - **Phương thức:**
    - `createPayment()`: Tạo một khoản thanh toán mới.
    - `validatePayment()`: Kiểm tra tính hợp lệ của yêu cầu thanh toán.
    - `processPayment()`: Thực hiện thanh toán cho nhân viên.

---

## 2. Control (Lớp Điều Khiển)

- **Lớp:** `PayrollAdministrator`
  - **Nhiệm vụ:**
    - Quản lý các hoạt động thanh toán trong hệ thống.
    - Tạo và xem các báo cáo thanh toán cho nhân viên.
  - **Thuộc tính:**
    - `adminId: String`
    - `name: String`
  - **Phương thức:**
    - `generatePayments()`: Tạo thanh toán cho các nhân viên.
    - `viewReports()`: Xem các báo cáo liên quan đến thanh toán.

---

## 3. Entity (Lớp Thực Thể)

- **Lớp:** `Employee`
  - **Nhiệm vụ:**
    - Đại diện cho nhân viên trong hệ thống.
    - Cho phép nhân viên yêu cầu thanh toán và xem lịch sử thanh toán của họ.
  - **Thuộc tính:**
    - `employeeId: String`
    - `name: String`
    - `payType: Enum {Hourly, Salaried, Commissioned}`
  - **Phương thức:**
    - `requestPayment()`: Gửi yêu cầu thanh toán.
    - `viewPaymentHistory()`: Xem lịch sử thanh toán của nhân viên.

---

- **Lớp:** `PaymentReport`
  - **Nhiệm vụ:**
    - Chứa thông tin báo cáo thanh toán cho nhân viên.
    - Tổng hợp số giờ làm việc và tổng thanh toán.
  - **Thuộc tính:**
    - `reportId: String`
    - `employeeId: String`
    - `totalHours: Double`
    - `totalPayments: Double`
  - **Phương thức:**
    - `generateReport()`: Tạo báo cáo thanh toán cho nhân viên.
    - `viewReport()`: Xem báo cáo thanh toán.

---

- **Lớp:** `ProjectManagementDatabase`
  - **Nhiệm vụ:**
    - Cung cấp thông tin về charge numbers cho nhân viên.
  - **Thuộc tính:**
    - `databaseStatus: Boolean`
  - **Phương thức:**
    - `getEmployeeChargeNumbers()`: Lấy thông tin charge numbers cho nhân viên.
## Biểu đồ lớp phân tích ca sử dụng Payment
![Class Diagram](https://www.planttext.com/api/plantuml/png/Z5DBRi903Drp2ejLMm4gswne0GaMLAZq0YQnOAhvf9u9LOGuMHSzKg_GIJ893QHgiuWqpsFxlMVFryVdn3fabodPYoLQ2tELIfCJmR47_Xi21M2PHB1nBFGk13Ggke1Ip5_orADpdIauBap6CX_01YMoe6G0KwEKi5OOJScfJ09WUil8kZNcYhIxkGtmGT1xm1R2EiEv3vrwWMQ8D2pJwdn5ybVsg4ocNGGpasqbjQlCq7aDnR-DhyZjJLAhMw6G0vW9fjZ1Z59ZXHl0KW_NnDReMbxCv0jTgKCfaWuyPHEJjMVufs8sKZuaIcZl1wEtf96F1VhtX01sf8dFVMtBxcSlWaliqkSgqhJZylX_ivrnA8jji1U6bu6QIojsfbhrxY3QuidcrSzXXHft56Q8MxJdFKu2i77eCj_hqHX9g9jchjxywHvvHq-PslevLZsQHz4Vzs4uXFxzQ7JNRvOmyeR490vaUvrJwimAbaQDpZAvh5VV7rzVhhQf--gl5aI0SR5LFcz2EYaU-pS0003__mC0)
## Biểu đồ sequence phân tích ca sử dụng Payment
![Squence Diagram](https://www.planttext.com/api/plantuml/png/V58xRWCX4Eqv1QLJ-09RHBOI5ouIHIdIZs6q9kANOTQMpvOYHyeLmjgBzkjG81ZUXtdm-_spIGp4ZRC250UIEnTjk22AcCj6cGYUvHjS77gUrYXOkzNEU9EO8BENIEyO0qse53vHyGjugB75F0F30H8AKUpb-h48L9Bmgy74tNxr8BhL5NHFgv8rSf5xEWBL-Dgu0r9g1Uwnv7feh8QqaMj1dC0Q3OpztS2o_6YhCdQfoJoMk8fmn9pZPW6tJNcadfPwtWmyCBizGh4SUztEIkCBbdG5xFNqWYNSgdIQKrMO4kfiW3Q7kVUd_vBe1T8nd7T4WLOk2-GtoG9UYqsUsg_v1m00__y30000)
# 4. Phân Tích Ca Sử Dụng Maintain Timecard
## Các lớp loại phân tích
- **Boundary (Lớp Giao Diện)**
  - `TimecardForm`
  
- **Control (Lớp Điều Khiển)**
  - `TimecardController`
  
- **Entity (Lớp Thực Thể)**
  - `Employee`
  - `Timecard`
  - `ChargeNumber`
  - `ProjectManagementDatabase`
 ## Nhiệm vụ của từng lớp phân tích
- **Boundary (Lớp Giao Diện)**
  - `TimecardForm`
    - **Nhiệm vụ:** Cung cấp giao diện người dùng để nhập và hiển thị thông tin timecard.

- **Control (Lớp Điều Khiển)**
  - `TimecardController`
    - **Nhiệm vụ:** Điều phối các hành động giữa người dùng và các lớp thực thể, xử lý logic và quản lý trạng thái của timecard.

- **Entity (Lớp Thực Thể)**
  - `Employee`
    - **Nhiệm vụ:** Đại diện cho nhân viên, lưu trữ thông tin cá nhân và quản lý các thao tác liên quan đến timecard của họ.
  - `Timecard`
    - **Nhiệm vụ:** Lưu trữ thông tin về giờ làm việc của nhân viên, quản lý trạng thái và xử lý các thao tác liên quan đến timecard.
  - `ChargeNumber`
    - **Nhiệm vụ:** Đại diện cho số charge để lập hóa đơn, cung cấp thông tin và quản lý các số charge có sẵn.
  - `ProjectManagementDatabase`
    - **Nhiệm vụ:** Cung cấp và quản lý các dữ liệu liên quan đến dự án, bao gồm số charge và trạng thái cơ sở dữ liệu.

## Biểu đồ lớp phân tích ca sử dụng Maintain Timecard
![Class Diagram](https://www.planttext.com/api/plantuml/png/Z5JDRjim3BxxAGIVkg4frgjH3DtQ30kmhiDIe6V6PXsr-Z4esOLHvCbss2Fj5IOdiYp73hOS0l3ZHv7yIFhFhz_NnWBPMeea5s0CMyfAw1QHlINC_HOCFR0gChQsn5Nf7Gea7a4Lj0zjvT2bgYLx-wfh4kqvMuC0ubZizZJ6X2xlrTaxRw6oI1tL1CZK6ydj0vUO0nK1RZY-Hk0kyJNtMAZPUc1IyybczYhSWdMrT_yzNHKJx52RnHcF1LkRllbRWYVhUk_fEy_QTfq-Qdf1LyCtRgnlBYTqJuLU2Lrvs0o0WSXeGF0YfX-g2gQ45_o9KDmhqSPAtMo1IlnUomrIK2kFm8am1PgSU6MvLYFFKE6d1hY0ZS3uSHDd_K7w6NDx1mfAb6xUJZJOW1cMhF30saluMMk1e7oc4ks_a_HBy4MJ3E_-_rXZ4SnXC5Tnhezpuxk3wgfxuvojt1ANFOknWfjAG1lcaMiXd08hLTN3aCnMlow9D9r9DCP9qmiS4zPrdZllb39f_4OhIrqUcjn15aX7Tv25U_SfkOgswDGP-kKRToCq53F32T-Jz39bYmLBFrnSl4-7aytO5amIJEyUYAEDpPoGoW9N9ZczK-D4H_4LwOQxdKv6wzA7NAPpQXwoEcE8YhmpiIv2xkiooRNRjUxZ-XS00F__0m00)
## Biểu đồ sequence phân tích ca sử dụng Maintain Timecard
![Squence Diagram](https://www.planttext.com/api/plantuml/png/Z5ExJiGm4Epp5IwFWXz8WGuTXw20Gu3eDyugP_0ZMcy2-JOAFebVO9DJHC8bv5ous5tFZ6Vixy-lTMGWhfnDG7CWjNMb3GrYKahPQ5E2P_Li76gWV1CyKx0MQR8zAZvGU4NDT-2XG8UUhu0XWpYDV1t89KbFhiul9ZXJPKEnywkpvBWtF94gGYQ3DSees5yIbGUCoWTM-64Y9qhM4fGc16w1qESplBCtJLM1V5c3iP1PtEo12holN8OK1N3ssDpjOH9fmOpMs5Jb9fOM6c6TilWm8mgGRaBLYHksneP4w7nTYYfMcJFSTqx8h0PhyeFLRMQtlYkeVIjebDInyhWFxrkYG2k7COgRafOL7rzEGEYL2ktyY8CtV4J8TzusVmR_SxtLzLHfBQ86okGThMLhlzmF0000__y30000)
# 5. Hợp nhất kết quả phân tích

## Các tác nhân tham gia vào hệ thống

Trong hệ thống hợp nhất "Payment" và "Maintain Timecard," các tác nhân tham gia bao gồm:

---

### 1. Nhân viên (Employee)
- **Vai trò:** 
  - Người sử dụng chính của hệ thống để thực hiện các yêu cầu thanh toán, nộp thẻ chấm công, và xem lịch sử thanh toán.
  
- **Tác vụ:** 
  - Gửi yêu cầu thanh toán.
  - Xem lịch sử các khoản thanh toán.
  - Nộp và kiểm tra thẻ chấm công.

---

### 2. Quản trị viên (Payroll Administrator)
- **Vai trò:** 
  - Quản lý các giao dịch liên quan đến thanh toán và thẻ chấm công, chịu trách nhiệm điều phối các hoạt động thanh toán cho nhân viên.
  
- **Tác vụ:** 
  - Tạo các khoản thanh toán cho nhân viên dựa trên thời gian làm việc hoặc các yêu cầu khác.
  - Xem và tạo báo cáo thanh toán.
  - Quản lý các số charge liên quan đến dự án.

---

### 3. Cơ sở dữ liệu quản lý dự án (Project Management Database)
- **Vai trò:** 
  - Hệ thống phụ trợ hoặc bên thứ ba được kết nối để lưu trữ và cung cấp các số charge cho nhân viên, phục vụ mục đích lập hóa đơn và quản lý dự án.
  
- **Tác vụ:** 
  - Cung cấp số charge cho thẻ chấm công của nhân viên.
  - Cập nhật và truy xuất thông tin về dự án để hỗ trợ báo cáo thanh toán.

---
## Các lớp phân tích

### 1. **Boundary (Lớp Giao Diện)**
   - **`TimecardForm`**: 
     - **Chức năng**: Cung cấp giao diện cho nhân viên nhập thẻ chấm công và xem lịch sử chấm công.
   
   - **`Payment`**: 
     - **Chức năng**: Cung cấp giao diện để xử lý yêu cầu thanh toán từ nhân viên và kiểm tra tính hợp lệ của thanh toán.

### 2. **Control (Lớp Điều Khiển)**
   - **`PayrollAdministrator`**:
     - **Chức năng**: Điều khiển và quản lý các hoạt động thanh toán, đồng thời tạo báo cáo thanh toán cho nhân viên.
   
   - **`TimecardController`**:
     - **Chức năng**: Điều phối các hành động giữa người dùng và các lớp thực thể liên quan đến thẻ chấm công, xử lý các logic liên quan đến nghiệp vụ.

### 3. **Entity (Lớp Thực Thể)**
   - **`Employee`**: 
     - **Chức năng**: Đại diện cho nhân viên trong hệ thống, lưu trữ thông tin nhân viên và các thao tác liên quan đến thanh toán và thẻ chấm công.

   - **`Timecard`**: 
     - **Chức năng**: Lưu trữ thông tin về giờ làm việc của nhân viên, quản lý và truy xuất dữ liệu thẻ chấm công.

   - **`PaymentReport`**: 
     - **Chức năng**: Lưu trữ thông tin báo cáo thanh toán cho nhân viên, bao gồm tổng hợp số giờ làm việc và tổng số tiền thanh toán.

   - **`ChargeNumber`**: 
     - **Chức năng**: Đại diện cho số charge dùng trong việc lập hóa đơn, cung cấp thông tin và quản lý các số charge.

   - **`ProjectManagementDatabase`**: 
     - **Chức năng**: Hệ thống phụ trợ lưu trữ và cung cấp thông tin về số charge và trạng thái cơ sở dữ liệu liên quan đến các dự án.
 ### Biểu đồ class hợp nhất hai lớp phân tích
 ## Biểu đồ lớp phân tích ca sử dụng Maintain Timecard
![Class Diagram](https://www.planttext.com/api/plantuml/png/Z5NDRjim3BxxARISjY4fi6im36sJR2tG546J5s0iBjMc7u-IKnX5dso7FT9UOP9jfN9YPxqa4IcI7_bzOlx-_dDf7P0hbSpUSVmkDBA7nMnpTV_jRi5o2TPcsQjX1PL2xTXpnXWhciCjdxAr8w5tmOYgaAP2x5f1cLAxAPkRSYin2Pw3Gs_sdubnYUxH-FY5BXLxNeAGOpONXBbZSooC5MxCRlLaXMIDVWc1EQ5FqQ9x_s7AzaRmuDY35BphkZP68kYw7faShJsEUqbRtWY5EH3_QaWrVVUt-6JevuqfoQPTvez0ExmlrHOflMpBhH8kfau1Ss4B2LLqtGZh35Nzq3nkCb9USIMqlqVWhpOG8PYw-3GeJCyxr4Ylax6TgGbyUl2JfiJSEvIPqIv0mBPkVZWVyH_mJ7i19ppqpICIcFeYWnr8YvQLSnmTpy3hRLCL69KMw9FLcAr10WdaOpOpIWbhXT78Qw4H_YhHkZwb-PcrvhEanKOQdAuzlUKH1OKXFz4OxpoXOMKH-aounnFViQP22mtx3KQgVxy5eJCEv0d0sXfbbZgY19jY_GBiHpbBtbMhl86Nnj7c90hdAUogtpKvvkZyVXcG-OhC3xzrbg1XX-swWYtOLcIyFQqTkD9sDelF7mMPOgtht7bvV4wjNqBLWtv7dqPiCgc_sg7r-2ukFeuEKXhoTxWSAd3w8EEIFvUiPm7yB-tva7JD7gwc5zA1PHt-Mu2nzX1dMNQ9ceS_kdy0003__mC0)
  



