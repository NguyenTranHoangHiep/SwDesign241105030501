# 1. Vẽ biểu đồ ngữ cảnh và giải thích
## 1.1 Hệ thống con BankSystem
## 1.1.1 Biểu đồ ngữ cảnh của hệ thống con BankSystem

![Context Diagram](https://www.planttext.com/api/plantuml/png/d5AzJiCm4Dxp5ATEhKGYM2ChgkZK3Qaho-6unOfzjco7De8-6GEFn2jWrqe9RISyn1T_z_tauk_FhwKFw4AlLO5AcRsM1qcxmdUIB3hKm8ssXWI5JHYK02TuGDefKSG5m1Lw3qyuEAFKob18kt306CylJHExhl4QN4zWy_byaQGa1U6so0Mi7v6wpU23qF0U4O1MMEDbc6DKug-2TpMCrLqYciIe8JtNj3LEOv265f5x_4qvKMNCzoy-rzQPmz0qoMZIKV_RynY5uhXa6CxzZEM3x79ATUwvu6VyUc1bQ_PKDdzcKyEibUc7Z5azdEmyl4byflkgUfX5iIc5VLJLv3Clq38QZ9blG3UY5iLIK9jkpmy0003__mC0)

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
![Context Diagram](https://www.planttext.com/api/plantuml/png/r5HBRiCW5Dpx52nTgRu0YgmiceKNbQ8u5o3uDKOrOC5pKbJrP5tqIBr2iUDla2jrMIymVZDlc07axy-lhKLci95L50c5O5uO1x8ttJm7Sn7-SxF9cvDr5a6IskWtbwRl4McVkYNkcUCbyDSOP5rf1v0LbEJeeVCZgNkGae7sGCb5Ys8cS81Q6unDzpgw6gRsK7BHVWO5XY4CshtIUjV7F6OMvCm6B4t9Fux8AsRjwCRdsYaKwCPGITXzgpEf6uMK5BevLN2h-NXFVdrAsd4iIL3u35ZgfK9WDmvixVgr_s1BCGdBohg3nBAA6RVCmBMKmbgXrQ6BCiTAtPZA1NMV1ESXXlaSd2oqZDw43tfthv92NrMIJWT2nssoQznnboZfSCRHagl0Chg_jR-ghv7NvQCjgABz7_m0003__mC0)
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
## 1.3 Hệ thống con  ProjectManagementDatabase
## 1.3.1 Biểu đồ ngữ cảnh hệ thống con ProjectManagementDatabase
![Context Diagram](https://www.planttext.com/api/plantuml/png/b5JDRjim3BxxAOXSPWz8iLqD8oYGxX1WFqNH5s1a9j6WduoIWHb3dwo7FT9UeN8iUN5R1QqljiYFrCUFfFyz_hrs7jbtMXN51_YYZyhsH20KEWSb6IzzNnNZSV8spUXOhU1F0U5P0aNVfgr16X-j1ZNLu3nBiu-c8_Ptw8DrfooEE00cORczbve4SbiURCSk8ge8STrMIt_RiJYWen_S4fUeRMVyCw109JeLhhZ5lgpIFGz3US72LgbKdR36XtCgBtcR9ZgcyW3sP8Z7d0EcJEK6bb-byqsIPbN5czZ-9E6_eS4zwQ3MndZY7Gg2KgRFgfW-OVCY8l2Ot3CcVdr0tjFtJc-9DsPdIt5cI7BdYAp7sd8QvE2lYVAh8-xFoLmaCYetltvdUHY8a-n7jeAS2n6vpbpY4gFVq9ypxh7Q6_8ebNkNZ3VeSHi6CUcu3PFO8lTP8QU0fWcZx7hdIG-iV_VpvhwTqns5APVMk8Cykc9QpiNd1IoNiFXqTVLn0Mcde8vBbaNELYl0nuLpHLgBENfAKYVfQOAcFgM8y4f9Qj0dHIvYSpDOdxecX-0Sv2pDAnlrlWJv5lxFKroJQOUVvnC0003__mC0)
## 1.3.2 Giải thích hệ thống con

### 1. **Employee (Entity)**
   - **Thuộc tính**:
     - **employeeId** (int): Mã số nhân viên, duy nhất trong hệ thống.
     - **name** (string): Tên của nhân viên.
     - **payRate** (float): Mức lương cơ bản của nhân viên, được sử dụng để tính toán lương.
   
   - **Phương thức**:
     - **recordTimecard(hours: float)**: Ghi lại số giờ làm việc của nhân viên trong hệ thống.
     - **submitPurchaseOrder(amount: float)**: Gửi một đơn đặt hàng với giá trị tiền đã xác định.
     - **calculatePay(): float**: Tính toán và trả về lương của nhân viên dựa trên số giờ làm việc và mức lương cơ bản.

### 2. **Payroll (Control)**
   - **Phương thức**:
     - **generatePayroll(employees: List<Employee>)**: Xử lý và tạo bảng lương cho một danh sách nhân viên dựa trên thông tin về lương và thời gian làm việc của họ.

### 3. **IProjectManagement (Interface)**
   - **Phương thức**:
     - **getChargeNumberInfo(chargeNumber: string)**: Truy vấn thông tin chi tiết về một dự án thông qua số mã charge của dự án đó.

### 4. **ProjectManagementControl (Control)**
   - **Phương thức**:
     - **queryChargeNumber(chargeNumber: string)**: Truy vấn thông tin chi tiết của một dự án dựa trên số mã charge, giúp lấy các dữ liệu liên quan đến dự án.

### 5. **PayrollControl (Control)**
   - **Phương thức**:
     - **processPayroll(employees: List<Employee>)**: Xử lý và tính toán bảng lương cho danh sách nhân viên. Quy trình này có thể bao gồm tính lương cho các loại nhân viên khác nhau (lương theo giờ, lương cố định, hoặc lương theo hoa hồng).
     - **queryProjectDetails(chargeNumber: string)**: Truy vấn thông tin chi tiết về một dự án thông qua số mã charge, để lấy các dữ liệu liên quan đến dự án cần thiết cho quá trình tính toán lương.

### 6. **ProjectManagementDatabase (Subsystem Proxy)**
   - **Phương thức**:
     - **getProjectDetails(chargeNumber: string)**: Lấy thông tin chi tiết về dự án từ cơ sở dữ liệu bên ngoài, thông qua lớp proxy. Dữ liệu này có thể được sử dụng cho các tính toán lương và báo cáo.


## Quan Hệ Giữa Các Thành Phần

- **Employee** liên kết với **Payroll** để tính lương, ghi lại giờ làm việc và gửi đơn đặt hàng.
- **PayrollControl** quản lý quy trình tính lương và liên kết với **ProjectManagementControl** để truy vấn thông tin về dự án.
- **ProjectManagementControl** sử dụng **IProjectManagement** để truy vấn dữ liệu về dự án và liên kết với **ProjectManagementDatabase** để lấy thông tin từ cơ sở dữ liệu bên ngoài.
# 2. Analysis Class to Design Element Map

|  Analysis Class | Design Element |  
|-----------------|----------------|
| LoginForm | LoginForm|
| MaintainTimecardForm | MainEmployeeForm |
| TimecardController | TimecardController |
| PayrollController | PayrollController |
| PayCheck | PayCheck |
| BankService | BankService |
| SystemClockInterface | SystemClockInterface |
| PayrollController | PayrollControllerImpl |
| Employee | EmployeeEntity |
| Timecard | TimecardEntity |
| Payroll | PayrollProcessor |
| BankTransaction | BankTransactionProcessor |
| PaymentUI | PaymentUIComponent |
| PrintService | PrintServiceProcessor |
# 3. Design element to owning package map

| Design Element              | Owning Package                           |
|-----------------------------|------------------------------------------|
| LoginForm                   | Middleware::Security::GUIFramework      |
| MaintainTimecardForm        | Applications::Employee Activities       |
| TimecardController          | Applications::Employee Activities       |
| PayrollController           | Applications::Payroll                   |
| PayCheck                    | Business Services::Payroll Artifacts    |
| BankService                 | Business::Banking                       |
| SystemClockInterface        | Applications::Payroll                   |
| PayrollController           | Applications::Payroll                   |
| Employee                    | Data Access::Employee Management        |
| Timecard                    | Data Access::Employee Management        |
| Payroll                     | Business Services::Payroll Processing   |
| BankTransactionProcessor    | Business Services::Banking              |
| PaymentUIComponent          | Middleware::User Interface Components   |
| PrintService                | Middleware::Print Services              |


# 4. Architectural layers and their dependencies
## Biểu đồ mô tả các layers trong hệ thống và quan hệ giữa chúng
![Diagram](https://www.planttext.com/api/plantuml/png/V5BBRi8m4BpxArQvzCGFv51HG5ILYeeK-835MOWLFwBrKXHL_R8U-adzXPf7APIaXvKjpSpEQEolZyzX56JPEgjKWxh63K7sq3JMQ1GJF3nZIvp1cmBG5cE4R8uj1sl7mSl-JEWljZ2ED7BP2SxGU4dpGve6Tfbwlp0URQFnbBW5yQlH5FljvnmI7iEbmGXzlM3q4VK-UnSbgSSLwVgFwkHtdMPcojBI3fawOXIajsoapVF7vTEKqT4kS7tjvCZBycaSN1Dykbw2dAheD2tQAEIW26lfSPwWu0eZdULdP6ei7VMts4j3d5xKRuw4W-aTJ6YT2eUI6l8bUTr2PHAFTTN2ceC32KqQM0MHu5JNpnWCxlzvkFoqEqBmgfzsM7BRTmwfffH7IuITaKfrS0xIdjPkz6gOikm_-pS0003__mC0)
## Biểu đồ mô tả các lớp và mối quan hệ giữa các layer trong hệ thống

### 1. **Application Layer**
   - **PayrollController**: Xử lý các logic liên quan đến bảng lương và các chức năng tính lương.
   - **TimecardController**: Xử lý bảng thời gian và tính toán số giờ làm việc của nhân viên.

### 2. **Business Services Layer**
   - **PayrollProcessor**: Cung cấp các dịch vụ tính toán bảng lương, phụ cấp và thuế cho nhân viên.
   - **BankTransactionProcessor**: Xử lý các giao dịch ngân hàng, bao gồm chuyển khoản và các giao dịch tài chính khác.

### 3. **Middleware Layer**
   - **Security::GUIFramework**: Cung cấp các dịch vụ bảo mật cho hệ thống và giao diện người dùng (GUI).
   - **PaymentUIComponent**: Thành phần giao diện người dùng (UI) để xử lý các yêu cầu thanh toán và nhập thông tin thanh toán.
   - **PrintService**: Dịch vụ in ấn, bao gồm việc in phiếu lương hoặc báo cáo.

### 4. **System Software Layer**
   - **DatabaseService**: Quản lý kết nối và thao tác với cơ sở dữ liệu, lưu trữ và truy xuất thông tin.
   - **FileSystemService**: Quản lý hệ thống tập tin, bao gồm việc lưu trữ và xử lý các tệp tin.
   - **OperatingSystem**: Cung cấp các dịch vụ cơ bản của hệ điều hành, như quản lý tài nguyên hệ thống và hỗ trợ các ứng dụng chạy trên hệ thống.

### Mối Quan Hệ Giữa Các Layer:
- **Application Layer** phụ thuộc vào **Business Services Layer** để xử lý các nghiệp vụ tính lương và bảng thời gian.
- **Business Services Layer** sử dụng **Middleware Layer** để thực hiện các dịch vụ bảo mật, giao diện người dùng và in ấn.
- **Middleware Layer** cần tương tác với **System Software Layer** để truy cập cơ sở dữ liệu, hệ thống tập tin và các dịch vụ hệ điều hành.

