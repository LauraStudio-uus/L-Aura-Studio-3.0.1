# L’AURA STUDIO — bản triển khai đầy đủ

Gói này gồm giao diện trong `public/`, Node.js API trong `server.js`, PostgreSQL schema trong `database/schema.sql`, thư mục ảnh tải lên `uploads/` và file cấu hình mẫu `.env.example`.

## Chạy trên máy

1. Cài Node.js 20+ và PostgreSQL 15+.
2. Sao chép `.env.example` thành `.env`, thay toàn bộ mật khẩu và chuỗi bí mật.
3. Chạy `npm install`.
4. Chạy `npm run db:init` để tạo bảng và sáu concept.
5. Chạy `npm start`, sau đó mở `http://localhost:3000`.

## Đưa lên Render với database Supabase

- Tạo Supabase project, chạy `database/schema.sql` trong SQL Editor và lấy Session pooler `DATABASE_URL` từ nút Connect.
- Đặt các biến trong `.env.example` tại phần Environment Variables của dịch vụ hosting.
- Build command: `npm install`.
- Start command: `npm start`.
- Gắn persistent disk vào thư mục `/uploads` để ảnh tải lên không mất khi máy chủ khởi động lại. Nếu nền tảng không có persistent disk, nên thay phần lưu file bằng Cloudinary hoặc Supabase Storage.
- Bắt buộc đổi `ADMIN_EMAIL`, `ADMIN_PASSWORD` và `SESSION_SECRET` trước khi public website.

## Dữ liệu

- `concepts`, `concept_images`: album sáu concept, hiển thị trên trang chủ và trang concept.
- `bookings`: yêu cầu đặt lịch và trạng thái xử lý.
- `portfolio_items`, `posts`, `comments`: cấu trúc database sẵn cho các phần nội dung mở rộng.

Khi API hoạt động, album và booking được lưu trong PostgreSQL. Nếu chỉ mở thư mục `public/` như website tĩnh, giao diện vẫn chạy với localStorage để xem thử nhưng dữ liệu sẽ chỉ tồn tại trên trình duyệt đang dùng.
