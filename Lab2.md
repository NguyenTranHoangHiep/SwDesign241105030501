# 1. Phân tích các ca sử dụng còn lại trong hệ thống Payroll System

## 1.1 Phân tích ca sử dụng login

### 1.1.1 Các lớp phân tích

- **Boundary**: `LoginScreen`, `Database`
- **Entity**: `User`
- **Control**: `LoginController`

### 1.1.2 Nhiệm vụ các lớp phân tích

#### `LoginScreen` (Màn hình đăng nhập)
Lớp **LoginScreen** đại diện cho giao diện người dùng, nơi người dùng sẽ nhập tên đăng nhập và mật khẩu của mình. Sau khi người dùng thực hiện thao tác đăng nhập, lớp này sẽ gửi thông tin đến lớp **LoginController** để xác thực. Sau khi nhận kết quả từ lớp điều khiển, **LoginScreen** sẽ hiển thị thông báo về kết quả đăng nhập cho người dùng, bao gồm thông báo thành công hoặc thông báo lỗi nếu thông tin không hợp lệ. **LoginScreen** cũng có thể trực tiếp truy cập cơ sở dữ liệu để xác thực người dùng trong trường hợp này.

#### `User` (Người dùng)
Lớp **User** đại diện cho thông tin người dùng trong hệ thống. Lớp này chứa các thuộc tính như:
- Tên đăng nhập (`username`)
- Mật khẩu (`password`)
- Vai trò người dùng (`role`)
- Các thông tin cá nhân khác liên quan đến người dùng trong hệ thống.

Lớp **User** sẽ chỉ là đối tượng dữ liệu và không chịu trách nhiệm trực tiếp về việc truy cập cơ sở dữ liệu.

#### `LoginController` (Điều khiển đăng nhập)
Lớp **LoginController** chịu trách nhiệm xử lý logic đăng nhập. Các nhiệm vụ chính bao gồm:
- Kiểm tra tính hợp lệ của thông tin đăng nhập (username, password).
- Liên kết với lớp **User** để xác minh thông tin người dùng.
- Trả về kết quả cho **LoginScreen** để hiển thị thông báo cho người dùng.

#### `Database` (Cơ sở dữ liệu)
Lớp **Database** không còn thuộc **Entity** nữa mà sẽ nằm trong **Boundary**, vì nó có nhiệm vụ trực tiếp tương tác với lớp giao diện người dùng để xác thực thông tin đăng nhập. **Database** sẽ truy vấn thông tin từ bảng người dùng và trả về kết quả (true/false) về tính hợp lệ của thông tin đăng nhập.

### 1.1.3 Biểu đồ lớp
![Class Diagram](https://www.planttext.com/api/plantuml/png/f9B1JiCm38RlUOgefu7OOTUTqAW4qaOlvC3LZ2YnQ1tK9XFJj2VRWKVY5OYg9XbD9K3B9PRps_viv-lqUTjPQArhQhQjeUjufPp1qf7Y1yRxOoMLGAhIyBxaJxP5KiDB0tQjmOsyv8L26r82O-1i8idDEFvgoNS6NzcH3Ipt2AR451cHj7SAZNsL5HYXWVITjsSXnQHiOt0aK0ul8lrHvX7e0Kd7HB-nPCBOj-_PhVLKusye6z52W8xB-YlrofXQ0WtPFc3h0-WS90WI2rXuWKuc16chR92sTVjd1xPq6y_-NnfVB7sxOb7m-Ro_ilspp5DSHtK-DPQxplMXCnQjKDkB4X3x1W00__y30000)
### 1.1.4 Biểu đồ Squence
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/d5A_IWCn6D_p5DzeGN6_GGfM52fThE2QtiMxqEkNcalKZkBWuDJ9GKIBE2Y82e9u6HnE-Xvv0b_1v6fjBKN1BVpo-vVlouTvgsQAIgKxAQ6X4XAsCoP9IsYCgEp1EgUYnXdMACQDX7Q1Ph0fOevReMGCIIXGIP62u-XwCe-uEcAapfMXuge7ZLWBNjCOUuwFMojn4b55MpHZKFiw4E9lOMbbEZA0HcBp-oweuWxXlVz-x8nm1EqNLz1n9mLj1zngCgNxjfaK2c3TcdiEAYcUdOdYCtvaXkyjnjq2gDlyJG5Qq-UmRyqvXt0uWCoQIuYiUO2KMtEYoLWmDxyfRNxjrKVGBktsj0VQ4-lVEpIbxZbvVeFJZy1u-6ZD1OUeU7NGWdPJHDfXYz2bMNOWP5JvLwt3OX2w76kUGbXGKhFbNPfch3Aluu-DxNXXETFPZRdMLvX0M7PFXCrVml5BMiL0G6hD6PzTe_yL0Mou-HvZsUVqX-RlX94hgJAC_CV_1000__y30000)
## 2.1. Phân tích ca sử dụng Create Administrative Report

