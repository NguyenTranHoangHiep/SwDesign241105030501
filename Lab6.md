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
![Diagram](https://www.planttext.com/api/plantuml/png/f5LTRjGm47xFAVoubUW58bGLoeygLHKYlS3W38jL_wpioOe8SJ8UE19N84xipJWnI8XzsSZp_Nbc9_lhny_RGE1fCBgH6a8G7s3qJkixPob-enVV6X4_Vh2fThXgnTcfFfqZUOLdV6jEses82VG62PGE4VkW0htCvPk5TKIB7YYZF-B9UIg59MWvw0cpKOwewJ4PBDYJTn93c8uDMZfWOhGYSr-8quN2wONZ5x2znivqeC6FTybVELi6wr7ZcgfYbj7VcxMfCLU7_gmaveuggqWjFVZtrA_1FZzvi05aJBWedj6hpsCilPBI3LNDo7LE8zWrNsHqOo0qELjgA7CuqFgyisUY_ns4oUOqpFg-RqKt_UBiSIc1YVAjUASTK3fQB1y7ymbzYMP2bxRo-X7fQGU9q-SW_8fo8EIzgTqbttCpzSaYLx9-xirwjwkrJJlMPi6gvEr-N7Ofxr1r78orkqMEp-sKJHstOB3iKPXNg1ZBT8NttirB6ljLLXwHYdE-EYdJNnCSatAXssC_pFC9nR6TlPZJ_frtVNspNTfM30737x3RMRV2m3E6kBvHGv1hDdAHnTPkLQ-1-4fKf9bEdP6sUJBO1kNX9s1-cTU1R1Orw1up9srkqVRn3-Ot0000__y30000)
## 2.2 Xác định các thuộc tính:
![Diagram](https://www.planttext.com/api/plantuml/png/V5HjQi904FsVK-m5Ue5GHAqj58e8Ue5nCqZeViZEh3IKdgm_UgHUePjaa-n6hJyKthnvR-RjuE_tpv8O77kj2gc0IEoWSLQf9sku_KKdFWiHFj8xXuOtm5YAzhj3KP-LRH3fO4DZATvguiVd22uwoXcQ3JBKYjfYfEn6S55y5PEr3XPxT9TQOlGzHv21FPLYpwusfxIIJ3GghS6y7nmO0icrDL6A9-IrogH0Ms_2R2_A0lU8b2sqzVg8BkCcAd65iPpvxnjYrDVM52EOpTY7LLFVjhe4OJYgiDdQMeLW9l4XtZmdJ-YIWFCt69vf77WeNwj6kQ6Z3Qesd65Rq9X5Gg30DMby5LP-s7P2Zs7bLHzirc-Gk-lfcUazn87_6UhaB57IVT_zokNwr1yU5lChBDjagPYXBN5-PAMG3iCPKZ6l3Enu4XFnzWGPTN2_mHkVh1Ju8PMlxZAJ9AFY_8XcUXeCd6xJKYq9IdhLhR94KuL_aJy0003__mC0)
## 2.3 Xác định các mối quan hệ và phụ thuộc:
![Diagram](https://www.planttext.com/api/plantuml/png/V5DRQiCm4FptAVIPGd81KqBw2WHAAKqliCWR8wg7MQqDflHa_UYHUeLAiPGuTgW_RB4pEpiUIR_VFnlFGDmQNKWDtejNwCbf_U0ino-I-2n4UAYr2LhSbA9pgZgMQxH8m9YmDsmSyGL3WfQj7YWBD8rsFM8fdj8gK0FmY0nA--AhEDimQ7cFr2c9oOEoYjMW5C4hQalHdCJ6mc7AFTYFTmBhGR9oTl3cx46HoNfyXcVy_4idXn7VzvxH97SDEOdUZth-5LmACAwrN8gjTi3HeNCQON3M8Qb37rlkf8oqwz7bbfEhZ5q6LoDdmCVDULQURtDbFQLi7SNaGj2BAhnA4PVphjdCD2mRtLLbs36-gBs02Nfx9cNh8-110_KfWoWvFt-hrNfw74hHUlJ5f1g9erqvawu8JdDAv6bvJ0qS0nRgGDkWhSAL-GC00F__0m00)
## 2.4 Xác định các trạng thái chính:
![Diagram](https://www.planttext.com/api/plantuml/png/T991JWCn34NtSmglaNe15gYYGeBTYAehnCBD63GYaumIfrBEne8ZSGNi9WobJNVHzt_9jvtlpwzrP0oS9jl9WGcU1alr-4mSHZgCxlrXcgtFHB5MDcXDiiXIwZ5NiG_UK8n5cyZnh_iHdLnwZ-vZv_20eyNzyaQrRhoyG4n3rxtSlC9gTNSC0hSI0eSCx24a1pFcuAtjZZKrDI8AizMM5dFBe-p_9WJxAuU2I9mpatANVGghHLEzWZKyYZOd8RGgiCsHQOBJ6RNzLqDefnaYkK5qsEkb7D15D3nwTotK-GfADoh1N0ZHOZ9wUalMvkw2EDbNNwOEPjdeMlB8__e1003__mC0)
