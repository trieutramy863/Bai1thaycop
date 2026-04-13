# Cài đặt Ubuntu + Docker
# Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
# Sử dụng một trong các công cụ để giả lập: VM_Ware (bản quyền) 
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 225543" src="https://github.com/user-attachments/assets/9c0a42da-7e9d-40e5-949b-9fce9d624020" />
# Download file iso để cài đặt.
# <img width="1161" height="1086" alt="Screenshot 2026-04-12 225600" src="https://github.com/user-attachments/assets/5c1b67fa-8b4a-4598-9643-32a3e7b8c277" />
# Cấu hình mạng trong Ubuntu (và công cụ giả lập) để cho phép truy cập SSH vào Ubuntu từ cmd của windows 
# <img width="1357" height="738" alt="Screenshot 2026-04-12 194256" src="https://github.com/user-attachments/assets/a603e5b9-637d-415d-81ea-2f0cacd0d30c" />
# Cài SSH bằng dòng lệnh
# sudo apt install openssh-server -y
# <img width="822" height="523" alt="Screenshot 2026-04-12 193654" src="https://github.com/user-attachments/assets/85af5994-3c9a-466e-a68e-10a00c8f6ca4" />
# Sau đó bật SSH lên bằng 2 lệnh dưới
sudo systemctl enable ssh
sudo systemctl start ssh
# <img width="840" height="260" alt="Screenshot 2026-04-12 193714" src="https://github.com/user-attachments/assets/d6299fff-b1de-4a65-9e99-886f69b2a984" />
# Bật tường lửa cho SSH
# <img width="597" height="174" alt="Screenshot 2026-04-12 194049" src="https://github.com/user-attachments/assets/525446c0-def3-44fc-b667-d947d788807a" />
# Sau đó chỉnh mạng của VMware từ NAT sang Bridged
Chạy lại lệnh ip -4 addr
# <img width="1166" height="338" alt="Screenshot 2026-04-12 195349" src="https://github.com/user-attachments/assets/750a5800-e93e-4788-82df-388271105d53" />
# Mở CMD ở windown ra rỗi gõ dòng lệnh này
ssh My@192.168.1
# <img width="1357" height="738" alt="Screenshot 2026-04-12 194256" src="https://github.com/user-attachments/assets/ab7d3668-fa34-4219-92d4-603e265e0e66" />
ssh cmd ở windown thành công và ubutun bắt đầu có thể sử dụng domain được.
# 2. Tìm hiểu các lệnh cơ bản của ubuntu - Liệt kê các file trong thư mục: ls
# <img width="1326" height="86" alt="Screenshot 2026-04-12 194536" src="https://github.com/user-attachments/assets/e360df24-77d8-4ba3-8ffc-68d0d998f56b" />
Dùng lệnh ls để liệt kê các thư mực và nó sẽ hiện thị ra những thư mục đã có 
# Tạo thư mục: mkdir nameFolder
# <img width="673" height="248" alt="Screenshot 2026-04-12 194852" src="https://github.com/user-attachments/assets/3e060e85-8332-49df-b795-919db821e62d" />
# Chuyển thư mục làm việc: cd path
# <img width="673" height="248" alt="Screenshot 2026-04-12 194852" src="https://github.com/user-attachments/assets/69c767bd-93d1-4370-9514-fcc1eddafc1f" />
# Copy file: cp file_nguồn path/file_đích
# <img width="673" height="248" alt="Screenshot 2026-04-12 194852" src="https://github.com/user-attachments/assets/f22f4719-1de2-4b02-87af-79d91d434d35" />
copy lile:cp a.txt b.txt
# Thay đổi quyền thao tác file: sudo chmod xxx filename
# <img width="531" height="189" alt="Screenshot 2026-04-12 194934" src="https://github.com/user-attachments/assets/467e01a5-bdfa-42a1-b377-cc6180f9e03c" />
# CTRL+o : lưu nội dung sau khi edit, CTRL+x : thoát edit file - Xem ip của máy ubuntu: ip -4 addr
# <img width="1166" height="338" alt="Screenshot 2026-04-12 195349" src="https://github.com/user-attachments/assets/1202754b-83df-4458-97c9-f7ba9fa1a757" />
# 3. Cài đặt docker cho Ubuntu - Sử dụng lệnh: sudo apt install -y docker.io
# <img width="1312" height="497" alt="Screenshot 2026-04-12 195533" src="https://github.com/user-attachments/assets/243729ae-1138-44f6-91ef-89d037d29da6" />
# docker vừa cài đặt, kiểm tra phiên bản của docker compose 
# <img width="687" height="223" alt="Screenshot 2026-04-12 200446" src="https://github.com/user-attachments/assets/0f4f6912-8a52-47a7-b75f-45c397a1cd77" />
# 5. Cấu hình để docker chạy mà không cần tiền tố sudo
# Dùng lệnh: sudo usermod -aG docker $USER để chạy docker mà ko cần tiền tố sudo và sau khi chạy xong ta dùng lệnh: exit để thoát
# SSH và domain và test ko cần sudo bằng lệnh: docker run hello-world
# <img width="918" height="387" alt="Screenshot 2026-04-12 202756" src="https://github.com/user-attachments/assets/c60e7882-3b26-4948-8208-17bd45f5a735" />
# 6.Tìm hiểu tập lệnh của docker và docker compose

# Lệnh docker
# vdocker --version: Kiểm tra phiên bản Docker
# docker run hello-world: Chạy container để kiểm tra Docker hoạt động
# docker ps: Xem các container đang chạy
# docker ps -a: Xem tất cả container (kể cả đã dừng)
# vdocker images: Xem danh sách các image
# docker logs <container_name>: Xem log của container
# docker stop <container_name>: Dừng container
# docker rm <container_name>: Xóa container
# Lệnh docker compose
# docker compose up -d: Chạy toàn bộ service trong docker-compose.yml
# docker compose down: Dừng toàn bộ service
# docker compose ps: Xem trạng thái các container
# docker compose logs: Xem log các service
# docker compose restart: Restart lại service
# docker compose up -d --build: Build và chạy lại container
# Đảm bảo tường lửa trên Ubuntu đã cho phép các cổng 80, 1880, 9630 (Lệnh: sudo ufw allow ...)
# Do em bật tường lửa bằng lệnh: sudo ufw enable trước rồi lên ở phần này em dùng lệnh: sudo ufw allow 80, 1880, 9630 để các cổng hoạt động thành công. Sau đó dùng lệnh: sudo ufw status để kiểm tra lại
# <img width="715" height="664" alt="Screenshot 2026-04-12 203850" src="https://github.com/user-attachments/assets/90ebc219-f138-4a5f-a558-384e3e1c9384" />








