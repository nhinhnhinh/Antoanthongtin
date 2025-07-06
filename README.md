ĐẠI HỌC ĐẠI NAM - CÔNG NGHỆ THÔNG TIN
![image](https://github.com/user-attachments/assets/adef89a2-6926-4ade-8b86-eb829227cf95)   
![image](https://github.com/user-attachments/assets/c52d9805-663b-4cdc-8024-0d312a35667f)

MÔN HỌC: AN TOÀN VÀ BẢO MẬT THÔNG TIN
GỬI TẬP TIN NHẠC CÓ BẢN QUYỀN
TRƯỜNG ĐẠI HỌC ĐẠI NAM
Giảng viên hướng dẫn: TS. Trần Đăng Công
Sinh viên thực hiện – Nhóm 5:

Đặng Thanh Bình

Nguyễn Việt Ninh

Vũ Duy Thái

🎯 Mục tiêu đề tài
Đề tài tập trung phát triển một hệ thống an toàn cho phép gửi và nhận các tập tin nhạc có bản quyền giữa hai thực thể (Client - Server) nhằm đảm bảo:

Bảo mật nội dung: Không ai ngoài người nhận hợp lệ có thể mở tập tin nhạc.

Toàn vẹn dữ liệu: Dữ liệu không bị thay đổi trong quá trình truyền tải.

Ngăn chặn truy cập trái phép: Tập tin chỉ giải mã được bởi Server được ủy quyền.

📌 Giới thiệu hệ thống
Hệ thống truyền tập tin nhạc theo mô hình Client - Server, sử dụng thuật toán mã hóa hiện đại như:

RSA (Asymmetric) để mã hóa khóa.

AES (Symmetric) để mã hóa nội dung tập tin nhạc.

Quy trình tổng quan:

Client mã hóa tập tin nhạc bằng AES với một khóa bí mật (key).

Khóa AES được mã hóa bằng public key RSA của server.

Tập tin và khóa mã hóa được gửi đến Server.

Server sử dụng private key để giải mã khóa AES, sau đó dùng nó để giải mã tập tin nhạc.

Ghi log quá trình để kiểm tra và xác thực.

🏗️ Kiến trúc hệ thống

CLIENT
│
├── Giao diện hoặc CLI để chọn file nhạc
├── Tạo khóa AES ngẫu nhiên
├── Mã hóa file bằng AES
├── Mã hóa khóa AES bằng RSA (Public Key của Server)
└── Gửi file + khóa đến Server qua Flask API
        ↓
      SERVER
        ↑
┌────── Nhận file và khóa AES mã hóa
├────── Giải mã khóa AES bằng Private Key
├────── Giải mã file nhạc
├────── Lưu trữ hoặc phát lại file
└────── Ghi log quá trình gửi/nhận

⚙️ Cấu trúc thư mục dự án

btl/
├── keys/                            # Chứa public/private key RSA
│   ├── server_private.pem
│   └── server_public.pem
├── music/                           # File nhạc mã hóa/gốc
├── logs/                            # Lưu các file log truyền tải
├── README.md                        # Tài liệu mô tả dự án
└── src/
    ├── config.py                    # Thông số cấu hình
    ├── crypto_utils.py              # Mã hóa/giải mã AES & RSA
    ├── server.py                    # Flask server
    └── client/
        ├── client.py                # Giao diện gửi file
        └── utils.py                 # Hỗ trợ mã hóa file
🛠️ Công nghệ sử dụng
Python 3.6+

Thư viện:

cryptography: Mã hóa RSA, AES.

Flask: API server giao tiếp.

logging: Theo dõi quá trình xử lý.

Hệ điều hành: Windows, Linux, macOS.

🚀 Hướng dẫn cài đặt và chạy
1. Cài thư viện cần thiết:

pip install flask cryptography
2. Khởi động Server:

cd src
python server.py
3. Gửi tập tin từ Client:

cd src/client
python client.py
Client sẽ yêu cầu chọn tập tin nhạc → tiến hành mã hóa → gửi đến server.

🔐 Bảo mật và toàn vẹn
Bảo mật nội dung: Tập tin nhạc được mã hóa bằng AES.

Bảo mật khóa: Khóa AES được mã hóa bằng RSA.

Toàn vẹn: Có thể tích hợp hàm băm SHA256 để kiểm tra dữ liệu.

Lưu vết: Toàn bộ quá trình truyền đều được log ra file.

📁 File log ví dụ
File transmission.log chứa:

[INFO] 2025-07-06 10:15 - File 'song.mp3' encrypted.
[INFO] 2025-07-06 10:16 - AES key sent securely.
[INFO] 2025-07-06 10:17 - File received and decrypted successfully.
🔄 Khả năng mở rộng
Tích hợp chữ ký số để xác thực người gửi.

Áp dụng SSL/TLS để bảo vệ kênh giao tiếp.

Cho phép upload nhiều tập tin hoặc cả thư mục.

Thêm UI nền web cho người dùng không biết kỹ thuật.

👨‍💻 Nhóm thực hiện
Nhóm 5 – Môn học: An toàn và Bảo mật Thông tin

Trường: Đại học Đại Nam

Giảng viên hướng dẫn: TS. Trần Đăng Công

Thành viên:

Đặng Thanh Bình

Nguyễn Việt Ninh

Vũ Duy Thái
