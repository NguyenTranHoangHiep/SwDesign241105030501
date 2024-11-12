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

### 4.3. ![Class Diagram](https://www.planttext.com/api/plantuml/png/Z5BBJiCm4BpxArOv0L8ElVPKbC8DL1L-O4bNaS6FQBsjL26-Z4C_gR-0OmUhLKb5BgkCTsTsnZv-7nP1a6LhZLBXGpjW7qWfqM886YOKWlkDrKu7OHIz8rXJxrcWXiPW2B3Ks35QfThqUzwSUnyzM_XK46Su0Q_xdc0EByBQTGbFMom7jJaC9O7aDXUGxOtV4psZFMC0w4YoMiDQY3NUt0AehsjxDTu9UsE8qtO0RJAS3zFu00RS5IXteMl95AX8ZC5aep9jyTBXXC4oNYHMxD-fbITqs94bD_3X6mOQ3SGG7au8ydQJLrBDAgZhLAx7yoV5INg_H7VL6C9_1sAPjAJYjuW1nRVv0m00__y30000)

### 4.4. ![Sequence Diagram](https://www.planttext.com/api/plantuml/png/f5DBJiCm4Dtx5BCi4Rr05wYq0NK15G9nW6aoQWs97Pn9KTOiEGKh9AHAhCc2HINkaHDm1PnFLJS2jH8Rnv7VctdpdlrTV0vJHiDP70cHtai5HgSa14kE2CQ6a0bEmrWgcR91bak2QqgqOUZ33Jraf082N-BSO2m41gmDtAPan4ndAaIJTzWD-LoR6325wYi2hTZew5VWk3cBo5JmxPyWPINchHOH8kCCKu8he-yeu4jKEAVOWlpDYQNx8o4gRT0_gJl30AQBycEL0ClrMmR1Ohs2sVf5Gs0NKKCirD4mWA2sf6dRCur68vcCnADgVBci77E4EcnRon_P6dFYipY9T4uqnPXw3j5Aj91-joivS16I2z-jtsOp0CzJzEXvFSuJEeOwOsk5tP8AsurJqr7GEhe9kQl4xTv2NGLRPoUoB9uKyA8idXrJ7RfZKZUMYw_tR5yIAIvtSpZ4VyUVYcyD-jVeXqqpAOlNVE_5GlkIedQW_QDig_ybGWnjrFPT_m000F__0m00)

