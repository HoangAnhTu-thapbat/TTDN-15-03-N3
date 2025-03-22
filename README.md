1. Cài đặt công cụ, môi trường và các thư viện cần thiết
1.1. Clone project.
git clone https://gitlab.com/anhlta/odoo-fitdnu.git
cd odoo-fitdnu
git checkout cntt15_03
1.2. cài đặt các thư viện cần thiết
Người sử dụng thực thi các lệnh sau đề cài đặt các thư viện cần thiết

sudo apt update
sudo apt-get install libxml2-dev libxslt-dev libldap2-dev libsasl2-dev libssl-dev python3.10-distutils python3.10-dev build-essential libssl-dev libffi-dev zlib1g-dev python3.10-venv libpq-dev
1.3. khởi tạo môi trường ảo.
python3.10 -m venv ./venv
Thay đổi trình thông dịch sang môi trường ảo và chạy requirements.txt để cài đặt tiếp các thư viện được yêu cầu

source venv/bin/activate
pip3 install -r requirements.txt
2. Setup database
Chạy lệnh

sudo apt install docker-compose
Khởi tạo database trên docker bằng việc thực thi file dockercompose.yml.

docker-compose up -d
3. Setup tham số chạy cho hệ thống
3.1. Khởi tạo odoo.conf
Tạo file odoo.conf có nội dung như sau:

[options]
addons_path = addons
db_host = localhost
db_password = odoo
db_user = odoo
db_port = 5433
xmlrpc_port = 8069
Có thể kế thừa từ odoo.conf.template

4. Chạy hệ thống và cài đặt các ứng dụng cần thiết
Lệnh chạy

python3 odoo-bin.py -c odoo.conf -u all
Người sử dụng truy cập theo đường dẫn http://localhost:8069/ để đăng nhập vào hệ thống.

Hoàn tất
