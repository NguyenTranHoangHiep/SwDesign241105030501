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

# 4. Phân tích ca sử dụng Maintain Timecard
## Biểu đồ lớp phân tích ca sử dụng Maintain Timecard
## Biểu đồ tuần tự phân tích ca sử dụng Maintain Timecard
