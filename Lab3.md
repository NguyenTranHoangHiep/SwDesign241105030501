# 1. Vẽ biểu đồ ngữ cảnh và giải thích
## 1.1.1 Biểu đồ ngữ cảnh của hệ thống con BankSystem

![Class Diagram](https://www.planttext.com/api/plantuml/png/d5AzJiCm4Dxp5ATChKGYM2Chgc3gXjILvN3SOCKvMxP36q6VZ857uXMmQr92smaFySNVVJ-v-ElZS-KyMZ_qAaEbzAwNUqbjvZf91Ytsm7LlD0do6pyg0LPmZzGgaMK6UOUjWFmHHwkLWitelEXpUCio0AxGEVY17ZJvk0iBZF7qKjUXwnAlm0u49fqlbb5AaXTsYrp0-XwfIpR11S9gXD5E-WK69VuYU5V1LDr4eewC2k9pJLjjU_HIqp9m3xyfPwgCkU7PfTfOlH_hEXhDEgf_Unw2K1YazEEfdx5qa5oEgKuzP_o4NmwiQFIEYlhFR2h86nb_rPJLmT7EmQl49xejoxiyYCqfxBqiPvzvXXR1OCfy1ReIDOnt9QY95-iR003__mC0)

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
