# F. Gỡ lỗi
# 1 Nếu có lỗi xẩy ra trong quá trình triển khai docker compose up -d
# Kiểm tra nhanh: docker compose ps giúp biết container nào đang chạy xem log, ví dụ: docker logs mynginx docker logs myapi
# <img width="925" height="212" alt="Screenshot 2026-04-12 203425" src="https://github.com/user-attachments/assets/816234c4-cbbf-4709-abf8-93746e293835" />
# 2 Thêm healthcheck cho myapi trong file docker-compose.yml
# <img width="953" height="1079" alt="Screenshot 2026-04-12 221706 (2)" src="https://github.com/user-attachments/assets/f0bb6bd4-5c84-4d3f-a4fd-1f8a23ba3082" />
thêm helthcheck
# Giới hạn resource cho một service: (tránh việc 1 service chiếm quá nhiều ram)
# <img width="953" height="1079" alt="Screenshot 2026-04-12 221706" src="https://github.com/user-attachments/assets/3b128323-a246-49f2-851e-00c671429567" />
giới hạn resource 
# Sử dụng lệnh: docker compose stats để quan sát lượng ram sử dụng bởi mỗi service
# <img width="1763" height="350" alt="Screenshot 2026-04-12 221818" src="https://github.com/user-attachments/assets/3e5f714a-7fff-43f8-95b0-f1d6cb2ee839" />
