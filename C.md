# C. Cấu hình docker compose
# Tạo thư mục: ~/myapp
# <img width="715" height="664" alt="Screenshot 2026-04-12 203850" src="https://github.com/user-attachments/assets/331d5379-9d5b-48fa-8fd8-719c510ed1b5" />
# 1. Tạo thư mục: ~/mywed
# <img width="715" height="664" alt="Screenshot 2026-04-12 203850" src="https://github.com/user-attachments/assets/c056bcb5-b303-4e9b-b48d-f8a9b7ad2260" />
# 2 Tạo thư mục: ./myapp
# <img width="371" height="127" alt="Screenshot 2026-04-12 204633" src="https://github.com/user-attachments/assets/420bc46e-efe4-43ff-ac0f-46ce2a4ddb4b" />
# 3 Tạo file ./myweb/index.html (với nội dung là thông tin cá nhân của em)
# <img width="371" height="127" alt="Screenshot 2026-04-12 204633" src="https://github.com/user-attachments/assets/828eeb7b-dd86-492b-8f02-63d65f9be295" />
# 4 Tạo file docker-compose.yml để nó sẽ có các dịch vụ sau
# Khai báo sử dụng nodered/node-red, cổng 1880, dữ liệu nằm tại thư mục ./nodered
# Nhập nano docker-compose.yml để tạo file
# <img width="965" height="1126" alt="Screenshot 2026-04-12 205010" src="https://github.com/user-attachments/assets/44a7d06c-697d-4213-b0d1-c9c845c75862" />
# Khai báo sử dụng nginx, cổng 80, cấu hình trong file ./nginx/nginx.conf
# <img width="935" height="1118" alt="Screenshot 2026-04-12 204936" src="https://github.com/user-attachments/assets/bcf92a93-1ee8-4c70-af21-00f94d536d89" />
# Mount thư mục ./myweb thành thư mục /myweb trong nginx
# Mount file ./nginx/nginx.conf vào file /etc/nginx/nginx.conf trong nginx
# <img width="965" height="1126" alt="Screenshot 2026-04-12 205010" src="https://github.com/user-attachments/assets/9387f80a-fce6-408d-876e-e1da3fba47c5" />
# Edit file ./nginx/nginx.conf để
# Cấu hình web server cổng 80, server_name là sub-domain (sub-domain tuỳ ý của em)
# Trong quá trình test ban đầu, em sử dụng:server_name localhost;
# Sau khi triển khai với Cloudflare Tunnel, domain thực tế là: myapp.local
# location / trỏ tới root là thư mục /myweb
# Cấu hình location/, trong file cấu hình ngix.conf em thiết lập location/{ root /myweb; index index.html; }
# Khi người dung truy cập vào địa chỉ ip http://192.168.1.6/ thì Ngix sẽ lấy nội dùng từ thư mục /myweb thì nó sẽ mặc định hiển thị là index.html
# Điều này cho phép triển khai một website tĩnh hiện thị thông tin cá nhân
# location /api dùng proxy_pass trỏ tới 1 (hoặc nhiều) node http_in của nodered
# Trong file nginx.conf, em cấu hình: location /api/ { proxy_pass http://nodered:1880/; }
# Khi người dùng truy cập đường dẫn /api trên web → nginx sẽ chuyển tiếp (proxy) request tới service Node-RED
# "nodered" là tên service được khai báo trong docker-compose.yml
# → Docker tự tạo DNS nội bộ để các container có thể gọi nhau bằng tên này
# Port 1880 là cổng mặc định của Node-RED
# Nhờ đó, các API được tạo từ node http_in trong Node-RED
# sẽ được truy cập thông qua đường dẫn: http://192.168.1.6/api/hello
# Ngix sẽ chuyển tiếp (proxy) request này đến Node_RED đang chạy trong Docker tại http://nodered:1880/
# Service nodered là tên container trong docker-compose, Docker tự resolve nội bộ.
# <img width="935" height="1118" alt="Screenshot 2026-04-12 204936" src="https://github.com/user-attachments/assets/d5c2f1d1-d14d-4618-a821-ab5275abc7a2" />
# Ảnh Kết quả
Truy cập: http://192.168.1.255/
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 210123" src="https://github.com/user-attachments/assets/1cdf00f3-95b1-414e-b3a0-3cadb5f71418" />
# + http in (/hello) nối với function 1 nối với http response
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 212722" src="https://github.com/user-attachments/assets/aa1b8914-9e07-4418-a3af-75f49d37fcb9" />
# + Truy cập: http://192.168.1.6/hello
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 212610" src="https://github.com/user-attachments/assets/b68461a7-4b69-47f8-8240-4ad9e5c611c8" />
# Truy cập: http://192.168.1.6/api/hello
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 212610" src="https://github.com/user-attachments/assets/ae7d4a3e-a5ba-432f-a8c4-05a77d0c5190" />
# Edit file ./nodered/settings.js để nodered bắt buộc đăng nhập
# Chạy docker-compose lần đầu để Node-RED tự sinh file cấu hình trong thư mục ./nodered, sau đó mới tiến hành sửa settings.js và restart lại container
# Cài công cụ tạo mật khẩu: npm install -g node-red-admin
# Tạo mật khẩu mã hóa: node-red-admin hash-pw
# <img width="927" height="504" alt="Screenshot 2026-04-12 212735" src="https://github.com/user-attachments/assets/24e2a620-9555-4444-842c-be3da8fd3e5e" />
# Thêm cấu hình adminAuth để yêu cầu đăng nhập
# <img width="960" height="341" alt="Screenshot 2026-04-12 210814" src="https://github.com/user-attachments/assets/be45dab3-b08d-463f-9f53-37a283ff8038" />
#  Restart lại container: docker compose restart + Kết quả: Khi truy cập Node-RED sẽ yêu cầu nhập username/password
#  <img width="1052" height="530" alt="Screenshot 2026-04-12 210640" src="https://github.com/user-attachments/assets/ab8b89ac-7679-499a-91fe-20928d08a259" />









