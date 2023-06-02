# Database
## I. Percona database
### 1. Khái niệm
Percona Server for MySQL là một hệ quản trị cơ sở dữ liệu quan hệ (RDBMS) mã nguồn mở dựa trên mã nguồn mở của MySQL. Nó được xây dựng và phát triển bởi Percona, một công ty chuyên về dịch vụ và sản phẩm hỗ trợ cho MySQL và các công nghệ cơ sở dữ liệu khác.
Percona Server for MySQL cung cấp các tính năng và hiệu suất nâng cao so với MySQL thông thường. Mục tiêu của Percona là cải thiện khả năng mở rộng, hiệu suất, tin cậy và tính sẵn sàng của MySQL để đáp ứng nhu cầu của các ứng dụng yêu cầu hiệu năng và quy mô lớn.
### 2. Một số tính năng và cải tiến của Percona Server for MySQL
- InnoDB Storage Engine: Tối ưu hóa cho hiệu suất cao và độ tin cậy.
- XtraBackup: Công cụ sao lưu và khôi phục dựa trên các bản sao nhân bản.
- Percona Toolkit: Bộ công cụ mạnh mẽ để quản lý, sửa chữa và kiểm tra cơ sở dữ liệu MySQL.
- Tối ưu hóa truy vấn: Cải thiện tối đa hiệu suất và khả năng mở rộng của các truy vấn SQL.
- Thread Pool: Tăng cường hiệu suất cho các ứng dụng đa luồng.
- Cải thiện khả năng mở rộng: Tối ưu hóa việc sử dụng tài nguyên và quản lý khả năng mở rộng ngang.
Percona Server for MySQL là một sự lựa chọn phổ biến trong cộng đồng MySQL cho các ứng dụng quy mô lớn, yêu cầu hiệu suất cao và tính sẵn sàng cao.
### 3. Cài đặt
- Cập nhật hệ thống:
```
sudo apt update
sudo apt upgrade
```
- Thực hiện cài đặt gói kho lưu trữ Percona:
```
wget https://repo.percona.com/apt/percona-release_latest.focal_all.deb
sudo dpkg -i percona-release_latest.focal_all.deb
```
- Cập nhật lại danh sách gói và cài đặt Percona Server for MySQL:
```
sudo apt update
sudo apt install percona-server-server-5.7
```
- Sau đó ta đăng nhập vào tài khoản root của máy ` sudo -i ` rồi cài đặt các chức năng do người dùng xác định UDF:
```
mysql -e "CREATE FUNCTION fnv1a_64 RETURNS INTEGER SONAME 'libfnv1a_udf.so'" -p
mysql -e "CREATE FUNCTION fnv_64 RETURNS INTEGER SONAME 'libfnv_udf.so'" -p
mysql -e "CREATE FUNCTION murmur_hash RETURNS INTEGER SONAME 'libmurmur_udf.so'" -p
```
- Để tránh phần mềm được nâng cấp từ kho lưu trữ phân phối, làm như vậy cần tạo một tệp mới /etc/apt/preferences.d/00percona.pref và lưu nội dung sau vào đó:
```
Package: *
Pin: release o=Percona Development Team
Pin-Priority: 1001
```
## II. Postgre database
### 1. Khái niệm
PostgreSQL là một hệ quản trị cơ sở dữ liệu quan hệ mã nguồn mở, được viết bằng ngôn ngữ C. Nó được biết đến với tên viết tắt là "Postgres" và thường được sử dụng để lưu trữ và quản lý dữ liệu trong các ứng dụng web, ứng dụng di động và các hệ thống thông tin doanh nghiệp.
### 2. PostgreSQL hỗ trợ các tính năng quan trọng của một hệ quản trị cơ sở dữ liệu quan hệ
- Cấu trúc dữ liệu quan hệ: PostgreSQL sử dụng cấu trúc dữ liệu quan hệ với các bảng, cột và quan hệ giữa chúng để lưu trữ dữ liệu.
- Truy vấn SQL: PostgreSQL hỗ trợ ngôn ngữ truy vấn SQL (Structured Query Language) cho việc truy vấn và xử lý dữ liệu.
- Giao dịch và đồng nhất dữ liệu: PostgreSQL cho phép thực hiện các giao dịch cơ sở dữ liệu để đảm bảo tính nhất quán và an toàn cho dữ liệu.
- Quản lý quyền truy cập: PostgreSQL cung cấp hệ thống quản lý quyền truy cập mạnh mẽ để kiểm soát quyền truy cập vào cơ sở dữ liệu và bảo mật dữ liệu.
- Chức năng mở rộng: PostgreSQL hỗ trợ các chức năng mở rộng, cho phép bạn tạo các chức năng tùy chỉnh và mở rộng khả năng của hệ quản trị cơ sở dữ liệu.
