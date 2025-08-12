# Hệ thống Tư vấn Lộ trình Học tập bằng AI (AI Learning Roadmap Generator)

<!-- ![AI Roadmap Generator](https://placehold.co/800x400/020817/FFFFFF?text=AI+Learning+Roadmap+Generator) -->

## 1. Tổng quan dự án

Đây là một hệ thống tư vấn học tập đầu cuối, sử dụng AI để phân tích chênh lệch kỹ năng và tạo ra các lộ trình học tập được cá nhân hóa. Hệ thống bao gồm một **Backend** (Node.js/Express) xử lý logic nghiệp vụ, giao tiếp với AI, và một **Frontend** (Next.js) cung cấp giao diện tương tác cho người dùng.

- **[Link Demo Frontend](https://ai-frontend-roadmap.vercel.app/)**
- **[Link tới Backend API](https://ai-backend-roadmap.onrender.com/)** (Đợi 30s khởi động nếu có)

### Chức năng cốt lõi

- **Phân tích chênh lệch kỹ năng:** Hệ thống xác định khoảng cách giữa kỹ năng hiện tại của người dùng và yêu cầu của mục tiêu nghề nghiệp.
- **Tạo lộ trình học tập thông minh:** AI sẽ đề xuất một lộ trình học tập chi tiết theo tuần/tháng với trình tự các môn học hợp lý.
- **Gợi ý tài nguyên:** Cung cấp các tài nguyên học tập cụ thể cho từng kỹ năng (link khóa học, bài thực hành, dự án mẫu).
- **Tùy biến cao:** Lộ trình có thể được tùy chỉnh theo mục tiêu và thời gian học tập khác nhau của người dùng.
- **Giao diện web trực quan:** Người dùng có thể dễ dàng nhập thông tin, nhận kết quả và tương tác với lộ trình học tập của mình.

---

## 2. Kiến trúc hệ thống

Hệ thống được xây dựng theo kiến trúc Client-Server:

- **Backend (Server-side):**
    - **Nền tảng:** Node.js, Express.js
    - **Cơ sở dữ liệu:** MongoDB
    - **AI Core:** Tích hợp Google Gemini API để xử lý ngôn ngữ tự nhiên và tạo lộ trình.
    - **Chức năng:** Quản lý người dùng, xác thực (JWT), xử lý logic tạo lộ trình, cung cấp RESTful APIs.
- **Frontend (Client-side):**
    - **Nền tảng:** Next.js, React, TypeScript
    - **Giao diện:** Tailwind CSS & Shadcn/UI
    - **Chức năng:** Cung cấp giao diện cho người dùng đăng ký/đăng nhập, nhập thông tin, hiển thị lộ trình dưới dạng chi tiết và sơ đồ tương tác.

---

## 3. Hướng dẫn cài đặt và chạy thử

Để chạy toàn bộ hệ thống, bạn cần khởi động cả Backend và Frontend.

### 🚀 Phần Backend

#### Yêu cầu

- Node.js (v16 trở lên)
- MongoDB
- Redis

#### Cài đặt

1.  **Di chuyển vào thư mục backend:**
    ```bash
    cd backend
    ```
2.  **Cài đặt các gói phụ thuộc:**
    ```bash
    npm install
    ```
3.  **Thiết lập biến môi trường:**
    -   Tạo một file `.env` trong thư mục `backend`.
    -   Sao chép nội dung từ file `.env.example` (phần cấu hình `.env`) và điền các giá trị của bạn (MONGO_URI, GEMINI_API_KEY, JWT_SECRET, etc.).
    -   **Quan trọng:** Đặt `FRONTEND_URL=http://localhost:3000`.

4.  **Chạy server backend:**
    ```bash
    npm start
    ```
    Server sẽ chạy tại `http://localhost:5001`. Bạn có thể truy cập `http://localhost:5001/api-docs` để xem tài liệu API.

### 🚀 Phần Frontend

#### Yêu cầu

- Node.js (v18 trở lên)

#### Cài đặt

1.  **Di chuyển vào thư mục frontend:**
    ```bash
    cd frontend
    ```
2.  **Cài đặt các gói phụ thuộc:**
    ```bash
    npm install
    ```
3.  **Thiết lập biến môi trường:**
    -   Tạo một file `.env.local` trong thư mục `frontend`.
    -   Thêm dòng sau:
        ```env
        NEXT_PUBLIC_API_URL=http://localhost:5001/api/v1
        ```

4.  **Chạy server frontend:**
    ```bash
    npm run dev
    ```
    Ứng dụng sẽ có thể truy cập tại `http://localhost:3000`.

---

## 4. Tài liệu sử dụng

1.  **Đăng ký/Đăng nhập:** Tạo một tài khoản mới hoặc đăng nhập bằng tài khoản đã có (bao gồm Google/GitHub).
2.  **Tạo lộ trình:**
    -   Truy cập trang "Generate".
    -   Nhập **Mục tiêu nghề nghiệp** (ví dụ: "Lập trình viên Backend với Node.js").
    -   Nhập các **Kỹ năng hiện có**.
    -   Chọn các tùy chọn về **Thời gian** và **Phong cách học**.
    -   Nhấn "Tạo lộ trình" và đợi AI xử lý.
3.  **Xem kết quả:**
    -   Kết quả sẽ hiển thị dưới dạng danh sách chi tiết và một sơ đồ trực quan.
    -   Bạn có thể click vào các node trên sơ đồ để xem mô tả chi tiết.
    -   Sử dụng nút "Tải về PDF" để lưu lại lộ trình.
4.  **Xem lịch sử:** Truy cập trang "History" để xem lại các lộ trình đã tạo.
