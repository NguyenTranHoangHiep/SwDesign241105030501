# 1. Use case Login:
## 1.1 Xác định các lớp và các operations:
![Diagram](https://www.planttext.com/api/plantuml/png/T99DJiCm48NtFiNi21AzG1Qe_8XLXP2Y7i1rfgqbnuCyaqHLnSbOS2IkG6piqgh1o-UNzpuzv_lpQycYW_ITKpVmZ5lh4OpJpCYmfG0hsbaFV631Jgbq0sl604S5yJGIhDz1FqclkiCByNqoZnJQNz75fEgsXaSYXzghZvANEXeJ47s9vJsDINwXqCMF1h8v1xrWMEU-gXJNkVJQ-fOfge8pQ-L-qrbP_SluqCj-YhD6YoNVO1YimK8xQ6TRBVWKi8qcxVWAx0vc-izgJkjFBZ8srJ1iKCOuItuIfTBsYyNznMXrt9_LkHGjyypr2PV1_04hjKJVnl_W1m00__y30000)
# 1.2 Xác định các thuộc tính và mô tả:
![Diagram](https://www.planttext.com/api/plantuml/png/X5JBQYCn4BpFL-YsNaZy0NC8yIO45X88SPAxaDgsM5azj5fZJDWloo6Vb5_O7et7Ew-GEGbrLLTNgPdFzu_ho9euxNrH6AzZL2yHIBqLIhuanz-sL6ic5xRdgw3tCBYiX7T0cYAVq0-Hei3tk7MXLBUQuTdjeVZRAUV2sX10E0tWGfNuPKuoLnxdT7tkmffJBDKlb0bqo0KWGdg06FNsVw-X-0q69lJ-d42jlRCow0s1XS1E-xWOHt0nyVzpABpJmNh80fbSvem5LAEpfvdDdvKnc08lXg7tKH62NOD9vFYuaXc_mfuzTU077SHpvmc2eMDr3cynCtqlpXh8ROxF1xpJXf56aXVAe8KlV9iTP5iI-JtKu8VcEwHC-qEjOaJZD3iCBK0Uc854Cgg3urr_DufSlxoy6YnCgHu9QsSXjXkWBB1sFZRTRw6IwCJtiHnmca2ZalVLYd6y0KKVkLnUJJP4N6V-IKwwp6hr6E9_-YWR9AKJxvhrCZc1OinhrCUq75ESOIlPDd7MeYVPZbjt2nupBLNjERKliC79A4tiEVzIlNv3BQubYER7yWy00F__0m00)
## 1.2.1 Mô tả các thuộc tính

## User (Người dùng)
- **userId: String** - Mã định danh duy nhất cho người dùng.
- **username: String** - Tên đăng nhập của người dùng.
- **password: String** - Mật khẩu được mã hóa của người dùng.
- **userRole: String** - Vai trò của người dùng (ví dụ: Sinh viên, Giảng viên).
- **lastLogin: DateTime** - Thời gian đăng nhập gần nhất của người dùng.

## LoginScreen (Màn hình đăng nhập)
- **inputUsername: String** - Trường để người dùng nhập tên đăng nhập.
- **inputPassword: String** - Trường để người dùng nhập mật khẩu.
- **loginStatus: Boolean** - Trạng thái đăng nhập (`true` nếu thành công, `false` nếu thất bại).
- **errorMessage: String** - Thông báo lỗi khi đăng nhập không thành công.

## LoginController (Bộ điều khiển đăng nhập)
- **validateCredentials(username: String, password: String): Boolean** - Kiểm tra tên đăng nhập và mật khẩu.
- **handleLogin(user: User): void** - Chuyển hướng người dùng sau khi đăng nhập thành công.
- **lockAccount(userId: String): void** - Khóa tài khoản sau nhiều lần đăng nhập thất bại.
- **sendSecurityAlert(userId: String): void** - Gửi cảnh báo bảo mật khi có hành động đáng ngờ.

## SecurityManager (Quản lý bảo mật)
- **encryptPassword(password: String): String** - Mã hóa mật khẩu trước khi lưu trữ hoặc kiểm tra.
- **verifyTwoFactor(userId: String, code: String): Boolean** - Xác minh mã hai yếu tố (2FA).
- **checkAccessLevel(user: User): Boolean** - Kiểm tra quyền truy cập của người dùng.

Mô tả:
# 1.3 Xác định các mối quan hệ và phụ thuộc:
## Các Mối Quan Hệ Giữa Các Lớp

### 1. **User ↔ LoginScreen**
   - **Mối quan hệ**: **Association** (Liên kết)
   - **Giải thích**: `LoginScreen` cung cấp giao diện để người dùng nhập tên đăng nhập và mật khẩu. Sau khi người dùng nhập thông tin, hệ thống sẽ kiểm tra thông tin người dùng thông qua lớp `User`.
   - **Loại mối quan hệ**: `LoginScreen` liên kết với `User` vì người dùng thực hiện hành động đăng nhập thông qua `LoginScreen`.

### 2. **LoginScreen ↔ LoginController**
   - **Mối quan hệ**: **Dependency** (Phụ thuộc)
   - **Giải thích**: `LoginScreen` sẽ gửi thông tin (tên đăng nhập và mật khẩu) từ người dùng tới `LoginController` để xác thực và xử lý đăng nhập.
   - **Loại mối quan hệ**: `LoginScreen` phụ thuộc vào `LoginController` vì `LoginScreen` cần `LoginController` để xử lý và kiểm tra thông tin người dùng.

### 3. **LoginController ↔ SecurityManager**
   - **Mối quan hệ**: **Dependency** (Phụ thuộc)
   - **Giải thích**: `LoginController` cần `SecurityManager` để mã hóa mật khẩu và kiểm tra tính hợp lệ của các thông tin bảo mật như mã hai yếu tố (2FA).
   - **Loại mối quan hệ**: `LoginController` phụ thuộc vào `SecurityManager` để thực hiện các thao tác bảo mật như mã hóa mật khẩu và xác minh quyền truy cập.

### 4. **LoginController ↔ User**
   - **Mối quan hệ**: **Association** (Liên kết) / **Dependency** (Phụ thuộc)
   - **Giải thích**: `LoginController` xác thực thông tin của người dùng, bao gồm việc kiểm tra tên đăng nhập, mật khẩu, và vai trò người dùng. `LoginController` cũng có thể cập nhật trạng thái đăng nhập của `User`.
   - **Loại mối quan hệ**: `LoginController` liên kết với `User` vì lớp này phụ thuộc vào thông tin người dùng để thực hiện các chức năng xác thực và xử lý đăng nhập.

# 1.4 Xác định các trạng thái chính:
![Diagram](https://www.planttext.com/api/plantuml/png/P90n3i8m34NtdC8pKY_GWGa69BOA5iHWDQP4IjtAJa4z6mD7uWeaBOMARfRrdltrNu_dQNM6B5l3lgaS5wKGCUHGz1ge1kkqzTWhX2k1JmJeW9WvdlGZUcSnEAwYVL0I80ua2bsS6Mi2P0ijgjuRiMQ69xleof9KF-e21nI2MrBCH2OhHS_7uA3Z_j9vytzyAz9817SydFWbYjjle15Q5h6P6g01gECFhCYy0G00__y30000)

# 2. Use case Run Payroll:
## 2.1 Xác định các lớp và các operations:
![Diagram](https://www.planttext.com/api/plantuml/png/T5BDIWCn4BxlKmIyr4EXWXxSWtIjBVIW21KypoPZ6vfabcHMMCKdy-0Z-GecwswbstK32vdlP-ORyltvDGyCdcjhih3NhW8FLaW38HJCNfSrurgIs-Wt5BCXPKMEM-JYSWnw08kYy1fEl5iXDmP5IKODqLkG-wsdsga56VBYR7MTpWcDl4BVKMQpgsLHP5cBYAMj33M8uZqJySFkkbQvsCHKRjkMNPplg511Oz7nFVAEr1YoIExwHKjWJUw88S78sW3Z8pIJyrpSKLqQp3xwaPwqHGbUTIEfo8oa-4z0MzfHxSCp-JsgKtbqzMHCeQnsEh07Zgb_hK2fFk-aJveVLX17UIMjMgQlNUSpwSl31ficCDhEkV8aCOGHpM71q-dDNxHSXBgqceFWhXIoOzz4FsZplW66jE14oqPp3bGM76oZfW-RbWd_AuydoDCM_lhDqQdq-7y0003__mC0)
## 2.2 Xác định các thuộc tính và mô tả:
![Diagram](https://www.planttext.com/api/plantuml/png/b5LjZjCm4FsVKrZzrPNe7Y12guLb5o6X5I9xWS6PBTRwex8d5H7YPFpWI5o1EBMJYTE2w9z6dlVUl9dn9Bz__heD19uwewjAQWX1V8BUEwtldANuZrvyhyJuyvrDmUrLBOvEjJc0v1KUyTuSjEiH4-eT4YWT8lYZ2lGwXsyIROyMFL26VyQ3yrH8Iz2oqmEeq8wmuJ6bIE23Tn936CuDMigCBQQ7MkIZL-8mSRdEClTNiAt6neG6DFZ-BbbHpXOcMzGuEpoJByD_i2P7Ymtwev8uTLXPHUhKaHZ-F-TlmRuyUR01PFIO98_erNCVOs-aTDrPqKXsJYFOsM5aD7qWD9Exr5wMOqlpyyh09LK6IT8xmNG-jBLeXljazoa69jgknODsGFdiLCjZPxwWB_1CQseK0yHxHqyhJ1pf0eNVK7Q4lDfp5UKUbgCSakHGpf0RFrTuDSzWJIksw2nxjGBJlYJstoybewyAccR34okR9s31OD7uCAu97zHOptllnfsCxIj2ZqYB0D-FPEmVDlP9V7azMcoxSMHXUMx7V2pR-cKdThiRKUvdBJPTmB2vY2zl0ITmeHEQxTO0DF228Qvr10focwfK6rdJN0PAVk662rZUloMSfHRNryaBtyW1dlOymtdqnE5MrkwhMxHj_A3y0G00__y30000)
### Lớp: PayrollController
- **Phương thức:**
  - `runPayroll()`: Chạy quy trình tính lương.
  - `retrieveEmployeePayrollDetails()`: Lấy thông tin chi tiết lương của nhân viên.
  - `generatePayrollReport()`: Tạo báo cáo lương.
  - `calculateEmployeePayroll()`: Tính lương cho một nhân viên.
  - `processPaymentEmployee(employee, payDetails)`: Xử lý thanh toán cho một nhân viên.
  - `handleSmsSalaryCalculation()`: Xử lý tính toán lương qua SMS.
  - `deleteEmployee(employee)`: Xóa thông tin nhân viên.

### Lớp: PaymentService
- **Phương thức:**
  - `initiatePayment(employee, payDetails)`: Khởi tạo việc thanh toán cho nhân viên.
  - `verifyBankAccount(employee)`: Xác thực tài khoản ngân hàng của nhân viên.

### Lớp: BankSystem
- **Phương thức:**
  - `processTransaction(transaction)`: Xử lý giao dịch ngân hàng.

### Lớp: BankTransaction
- **Thuộc tính:**
  - `transactionId`: Mã giao dịch duy nhất.
  - `amount`: Số tiền trong giao dịch.
  - `accountNumber`: Số tài khoản của giao dịch.
  - `transactionDetails`: Chi tiết giao dịch.
- **Phương thức:**
  - `getTransactionDetails()`: Trả về chi tiết giao dịch.
  - `executeTransaction()`: Thực hiện giao dịch.

### Lớp: EmployeeService
- **Phương thức:**
  - `getEmployeeDetails(employeeId)`: Lấy thông tin chi tiết nhân viên theo mã nhân viên.
  - `getEmployeePayrollDetails(employeeId)`: Lấy thông tin chi tiết lương của nhân viên theo mã nhân viên.
  - `calculatePayrollEmployee(employee)`: Tính toán lương cho một nhân viên.

### Lớp: Employee
- **Thuộc tính:**
  - `employeeId`: Mã nhân viên duy nhất.
  - `name`: Tên nhân viên.
  - `salary`: Mức lương của nhân viên.
- **Phương thức:**
  - `getGrossPay()`: Trả về tổng lương trước thuế của nhân viên.
  - `getNetPay()`: Trả về lương thực nhận của nhân viên sau khi trừ thuế và các khoản giảm trừ.

### Lớp: PayDetails
- **Thuộc tính:**
  - `employeeId`: Mã nhân viên.
  - `grossPay`: Tổng lương trước thuế.
  - `deductions`: Các khoản giảm trừ.
  - `netPay`: Lương thực nhận sau khi trừ các khoản giảm trừ.

## 2.3 Xác định các mối quan hệ và phụ thuộc:
### 1. **Quan hệ giữa PayrollController và PaymentService**

- **Giải thích**: `PayrollController` sử dụng `PaymentService` để thực hiện các giao dịch thanh toán cho nhân viên. Khi payroll được chạy, hệ thống sẽ cần liên kết với dịch vụ thanh toán để xử lý việc chi trả tiền lương cho nhân viên.
  
- **Loại quan hệ**: **Sử dụng (Uses)**  
  - `PayrollController` không sở hữu `PaymentService`, mà chỉ sử dụng nó để thực hiện các chức năng liên quan đến thanh toán.


### 2. **Quan hệ giữa EmployeeService và Employee**

- **Giải thích**: `EmployeeService` lấy thông tin chi tiết về nhân viên từ đối tượng `Employee`, bao gồm các dữ liệu về lương, thông tin cá nhân, và các yếu tố liên quan đến việc tính toán tiền lương.
  
- **Loại quan hệ**: **Lấy thông tin (Retrieves)**  
  - `EmployeeService` cần lấy dữ liệu từ `Employee` để thực hiện các thao tác như tính toán lương, truy xuất thông tin cơ bản của nhân viên.

### 3. **Quan hệ giữa BankSystem và BankTransaction**

- **Giải thích**: `BankSystem` phụ thuộc vào `BankTransaction` để thực hiện các giao dịch thanh toán. Khi thực hiện một giao dịch thanh toán cho nhân viên, hệ thống ngân hàng sẽ sử dụng thông tin trong `BankTransaction` để xử lý.
  
- **Loại quan hệ**: **Phụ thuộc (Depends)**  
  - `BankSystem` phụ thuộc vào `BankTransaction` để thực hiện các giao dịch thanh toán, nghĩa là `BankSystem` không thể hoàn thành nhiệm vụ nếu không có `BankTransaction`.


## 2.4 Xác định các trạng thái chính:
![Diagram](https://www.planttext.com/api/plantuml/png/R92n2i9038RtF4LceI_GGSJMmK4efPiuXBjWZrxJShqRV3O77ybNi54wjBY4_7_o_P2ydw_352d4r7kuxcwOPNiyMyy0Mh-oJY9ExXKzmk0zvhXqZUiPQoRJieNDbe85UPCynPyzWul16W6RiH9LSAAwQDbqCt0Xvt48M3dJPMdyXnn9kYQGJ6IY6sI6IXVOH2nv72ONOPsfYDwPuqaiRE7r50uiLX_p0G00__y30000)
