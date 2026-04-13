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
# 