### 2.1.1. Các lớp phân tích:
- **Boundary**: `AdministrativeReportForm`, `ProjectManagementDatabase`
- **Control**: `AdministrativeReportController`
- **Entity**: `Report`

### 2.1.2. Nhiệm vụ của từng lớp phân tích:

#### `AdministrativeReportForm`:
Lớp **AdministrativeReportForm** chịu trách nhiệm hiển thị giao diện người dùng và các trường nhập liệu để người dùng có thể điền thông tin báo cáo. Lớp này tương tác với người dùng, nhận thông tin từ họ và gửi yêu cầu tạo báo cáo.

#### `ProjectManagementDatabase`:
Lớp **ProjectManagementDatabase** thực hiện chức năng truy xuất thông tin từ cơ sở dữ liệu về các nhân viên (employee) và các báo cáo đã có. Lớp này sẽ cung cấp dữ liệu cần thiết để tạo ra báo cáo hành chính.

#### `AdministrativeReportController`:
Lớp **AdministrativeReportController** xử lý các logic và điều khiển tạo báo cáo hành chính. Nó sẽ nhận thông tin từ lớp **AdministrativeReportForm**, yêu cầu **ProjectManagementDatabase** truy xuất dữ liệu, và cuối cùng tạo ra báo cáo dựa trên dữ liệu đó.

#### `Report`:
Lớp **Report** đại diện cho báo cáo hành chính, chứa các thông tin liên quan đến báo cáo như tên báo cáo, dữ liệu báo cáo, và các phương thức để xử lý báo cáo.

### 2.1.3. ![Class Diagram](https://www.planttext.com/api/plantuml/png/Z5BBJiCm4BpxArOv0L8ElVPKbC8DL1L-O4bNaS6FQBsjL26-Z4C_gR-0OmUhLKb5BgkCTsTsnZv-7nP1a6LhZLBXGpjW7qWfqM886YOKWlkDrKu7OHIz8rXJxrcWXiPW2B3Ks35QfThqUzwSUnyzM_XK46Su0Q_xdc0EByBQTGbFMom7jJaC9O7aDXUGxOtV4psZFMC0w4YoMiDQY3NUt0AehsjxDTu9UsE8qtO0RJAS3zFu00RS5IXteMl95AX8ZC5aep9jyTBXXC4oNYHMxD-fbITqs94bD_3X6mOQ3SGG7au8ydQJLrBDAgZhLAx7yoV5INg_H7VL6C9_1sAPjAJYjuW1nRVv0m00__y30000)

### 2.1.4. ![Sequence Diagram](https://www.planttext.com/api/plantuml/png/f5DBJiCm4Dtx5BCi4Rr05wYq0NK15G9nW6aoQWs97Pn9KTOiEGKh9AHAhCc2HINkaHDm1PnFLJS2jH8Rnv7VctdpdlrTV0vJHiDP70cHtai5HgSa14kE2CQ6a0bEmrWgcR91bak2QqgqOUZ33Jraf082N-BSO2m41gmDtAPan4ndAaIJTzWD-LoR6325wYi2hTZew5VWk3cBo5JmxPyWPINchHOH8kCCKu8he-yeu4jKEAVOWlpDYQNx8o4gRT0_gJl30AQBycEL0ClrMmR1Ohs2sVf5Gs0NKKCirD4mWA2sf6dRCur68vcCnADgVBci77E4EcnRon_P6dFYipY9T4uqnPXw3j5Aj91-joivS16I2z-jtsOp0CzJzEXvFSuJEeOwOsk5tP8AsurJqr7GEhe9kQl4xTv2NGLRPoUoB9uKyA8idXrJ7RfZKZUMYw_tR5yIAIvtSpZ4VyUVYcyD-jVeXqqpAOlNVE_5GlkIedQW_QDig_ybGWnjrFPT_m000F__0m00)
## 3.1 Phân tích ca sử dụng Create Employee Report
### 3.1.1 Các lớp phân tích, nhiệm vụ,thuộc tính và quan hệ giữa các lớp phân tích
### 1. **Boundary**

