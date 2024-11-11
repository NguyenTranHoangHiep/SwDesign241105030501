# 1. Phân tích các ca sử dụng còn lại trong hệ thống Payroll System

## 1.1 Phân tích ca sử dụng login

### 1.1.1 Các lớp phân tích

- **Boundary**: `LoginScreen`
- **Entity**: `User`
- **Control**: `LoginController`

### 1.1.2 Nhiệm vụ các lớp phân tích

#### `LoginScreen` (Màn hình đăng nhập)
Đây là lớp giao diện người dùng, nơi người dùng sẽ nhập tên đăng nhập và mật khẩu của mình. Sau khi người dùng thực hiện thao tác đăng nhập, `LoginScreen` sẽ hiển thị thông báo về kết quả đăng nhập, bao gồm thông báo thành công hoặc lỗi.

#### `User` (Người dùng)
Lớp này đại diện cho người dùng trong hệ thống, lưu trữ các thông tin như:
- Tên đăng nhập (`username`)
- Mật khẩu (`password`)
- Vai trò của người dùng (`role`)
- Các thông tin khác liên quan đến người dùng trong hệ thống.

#### `LoginController` (Điều khiển đăng nhập)
Lớp `LoginController` có trách nhiệm:
- Kiểm tra tính hợp lệ của thông tin đăng nhập (username, password).
- Liên kết với lớp `User` để xác minh thông tin người dùng.
- Trả về kết quả (thành công hoặc lỗi) cho lớp `LoginScreen` để người dùng nhận thông báo phù hợp.

### 1.1.3 Biểu đồ Squence

![Sequence Diagram](https://www.planttext.com/api/plantuml/png/d98nIyD05CVt-nHlLD0la44AHYfKkbZ1zPeSoT7aNRnSgXsbWuEJavFGqacXuE1YR-YGulUuJ-1NyAvH4qiHDCFnUFpVx_z_ZxphPIjNLAeYJGWDb93GZTwUZNxWVlcA4T0Spd8cILyK658vWZQdmkSCVOfHDwQPKvo8YEDf81b34WXKKYHWDKKdtYOyh1I9fJ9KN8siPI6uNzHsH-i-8Qw6_OEcWGVTs2pc6QZo2M5rjnhRCQnQmt82gQqK36pZiI2DkMzCRUz1s-Wv1nMNBnQY-0QFREWTeaxdGOSRFKv1ITf4uEVz85mVSAUm4qXJjWSPpVDB8SDTKbEsnkf9ivZ1qEXh69Z5Ki55uHfNvJI0b6DC24qKz6hFsEXP1edHDmJijoNtZmkUEz1wnyqBsZqc64FWo3Mglg0Bxi6nMnojsEZRhzNxvLJy1cD9pfgH1rNvn-IzXfaTkkV_25dDCGm9QTdN_VaV0000__y30000)
