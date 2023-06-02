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
### 3. Ưu và nhược điểm
#### 3.1. Ưu điểm
- Hiệu suất tối ưu: Percona Server có các cải tiến hiệu suất như bộ điều chỉnh truy vấn, bộ nhớ đệm thông minh và tối ưu hóa I/O, giúp cải thiện tốc độ xử lý truy vấn và thời gian phản hồi.
- Độ tin cậy cao: Percona Server bao gồm các tính năng bảo mật và cải tiến như bảo vệ chống sự cố và khả năng khôi phục dữ liệu, giúp đảm bảo độ tin cậy của hệ thống cơ sở dữ liệu.
- Tính tương thích ngược: Percona Server tương thích ngược với các ứng dụng và công cụ sử dụng MySQL, cho phép bạn dễ dàng chuyển đổi từ MySQL sang Percona Server mà không cần thay đổi mã nguồn.
- Công cụ quản lý: Percona Server đi kèm với các công cụ quản lý cơ sở dữ liệu mạnh mẽ như Percona Toolkit và Percona Monitoring and Management (PMM), giúp quản lý và giám sát hệ thống cơ sở dữ liệu dễ dàng hơn.
#### 3.2. Nhược điểm
- Độ phổ biến: So với MySQL, Percona Server không được sử dụng rộng rãi và phổ biến như là một hệ quản trị cơ sở dữ liệu mã nguồn mở.
- Tài liệu và cộng đồng hỗ trợ: Do Percona Server không phổ biến như MySQL, nên tài liệu và cộng đồng hỗ trợ có thể hạn chế hơn, điều này có thể làm khó khăn khi gặp phải vấn đề hoặc cần hỗ trợ kỹ thuật.
- Phụ thuộc vào bản phân phối: Percona Server là một bản phân phối riêng biệt và phụ thuộc vào nhà phân phối Percona, điều này có thể gây phiền toái trong việc cập nhật và duy trì hệ thống.
- Khả năng mở rộng: Mặc dù Percona Server có các cải tiến hiệu suất, nhưng khả năng mở rộng theo quy mô lớn có thể hạn chế so với các hệ quản trị cơ sở dữ liệu khác như PostgreSQL hoặc MongoDB.
### 4. Cài đặt
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
### 3. Ưu và nhược điểm
#### 3.1. Ưu điểm
- Độ tin cậy cao: PostgreSQL được thiết kế để đảm bảo tính nhất quán và an toàn cho dữ liệu. Nó hỗ trợ các tính năng như giao dịch ACID (Atomicity, Consistency, Isolation, Durability), đồng bộ hóa và phục hồi dữ liệu, giúp đảm bảo độ tin cậy của hệ thống.
- Mở rộng và linh hoạt: PostgreSQL cho phép mở rộng quy mô từ dự án nhỏ đến quy mô lớn. Nó hỗ trợ các tính năng như phân vùng, sao lưu và khôi phục, nhân bản và nhân rộng, giúp tăng cường khả năng mở rộng và linh hoạt của hệ thống.
- Tính năng phong phú: PostgreSQL cung cấp một loạt các tính năng nâng cao bao gồm khóa ngoại, chỉ mục toàn văn, truy vấn địa lý, truy vấn JSON, truy vấn đồ họa và nhiều tính năng khác, giúp phục vụ nhiều loại ứng dụng và trường hợp sử dụng khác nhau.
- Hỗ trợ chuẩn SQL: PostgreSQL tuân thủ tiêu chuẩn SQL ANSI, với hỗ trợ cho các tính năng tiên tiến của SQL như truy vấn phức tạp, phân tích cú pháp và các chức năng quản lý dữ liệu phong phú.
#### 3.2. Nhược điểm
- Phức tạp hơn: PostgreSQL có một số tính năng phức tạp và yêu cầu hiểu biết sâu về cơ sở dữ liệu quan hệ. Điều này có thể làm tăng độ khó và đòi hỏi thời gian để làm quen và triển khai.
- Tài liệu hạn chế: So với một số hệ quản trị cơ sở dữ liệu phổ biến khác như MySQL, PostgreSQL có ít tài liệu và nguồn hỗ trợ thực tế hơn. Điều này có thể tạo ra khó khăn khi gặp phải vấn đề hoặc cần hỗ trợ kỹ thuật.
- Khả năng mở rộng: Mặc dù PostgreSQL có khả năng mở rộng, nhưng quy mô mở rộng theo quy mô lớn có thể đòi hỏi sự quản lý kỹ lưỡng và hiệu suất tối ưu hóa để đảm bảo hiệu suất tốt.
- Thị trường và cộng đồng: PostgreSQL không phổ biến như MySQL, Oracle hoặc SQL Server, do đó, có thể có ít hỗ trợ thương mại và nguồn nhân lực có kinh nghiệm hơn cho PostgreSQL.
### 4. Cài đặt
- Cập nhật hệ thống:
```
sudo apt update
sudo apt upgrade
```
- Sau đó, cài đặt Postgres cùng với -contrib bổ sung một số tiện ích và chức năng bổ sung:
```
sudo apt install postgresql postgresql-contrib
```
##### Dùng tải khoản postgres
- Chuyển sang Tài khoản postgres
Chuyển sang tài khoản postgres trên máy chủ của bạn bằng cách nhập:
```
sudo -i -u postgres
```
Bây giờ bạn có thể truy cập vào lời nhắc PostgreSQL ngay lập tức bằng cách nhập:
```
psql
```
Từ đó bạn có thể tự do tương tác với hệ quản trị cơ sở dữ liệu khi cần thiết.

