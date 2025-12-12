# Hệ thống Tuyển sinh BDU

Hệ thống quản lý tuyển sinh với các chức năng: đăng ký thông tin, quản lý hồ sơ, upload tài liệu, và tra cứu kết quả.

## Công nghệ sử dụng

- **Frontend**: React + Vite
- **Backend**: Node.js + Express
- **Database**: MySQL

## Cài đặt

### 1. Cài đặt dependencies

```bash
# Cài đặt tất cả dependencies
npm run install:all
```

Hoặc cài đặt riêng:

```bash
# Backend
cd backend
npm install

# Frontend
cd ../frontend
npm install
```

### 2. Cấu hình Database

1. Tạo database MySQL và import schema:

```bash
mysql -u root -p < backend/database/schema.sql
```

2. Tạo file `.env` trong thư mục `backend` từ file `.env.example`:

```bash
cd backend
cp .env.example .env
```

3. Cập nhật thông tin database trong file `.env`:

```
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=bdu_tuyen_sinh
DB_PORT=3306
```

### 3. Tạo thư mục uploads

```bash
mkdir backend/uploads
```

## Chạy ứng dụng

### Chạy Backend

```bash
npm run dev:backend
```

Backend sẽ chạy tại: http://localhost:5000

### Chạy Frontend

```bash
npm run dev:frontend
```

Frontend sẽ chạy tại: http://localhost:3000

## API Endpoints

### Candidates (Thí sinh)

- `POST /api/candidates/register` - Đăng ký thí sinh mới
- `GET /api/candidates` - Lấy danh sách tất cả thí sinh
- `GET /api/candidates/:id` - Lấy thông tin thí sinh theo ID
- `PUT /api/candidates/:id` - Cập nhật thông tin thí sinh
- `DELETE /api/candidates/:id` - Xóa thí sinh
- `GET /api/candidates/search/cmnd/:cmnd` - Tra cứu theo CMND/CCCD

### Documents (Tài liệu)

- `POST /api/documents/upload` - Upload tài liệu
- `GET /api/documents/candidate/:candidate_id` - Lấy danh sách tài liệu của thí sinh
- `DELETE /api/documents/:id` - Xóa tài liệu

### Results (Kết quả)

- `PUT /api/results/:candidate_id` - Cập nhật kết quả tuyển sinh
- `GET /api/results/:candidate_id` - Lấy kết quả theo candidate_id
- `GET /api/results/search/cmnd/:cmnd` - Tra cứu kết quả theo CMND/CCCD

## Cấu trúc Database

### Bảng `candidates`
- Thông tin thí sinh đăng ký

### Bảng `documents`
- Tài liệu đã upload của thí sinh

### Bảng `results`
- Kết quả tuyển sinh và điểm thi

## Tính năng

1. **Đăng ký thông tin**: Thí sinh có thể đăng ký thông tin tuyển sinh
2. **Quản lý hồ sơ**: Quản trị viên có thể xem, sửa, xóa thông tin thí sinh
3. **Upload tài liệu**: Upload các tài liệu cần thiết (CMND, bằng tốt nghiệp, học bạ, v.v.)
4. **Tra cứu kết quả**: Tra cứu kết quả tuyển sinh bằng CMND/CCCD

