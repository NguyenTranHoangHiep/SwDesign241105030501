# 1. Vẽ biểu đồ ngữ cảnh và giải thích
## 1.1 Hệ thống con BankSystem
## 1.1.1 Biểu đồ ngữ cảnh của hệ thống con BankSystem

![Class Diagram](https://www.planttext.com/api/plantuml/png/d5AzJiCm4Dxp5ATEhKGYM2ChgkZK3Qaho-6unOfzjco7De8-6GEFn2jWrqe9RISyn1T_z_tauk_FhwKFw4AlLO5AcRsM1qcxmdUIB3hKm8ssXWI5JHYK02TuGDefKSG5m1Lw3qyuEAFKob18kt306CylJHExhl4QN4zWy_byaQGa1U6so0Mi7v6wpU23qF0U4O1MMEDbc6DKug-2TpMCrLqYciIe8JtNj3LEOv265f5x_4qvKMNCzoy-rzQPmz0qoMZIKV_RynY5uhXa6CxzZEM3x79ATUwvu6VyUc1bQ_PKDdzcKyEibUc7Z5azdEmyl4byflkgUfX5iIc5VLJLv3Clq38QZ9blG3UY5iLIK9jkpmy0003__mC0)

## 1.1.2 Giải thích hệ thống con BankSystem

Sơ đồ UML này mô tả một hệ thống bảng lương với các thành phần chính như sau:

- **PayrollController**: Điều khiển quy trình trả lương, có phương thức `runPayroll()` để thực hiện quy trình tính toán và trả lương cho nhân viên.
  
- **IBankSystem**: Là một giao diện đại diện cho hệ thống ngân hàng, với phương thức `deposit()` để gửi tiền lương (paycheck) vào tài khoản ngân hàng.

- **BankSystem**: Là hệ thống ngân hàng thực tế, triển khai phương thức `deposit()` của giao diện `IBankSystem`.

- **Paycheck** và **BankInformation**:
  - **Paycheck**: Thể hiện dữ liệu của từng khoản tiền lương.
  - **BankInformation**: Thể hiện thông tin tài khoản ngân hàng để nhận tiền lương.

### Quan hệ giữa các thành phần
- `PayrollController` gửi yêu cầu trả lương thông qua `IBankSystem`.
- `IBankSystem` kết nối với `BankSystem`, `Paycheck`, và `BankInformation` để thực hiện giao dịch.

Sơ đồ này mô tả cách hệ thống bảng lương gửi tiền vào tài khoản ngân hàng thông qua một giao diện trung gian (`IBankSystem`)
## 1.2 Hệ thống con PrintService
### 1.2.1 Biểu đồ ngữ cảnh hệ thống con PrintService
![Class Diagram](https://www.planttext.com/api/plantuml/png/r5HBRiCW5Dpx52nTgRu0YgmiceKNbQ8u5o3uDKOrOC5pKbJrP5tqIBr2iUDla2jrMIymVZDlc07axy-lhKLci95L50c5O5uO1x8ttJm7Sn7-SxF9cvDr5a6IskWtbwRl4McVkYNkcUCbyDSOP5rf1v0LbEJeeVCZgNkGae7sGCb5Ys8cS81Q6unDzpgw6gRsK7BHVWO5XY4CshtIUjV7F6OMvCm6B4t9Fux8AsRjwCRdsYaKwCPGITXzgpEf6uMK5BevLN2h-NXFVdrAsd4iIL3u35ZgfK9WDmvixVgr_s1BCGdBohg3nBAA6RVCmBMKmbgXrQ6BCiTAtPZA1NMV1ESXXlaSd2oqZDw43tfthv92NrMIJWT2nssoQznnboZfSCRHagl0Chg_jR-ghv7NvQCjgABz7_m0003__mC0)
## 1.2.2 Giải thích hệ thống con

### 1. **PrinterService :**
   - Là một giao diện cung cấp các phương thức để in phiếu lương, báo cáo và tạo báo cáo phiếu lương.
   - **Phương thức:**
     - `printPaycheck(employeeId: String, paycheck: Paycheck): void`: In phiếu lương cho nhân viên.
     - `printReport(reportType: String, employeeId: String): void`: In báo cáo cho nhân viên.
     - `generatePaycheckReport(employeeId: String): void`: Tạo báo cáo phiếu lương cho nhân viên.

### 2. **IPrinterService :**
   - Cũng là một giao diện tương tự như PrinterService, cung cấp các phương thức tương tự để in phiếu lương và báo cáo.
   - **Phương thức:**
     - `printPaycheck(employeeId: String, paycheck: Paycheck): void`
     - `printReport(reportType: String, employeeId: String): void`
     - `generatePaycheckReport(employeeId: String): void`
   
   **Lý do có sự trùng lặp:**  
   - **PrinterService** có thể triển khai các phương thức của **IPrinterService** trong một hệ thống đa lớp, giúp linh hoạt hơn khi cần thay đổi cách thức thực thi.

### 3. **Paycheck :**
   - Là thực thể chứa thông tin về phiếu lương của nhân viên, bao gồm các thuộc tính:
     - `employeeId`: ID của nhân viên.
     - `amount`: Số tiền lương.
     - `payDate`: Ngày trả lương.
     - `paymentMethod`: Phương thức thanh toán (tiền mặt, chuyển khoản, v.v.)
   - **Phương thức:**
     - `generatePaycheck()`: Tạo phiếu lương cho nhân viên, tính toán số tiền lương cần trả.

### 4. **Employee :**
   - Đại diện cho nhân viên, chứa các thông tin:
     - `employeeId`: ID của nhân viên.
     - `name`: Tên nhân viên.
     - `paymentMethod`: Phương thức thanh toán của nhân viên.
     - `salary`, `commissionRate`, `hourlyRate`: Các yếu tố liên quan đến tính toán lương của nhân viên.
   - **Phương thức:**
     - `getPaycheck()`: Trả về phiếu lương của nhân viên.
     - `getPaymentMethod()`: Trả về phương thức thanh toán của nhân viên.
## Quan hệ giữa các thành phần:

- **PrinterService** và **IPrinterService** đều tương tác với **Paycheck** và **Employee**:
   - **PrinterService** và **IPrinterService** có thể tạo phiếu lương (sử dụng phương thức `generatePaycheck()` trong **Paycheck**), in các báo cáo cho nhân viên và in phiếu lương cho nhân viên.
   - Các dịch vụ này sử dụng thông tin từ **Employee** để in các báo cáo và tính toán phiếu lương cho nhân viên.

- **Paycheck** và **Employee**:
   - **Paycheck** chứa thông tin lương của từng nhân viên và liên kết với **Employee** thông qua các thuộc tính như `employeeId` và phương thức thanh toán (`paymentMethod`).


