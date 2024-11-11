# 1. Vẽ biểu đồ ngữ cảnh và giải thích
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
