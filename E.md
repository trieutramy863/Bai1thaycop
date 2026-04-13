# E. Triển khai (level test) ứng dụng
# 1 Chuyển vào trong thư mục ~/myapp
# <img width="926" height="704" alt="Screenshot 2026-04-12 211927" src="https://github.com/user-attachments/assets/09d71370-a509-4ddb-9303-76c48a39e7a8" />
# 2 Gõ lệnh để docker compose chạy: sẽ run tất cả các service khai báo trong file docker-compose.yml
# <img width="914" height="422" alt="Screenshot 2026-04-12 213356" src="https://github.com/user-attachments/assets/80e13ca7-c848-4c18-a45d-e3574cc641d9" />
# 3 Kiểm tra các container đang chạy trong docker, nếu có cái nào bị restart cần tìm lỗi rồi edit lại docker-compose.yml
# Các container ở hình dưới không có cái nào lỗi cả
# <img width="914" height="227" alt="Screenshot 2026-04-12 213356" src="https://github.com/user-attachments/assets/4b482dc0-2b4f-493f-98c8-3e42ac43d475" />
# 4 Kiểm tra kiểm thử các service đang chạy độc lập thông qua ip và port của nó: ví dụ mở trình duyệt ip_ubuntu:1880 để check nodered đã chạy chưa
# trình duyệt http://192.168.1.6:1880 chạy ra được nodered
# <img width="1052" height="530" alt="Screenshot 2026-04-12 210640" src="https://github.com/user-attachments/assets/cda4f6bc-449d-418c-bbea-7ddd825a6bfa" />
# 5 Sử dụng nodered: kéo nodered http_in , http_response, function : để tạo api get đơn giản (dùng cho /api proxy_pass của nginx)
#  <img width="1920" height="1200" alt="Screenshot 2026-04-12 212722" src="https://github.com/user-attachments/assets/879b6f3b-4c26-444d-9dee-f5ffe4513d26" />
# <img width="1920" height="1200" alt="Screenshot 2026-04-12 212610" src="https://github.com/user-attachments/assets/c03dd876-c30e-40cf-bed1-dacc8987cb8a" />
# 6 Sửa file ./myweb/index.html : thêm code html+js để sử dụng được api đã khai báo proxy_pass (thực ra là sử dụng nodered http_in hoặc sử dụng service myapi)
# <img width="945" height="1113" alt="Screenshot 2026-04-12 204857" src="https://github.com/user-attachments/assets/f54f9c13-a728-4404-ba04-b1189bf14e0e" />
# <img width="1909" height="575" alt="Screenshot 2026-04-12 214541" src="https://github.com/user-attachments/assets/e3f7646d-9b7d-4291-865f-691313838175" />