### a. **EmployeeReportForm**
- **Nhiệm vụ**:
  - Cung cấp giao diện cho nhân viên nhập thông tin cần thiết để tạo báo cáo (ví dụ: tiêu chí báo cáo, khoảng thời gian).
  - Thu thập dữ liệu đầu vào từ người dùng.
  
- **Thuộc tính**:
  - Không có thuộc tính cụ thể (hoặc có thể là thông tin giao diện như các trường nhập liệu).
  
- **Phương thức**:
  - `displayForm()`: Hiển thị giao diện nhập liệu cho người dùng.
  - `getInput()`: Thu thập thông tin từ người dùng (ví dụ: ngày bắt đầu, ngày kết thúc, loại báo cáo).

### b. **SaveReportForm**
- **Nhiệm vụ**:
  - Cung cấp giao diện để người dùng lưu báo cáo với tên và vị trí.
  - Thu thập thông tin về tên báo cáo và đường dẫn lưu báo cáo.
  
- **Thuộc tính**:
  - Không có thuộc tính cụ thể (hoặc có thể là tên báo cáo và vị trí lưu).
  
- **Phương thức**:
  - `displaySaveForm()`: Hiển thị giao diện lưu báo cáo.
  - `getSaveDetails()`: Thu thập tên báo cáo và vị trí lưu từ người dùng.

---

## 2. **Entity**

### a. **EmployeeReport**
- **Nhiệm vụ**:
  - Đại diện cho báo cáo nhân viên, lưu trữ các thông tin về báo cáo và xử lý các hành động liên quan (tạo, lưu, hủy bỏ báo cáo).
  
- **Thuộc tính**:
  - `reportData`: Dữ liệu của báo cáo (ví dụ: bảng thống kê, nội dung báo cáo).
  - `reportName`: Tên báo cáo (ví dụ: "Báo cáo doanh thu tháng 10").
  - `saveLocation`: Đường dẫn hoặc vị trí lưu báo cáo.
  
- **Phương thức**:
  - `generateReport(criteria)`: Tạo báo cáo dựa trên các tiêu chí nhập vào từ người dùng (ví dụ: báo cáo theo tháng, báo cáo theo phòng ban).
  - `saveReport()`: Lưu báo cáo vào hệ thống (có thể lưu vào cơ sở dữ liệu hoặc file hệ thống).
  - `discardReport()`: Hủy báo cáo nếu không lưu, hoặc khi người dùng không muốn giữ lại báo cáo.

### b. **EmployeeReportDatabase**
- **Nhiệm vụ**:
  - Quản lý việc lưu trữ, truy xuất và xóa báo cáo từ cơ sở dữ liệu.
  
- **Thuộc tính**:
  - Không có thuộc tính rõ ràng (có thể là thông tin kết nối đến cơ sở dữ liệu).
  
- **Phương thức**:
  - `storeReport(reportData)`: Lưu báo cáo vào cơ sở dữ liệu.
  - `retrieveReport(reportName)`: Truy xuất báo cáo từ cơ sở dữ liệu theo tên báo cáo.
  - `deleteReport(reportName)`: Xóa báo cáo khỏi cơ sở dữ liệu.

---

## 3. **Control**

### a. **EmployeeReportController**
- **Nhiệm vụ**:
  - Điều khiển các quy trình tạo, lưu và hủy bỏ báo cáo.
  - Điều phối giữa các lớp **Boundary** và **Entity**.
  
- **Thuộc tính**:
  - Không có thuộc tính rõ ràng.
  
