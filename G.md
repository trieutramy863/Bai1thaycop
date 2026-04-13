# G. Triển khai ứng dụng đến End-user
# 1 Trong Cloudflare: Tạo tunnel (đường hầm), chọn loại triển khai cho docker
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 225041" src="https://github.com/user-attachments/assets/4f236bac-f5c6-41a9-9a33-c1312873f642" />
# 2 Convert lệnh docker run ... sang dạng docker compose
# Sau khi tạo xong tunnel chọn docker nó cho 1 đoạn lệnh bạn chuyển sang convert chuyển sang yaml
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 224648" src="https://github.com/user-attachments/assets/63509cab-d860-441e-979b-bf1a755b240f" />
# 3 Khai báo kết quả convert vào trong file docker-compose.yml
# Thêm service Cloudflare ( được chuyển từ lệnh docker run) vào phần services trong file docker compose.yml để hệ thống chạy đồng thời các container.
# <img width="944" height="950" alt="Screenshot 2026-04-12 224438" src="https://github.com/user-attachments/assets/04fc2641-2dfa-4622-a8a2-3022c56eeb1b" />
# Chạy lại docker compose
Sau khi thêm serviec vào docker compose.yml xong ,sử dụng lệnh docker compose down và lệnh docker compose up -d để dừng hệ thống và khởi động lại hệ thống
Sau đó sử dụng lệnh docker compose ps để xem lại các dịch vụ
# <img width="943" height="347" alt="Screenshot 2026-04-12 224607" src="https://github.com/user-attachments/assets/7a89ab90-c92c-4251-9205-ddc055833d3b" />
# 5 Public ứng dụng bằng cách thêm 1 router trỏ tới container đang chạy trong docker, dữ liệu sẽ đi qua tunnel, url dạng sub-domain
Thêm một Public Hostname trong Cloudflare Tunnel, cấu hình subdomain trỏ đến địa chỉ dịch vụ nginx đang chạy Docker
Tên hostname của subdomain này chỉ là tên lúc đầu khi em làm thử và tên subdomain mà em sử dụng để chạy bài của em có tên là app
# <img width="1368" height="879" alt="Screenshot 2026-04-12 224711" src="https://github.com/user-attachments/assets/e803185b-04e8-4db2-a2ff-b4707352ea05" />
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 225041" src="https://github.com/user-attachments/assets/6ca1ad8a-1237-449d-b37c-0f344164b724" />
# Kiểm tra url sub-domain đã hoạt động public cho mọi end-user
# Truy cập vào URL sub-domain đã cấu hình http://app.trieutramy04.id.vn trên trình duyệt đã được
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 225125" src="https://github.com/user-attachments/assets/d4284f18-46c1-47c7-a0ea-5adf027aa582" />
# Truy cập bằng điện thoại mobile đã ok, cho thấy hệ thống đã được public thành công
# <img width="828" height="1792" alt="image" src="https://github.com/user-attachments/assets/21c7289a-19bc-41ea-8644-859f0bd6677d" />
