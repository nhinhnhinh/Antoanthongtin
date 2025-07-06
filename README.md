# Antoanthongtin

ĐỒ ÁN MÔN HỌC: AN TOÀN VÀ BẢO MẬT THÔNG TIN
TÊN ĐỀ TÀI: GỬI TẬP TIN NHẠC CÓ BẢN QUYỀN

TRƯỜNG ĐẠI HỌC ĐẠI NAM
GIẢNG VIÊN HƯỚNG DẪN: TS. Trần Đăng Công

SINH VIÊN THỰC HIỆN – NHÓM 12:
1. Đặng Thanh Bình
2. Nguyễn Việt Ninh
3. Vũ Duy Thái

------------------------------------------------------------

GIỚI THIỆU HỆ THỐNG

Hệ thống được xây dựng nhằm mô phỏng mô hình giao tiếp giữa client và server sử dụng thuật toán mã hóa bất đối xứng RSA. Đây là một thuật toán mã hóa mạnh, có khả năng bảo mật cao, giúp đảm bảo thông tin được truyền đi giữa client và server không bị đánh cắp hay thay đổi trái phép.

Mỗi bên trong hệ thống đều sở hữu một cặp khóa RSA bao gồm khóa công khai và khóa riêng. Việc truyền dữ liệu được thực hiện thông qua mạng nội bộ, dữ liệu sẽ được mã hóa trước khi gửi đi và giải mã khi nhận về để đảm bảo tính toàn vẹn và bảo mật.

------------------------------------------------------------

CHỨC NĂNG CHÍNH

- Sinh cặp khóa RSA cho client và server.
- Client sử dụng khóa công khai của server để mã hóa dữ liệu trước khi gửi.
- Server sử dụng khóa riêng để giải mã dữ liệu nhận được.
- Ghi log toàn bộ quá trình mã hóa, giải mã và truyền tải dữ liệu vào file log.
- Giao tiếp giữa client và server được thực hiện thông qua Flask API.

------------------------------------------------------------

CẤU TRÚC DỰ ÁN

Thư mục chính `btl` bao gồm các file và thư mục như sau:

- client_private.pem: Khóa riêng của client.
- client_public.pem: Khóa công khai của client.
- server_private.pem: Khóa riêng của server.
- server_public.pem: Khóa công khai của server.
- key_generation.log: File log ghi lại quá trình tạo khóa RSA của client.
- server_key_generation.log: File log ghi lại quá trình tạo khóa RSA của server.
- Thư mục `btl (2)` chứa mã nguồn chính:
  - config.py: File cấu hình.
  - crypto_utils.py: Chứa các hàm xử lý mã hóa và giải mã bằng RSA.
  - server_flask.py: File chạy server Flask.
  - Thư mục `client` bên trong:
    - client_flask.py: File chạy client Flask.
    - crypto_utils.py: Các tiện ích mã hóa phía client.

------------------------------------------------------------

HƯỚNG DẪN CÀI ĐẶT VÀ SỬ DỤNG

Bước 1: Cài đặt các thư viện cần thiết
Sử dụng pip để cài đặt các thư viện:

pip install flask cryptography

Bước 2: Chạy server
Vào thư mục chứa mã server và chạy file:

cd "btl/btl (2)"
python server_flask.py

Bước 3: Chạy client
Chuyển vào thư mục client và chạy chương trình:

cd "btl/btl (2)/client"
python client_flask.py

Bước 4: Gửi và nhận dữ liệu
- Dữ liệu được gửi từ client đến server dưới dạng đã mã hóa bằng RSA.
- Server nhận dữ liệu và sử dụng khóa riêng để giải mã.
- Quá trình mã hóa – giải mã được ghi lại đầy đủ trong file log để phục vụ việc kiểm tra và đánh giá.

------------------------------------------------------------

YÊU CẦU HỆ THỐNG

- Hệ điều hành: Windows / macOS / Linux
- Python 3.6 trở lên
- Các thư viện: flask, cryptography, os, logging

------------------------------------------------------------

GIẤY PHÉP VÀ MỤC ĐÍCH

Dự án này được thực hiện nhằm phục vụ mục đích học tập và nghiên cứu trong khuôn khổ môn học "An toàn và Bảo mật Thông Tin" tại Trường Đại học Đại Nam.

Tác giả không chịu trách nhiệm nếu mã nguồn được sử dụng sai mục đích hoặc triển khai trong môi trường thực tế mà không có biện pháp bảo vệ thích hợp.

------------------------------------------------------------

THÔNG TIN LIÊN HỆ

Nhóm 12 – Môn học An toàn và Bảo mật Thông tin
Trường Đại học Đại Nam