- **Phương thức**:
  - `generateReport()`: Xử lý yêu cầu tạo báo cáo từ người dùng, gọi phương thức `generateReport()` của lớp `EmployeeReport`.
  - `saveReport()`: Xử lý yêu cầu lưu báo cáo, gọi phương thức `saveReport()` của lớp `EmployeeReport`.
  - `discardReport()`: Hủy bỏ báo cáo nếu người dùng quyết định không lưu lại, gọi phương thức `discardReport()` của lớp `EmployeeReport`.

---

## 4. **Quan Hệ Giữa Các Lớp**

- **EmployeeReportForm -- EmployeeReportController (1-1)**:
  - `EmployeeReportForm` cung cấp giao diện người dùng để nhập thông tin, và sau đó truyền thông tin này cho `EmployeeReportController` để xử lý.

- **EmployeeReportController -- EmployeeReport (1-1)**:
  - `EmployeeReportController` điều khiển quá trình tạo, lưu, và hủy bỏ báo cáo, và sẽ gọi các phương thức tương ứng trong lớp `EmployeeReport` để thực hiện các thao tác này.

- **EmployeeReportController -- SaveReportForm (1-1)**:
  - `EmployeeReportController` cung cấp giao diện để lưu báo cáo thông qua lớp `SaveReportForm`. Sau khi báo cáo được tạo, lớp điều khiển sẽ yêu cầu người dùng lưu báo cáo.

- **EmployeeReportController -- EmployeeReportDatabase (0..1)**:
  - `EmployeeReportController` có thể hoặc không kết nối với cơ sở dữ liệu (nếu báo cáo cần lưu trữ vào cơ sở dữ liệu). Mối quan hệ này là **0..1**, có thể có hoặc không có kết nối.

- **EmployeeReportDatabase -- EmployeeReport (1 - 0..*)**:
  - Lớp `EmployeeReportDatabase` lưu trữ nhiều báo cáo nhân viên, vì vậy mối quan hệ là **1 - 0..***.
### 3.1.2 Biểu đồ lớp
![Class Diagram](https://www.planttext.com/api/plantuml/png/Z9DHJiCm38RVSufeBnj8dU064zsGa10FumIcjLYaDAbiTwYQE1aF78ahqAIbsrYxxIcrdT__LoVv-VfUi019LLYbflh1Lou7gdLgWHbPPM7LgwAqlaPSO-b97ZqLUgUqrhdXqa8T4hERa7X7UN9b9KtqgJhnAsp7XA5q90w99GeOossBgLuvCT813UB4ZWd5xoK8xACNA314t7HzzXc8yQurSaWWdNwMaH4a0n62UzeMgY7DWF8-5PbIxuIyjKXdk0usxGPShtSBF_K6Z6Uy-YtHYSNJNzlzNA81eP31xN4rpAcrHuioL8iSQxHnXBmn9UiF8nkTDh36WMrEI0rSaidzH2T9N4PdeqOhe-hhDF_ktMNDtNn-OjKFLeta3yItfvngWIuFR-iN003__mC0)
### 3.1.3 Biểu đồ Squence
![Squence Diagram](https://www.planttext.com/api/plantuml/png/f9EnRi8m48PtFyM9YGvzWKgf4D1AbIg6jaDNOomIATYHSudACtJY3Q1iI4XKwaI63aQyHvwWhr0x54EJqAhgSeDz_-Ux_yuVsNihHgem6OM4CfGAhaPHACUS0usXqVFrYu0qq0lH8AGl4p6WQknoxdWa5LvBDI9C2bGoB5rrTgSXLuGB3B0iFI3lQNgCgytkKgHz6dD2F0yUylLCGbkRqB71yuWh_VoofaIuW9wVhvSHeA_Vn10m4D2tKcO2gH5KC8Ts36p8yKP42JRFoCci2g7G2QueVXqqcGgGgu2MARNQNTEkQ1ZasIi5L6O-fXszI83vUbaX_Tn8s-4s4pq7BDvuac9O-7oxNIMdRVu-jYEBRKMfdaAQPy-sm2M45dJmkwJyrMkRt-L8Wp3-g-EnUwgYhERlbypgp7_O2vMxB2ESe6gpOJpg6GDXJH4x1ypoJOLlF30h-Bz1RIRRLPxDMS4bfCN5m7xZJm000F__0m00)