Thoát khỏi lời nhắc PostgreSQL bằng cách nhập:
```
\q
```
Thao tác này sẽ đưa bạn trở lại dấu nhắc lệnh của postgres Linux.
##### Truy cập Lời nhắc của Postgres mà không cần chuyển đổi tài khoản
Bạn cũng có thể chạy lệnh bạn muốn với tài khoản postgres trực tiếp với sudo.

Ví dụ: trong ví dụ trước, bạn được hướng dẫn để truy cập lời nhắc Postgres bằng cách chuyển sang người dùng postgres trước tiên và sau đó chạy psql để mở lời nhắc Postgres. Bạn có thể thực hiện điều này trong một bước bằng cách chạy lệnh psql duy nhất với tư cách là người dùng postgres với sudo, như sau:
```
sudo -u postgres psql
```
Điều này sẽ giúp bạn đăng nhập trực tiếp vào Postgres mà không có trình bash trung gian ở giữa.

Một lần nữa, bạn có thể thoát phiên Postgres tương tác bằng cách nhập:
```
\q
```
Nhiều trường hợp sử dụng yêu cầu nhiều hơn một Postgres role. Đọc tiếp để tìm hiểu cách định cấu hình chúng.
## 3. Mongo database
### 1. Khái niệm
MongoDB là một hệ quản trị cơ sở dữ liệu phi quan hệ, mã nguồn mở và phân tán được thiết kế để lưu trữ và xử lý dữ liệu phi cấu trúc và có cấu trúc linh hoạt. MongoDB sử dụng mô hình dữ liệu JSON-like (BSON) để lưu trữ dữ liệu, giúp tương thích tốt với các ngôn ngữ lập trình hiện đại và phục vụ cho các ứng dụng có tính mở rộng và linh hoạt.
### 2. MongoDB hỗ trợ nhiều tính năng quan trọng
- Tính linh hoạt: MongoDB cho phép lưu trữ dữ liệu phi cấu trúc và có cấu trúc linh hoạt. Bạn có thể lưu trữ các bản ghi có cấu trúc khác nhau trong cùng một bảng, giúp dễ dàng thay đổi cấu trúc dữ liệu mà không yêu cầu sự thay đổi cấu trúc cơ sở dữ liệu.
- Phân tán và mở rộng: MongoDB được thiết kế để phân tán dữ liệu trên nhiều máy chủ, cho phép mở rộng theo quy mô lớn và xử lý tải lớn. Nó hỗ trợ sharding, replica sets và các tính năng như auto-sharding, giúp tăng khả năng mở rộng và độ tin cậy của hệ thống.
- Truy vấn mạnh mẽ: MongoDB cung cấp một ngôn ngữ truy vấn linh hoạt và mạnh mẽ để truy vấn dữ liệu. Bạn có thể thực hiện các truy vấn phức tạp và các phép toán như truy vấn theo điều kiện, truy vấn dựa trên vị trí địa lý và truy vấn theo các trường nhúng.
- Tính nhất quán và độ tin cậy: MongoDB hỗ trợ các tính năng như replica sets và transaction để đảm bảo tính nhất quán và độ tin cậy của dữ liệu.
### 3. Ưu và nhược điểm
#### 3.1. Ưu điểm
- Khả năng mở rộng: MongoDB có khả năng mở rộng tuyến tính, cho phép bạn xử lý lưu lượng truy cập lớn và dữ liệu lớn một cách dễ dàng. Bạn có thể thêm các node mới vào cụm MongoDB để tăng khả năng chịu tải.
- Tính linh hoạt và dễ sử dụng: MongoDB sử dụng mô hình dữ liệu linh hoạt với JSON/BSON, cho phép lưu trữ dữ liệu có cấu trúc và không cấu trúc một cách tự nhiên. Điều này giúp MongoDB dễ dàng tích hợp vào các ứng dụng phát triển nhanh.
- Truy vấn mạnh mẽ: MongoDB cung cấp một ngôn ngữ truy vấn linh hoạt và mạnh mẽ, bao gồm truy vấn theo điều kiện, truy vấn dựa trên vị trí địa lý và các truy vấn phức tạp khác. Điều này giúp bạn tìm kiếm và truy xuất dữ liệu một cách hiệu quả.
- Replica sets và sharding: MongoDB hỗ trợ replica sets để tăng tính sẵn sàng và độ tin cậy của hệ thống. Nó cũng hỗ trợ sharding để phân tán dữ liệu trên nhiều máy chủ, tăng khả năng mở rộng và hiệu suất.
- Cộng đồng hỗ trợ: MongoDB có một cộng đồng lớn và nhiều tài liệu hỗ trợ trực tuyến. Bạn có thể tìm thấy nhiều tài liệu, câu trả lời cho câu hỏi và tài nguyên phát triển từ cộng đồng này.
#### 3.2. Nhược điểm
- Tính nhất quán và đồng thuận: MongoDB không hỗ trợ ACID (Atomicity, Consistency, Isolation, Durability) hoàn toàn trong các giao dịch. Điều này có nghĩa là nếu bạn cần tính toàn vẹn tuyệt đối của dữ liệu trong các giao dịch, MongoDB có thể không phù hợp.
- Sử dụng tài nguyên: MongoDB tiêu tốn nhiều tài nguyên hơn so với một số hệ quản trị cơ sở dữ liệu khác. Việc lưu trữ dữ liệu trong MongoDB có thể đòi hỏi nhiều không gian đĩa và bộ nhớ.
- Không tốt cho các truy vấn phức tạp: Trong một số trường hợp, MongoDB có thể không hiệu quả cho các truy vấn phức tạp và yêu cầu xử lý phức tạp. Việc mô hình dữ liệu phi quan hệ của MongoDB có thể không phù hợp cho các tình huống này.
- Khả năng quản lý dữ liệu: MongoDB có thể khó khăn trong việc quản lý dữ liệu khi dữ liệu trở nên lớn và phức tạp. Bạn cần có kiến thức và kỹ năng để thiết kế và triển khai hệ thống MongoDB hiệu quả.
Tóm lại, MongoDB có nhiều ưu điểm như khả năng mở rộng, linh hoạt, truy vấn mạnh mẽ và hỗ trợ replica sets và sharding. Tuy nhiên, nó cũng có nhược điểm như thiếu tính nhất quán và đồng thuận, sử dụng tài nguyên cao và không phù hợp cho các truy vấn phức tạp. Việc sử dụng MongoDB nên được cân nhắc kỹ lưỡng dựa trên yêu cầu và điều kiện cụ thể của dự án.
### 4. Cài đặt
- Cập nhật ubuntu
```
sudo apt update
sudo apt upgrade
```
- Thêm MongoDB Repository
```
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
```
Sau đó, thêm MongoDB Repository vào danh sách nguồn:
```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
```
- Cài đặt mongo
```
sudo apt update
sudo apt install mongodb-org
```
Sau khi tải xong thì dùng lệnh ` mongo ` để chạy mongo
