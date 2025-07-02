# 🧠 Hệ thống Trắc nghiệm AI (Phiên bản 2.0)

[![Deploy](https://img.shields.io/badge/Deploy-GitHub%20Pages-blue)](https://github.com)
[![AI](https://img.shields.io/badge/AI-Gemini%20API-orange)](https://makersuite.google.com)
[![Database](https://img.shields.io/badge/Database-Firebase-yellow)](https://firebase.google.com)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

Hệ thống trắc nghiệm AI với **2 giao diện riêng biệt** (Admin & User), tích hợp **Firebase Database** để đồng bộ dữ liệu giữa các thiết bị và **thống kê chi tiết** người dùng.

## 🆕 Cải tiến phiên bản 2.0

### 🔑 Phân quyền rõ ràng:
- **👨‍💼 Admin**: Mật khẩu → Quản lý câu hỏi + Xem thống kê
- **👤 User**: Chỉ cần tên → Làm bài + Xem kết quả

### 💾 Database thực (Firebase):
- ✅ Đồng bộ câu hỏi giữa mọi thiết bị  
- ✅ Lưu lịch sử làm bài của user
- ✅ Backup tự động LocalStorage
- ✅ Offline mode khi mất mạng

### 📊 Thống kê chi tiết:
- 📈 Số lượng user, câu hỏi, lượt làm bài
- 🏆 Điểm trung bình, điểm cao nhất
- ⏱️ Thời gian hoàn thành 
- 📋 Lịch sử chi tiết từng user

## ✨ Tính năng theo vai trò

### 👨‍💼 Giao diện Admin
- **Dashboard thống kê**: Cards tổng quan + bảng chi tiết
- **Quản lý câu hỏi**: Thêm/Xóa câu hỏi với hình ảnh
- **Cài đặt API**: Quản lý Gemini API keys (backup tự động)
- **Thống kê User**: Xem ai làm bài, bao nhiêu lần, điểm số, thời gian

### 👤 Giao diện User  
- **Chọn bộ đề**: Danh sách đề thi có sẵn
- **Làm bài trắc nghiệm**: Giao diện thân thiện + timer
- **AI giải thích**: Tự động khi trả lời sai (không cần API key)
- **Kết quả chi tiết**: Điểm số + thời gian hoàn thành

## 🚀 Hướng dẫn Deploy

### Bước 1: Cấu hình Firebase (BẮT BUỘC)

📋 **Xem hướng dẫn chi tiết**: [firebase-config.md](firebase-config.md)

1. Tạo project Firebase miễn phí
2. Enable Firestore Database  
3. Copy config vào `index.html`
4. Cấu hình security rules

### Bước 2: Upload lên GitHub

#### 🔄 Cách 1: Git Command Line
```bash
git clone https://github.com/hannhu11/quiz_ai_system.git
cd quiz-ai-system

# Cập nhật Firebase config trong index.html
# Rồi commit và push

git add .
git commit -m "🎉 Deploy Quiz AI System v2.0"
git push origin main
```

#### 📤 Cách 2: Upload trực tiếp
1. Vào GitHub repository
2. Upload các files: `index.html`, `README.md`, `firebase-config.md`
3. Commit với message: `🎉 Deploy Quiz AI System v2.0`

### Bước 3: Kích hoạt GitHub Pages

1. **Settings** → **Pages**
2. Source: **Deploy from branch**
3. Branch: **main** / Folder: **/ (root)**
4. **Save**

### Bước 4: Cấu hình API Keys

1. Lấy **Gemini API keys** từ [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Truy cập website: `https://hannhu11.github.io/quiz_ai_system`
3. Đăng nhập Admin (mật khẩu: `admin123`)
4. Vào tab **"🔑 Cài đặt API"** → Nhập 2 API keys → **Lưu**

## 📱 Hướng dẫn sử dụng

### 👨‍💼 Cho Admin:

1. **Đăng nhập**: 
   - Click **"⚙️ Quản trị viên"**
   - Nhập mật khẩu: `admin123`

2. **Thêm câu hỏi**:
   - Tab **"📚 Quản lý câu hỏi"**
   - Upload hình ảnh + nhập 4 đáp án
   - Chọn đáp án đúng → **"➕ Thêm câu hỏi"**

3. **Xem thống kê**:
   - Dashboard hiển thị tổng quan
   - Tab **"👥 Thống kê User"** → Chi tiết từng người

### 👤 Cho User:

1. **Bắt đầu**:
   - Click **"👤 Người dùng"**
   - Nhập tên → **"Bắt đầu làm bài"**

2. **Làm bài**:
   - Chọn bộ đề → Trả lời từng câu
   - **Đúng**: Chuyển câu tiếp theo
   - **Sai**: AI giải thích chi tiết

3. **Xem kết quả**:
   - Điểm số + thời gian hoàn thành
   - Có thể làm lại hoặc chọn đề khác

## 🛠️ Cấu trúc dự án

```
quiz-ai-system/
├── index.html              # Ứng dụng chính (2 giao diện)
├── README.md               # Tài liệu này
├── firebase-config.md      # Hướng dẫn cấu hình Firebase
└── .gitignore             # Ignore files
```

## 🔧 Tùy chỉnh hệ thống

### Thay đổi mật khẩu Admin:
```javascript
// Trong index.html, tìm dòng:
const ADMIN_PASSWORD = 'admin123';
// Thay đổi thành mật khẩu mong muốn
```

### Thêm nhiều bộ đề:
```javascript
// Có thể mở rộng để tạo nhiều collections khác nhau
// Ví dụ: questions-math, questions-english, etc.
```

### Tùy chỉnh giao diện:
```css
/* Thay đổi màu chủ đạo */
.bg-blue-500 { background-color: #your-color; }
.text-blue-600 { color: #your-color; }
```

## 📊 Database Schema (Firebase)

### Collections:

#### `questions`
```json
{
  "id": "auto-generated",
  "image": "base64-string",
  "content": "Nội dung câu hỏi",
  "answers": {
    "A": "Đáp án A",
    "B": "Đáp án B", 
    "C": "Đáp án C",
    "D": "Đáp án D"
  },
  "correctAnswer": "A",
  "createdAt": "timestamp",
  "createdBy": "Admin"
}
```

#### `userSessions`
```json
{
  "id": "auto-generated",
  "userName": "Tên người dùng",
  "score": 8,
  "totalQuestions": 10,
  "completionTime": 180,
  "completedAt": "timestamp"
}
```

#### `settings`
```json
{
  "id": "auto-generated", 
  "type": "apiKeys",
  "keys": {
    "key1": "gemini-api-key-1",
    "key2": "gemini-api-key-2"
  },
  "updatedAt": "timestamp"
}
```

## 🔒 Bảo mật

### Mức độ hiện tại (Test mode):
- ✅ Phân quyền cơ bản Admin/User
- ✅ Firebase rules test mode
- ⚠️ Mật khẩu admin đơn giản

### Nâng cấp bảo mật:
- 🔐 JWT authentication
- 🛡️ Firebase security rules nghiêm ngặt  
- 🔑 Mật khẩu admin phức tạp + hash
- 📧 Email verification

## 🆘 Troubleshooting

### ❌ Dữ liệu không đồng bộ:
1. Kiểm tra Firebase config trong `index.html`
2. Xem Firebase Console có data không
3. Kiểm tra Network tab có lỗi gì không

### ❌ AI không hoạt động:
1. Kiểm tra Gemini API keys đã nhập chưa
2. Đảm bảo API keys còn quota
3. Thử API key backup

### ❌ Website không load:
1. Kiểm tra GitHub Pages đã enable
2. Repository phải Public
3. File phải tên `index.html`

## 🎯 Roadmap tương lai

### Version 2.1:
- [ ] 📱 Progressive Web App (PWA)
- [ ] 🔐 Authentication nâng cao
- [ ] 📊 Dashboard analytics chi tiết hơn
- [ ] 🎵 Âm thanh hiệu ứng

### Version 3.0:
- [ ] 🌐 Đa ngôn ngữ (EN/VI)
- [ ] 📁 Nhiều categories câu hỏi
- [ ] 🏆 Ranking system
- [ ] 📤 Export/Import câu hỏi Excel

## 🤝 Đóng góp

1. Fork repository
2. Tạo branch: `git checkout -b feature/new-feature`
3. Commit: `git commit -m 'Add new feature'`
4. Push: `git push origin feature/new-feature`  
5. Tạo Pull Request

## 📞 Hỗ trợ

- 🐛 **Bug reports**: [GitHub Issues](https://github.com/hannhu11/quiz_ai_system/issues)
- 💡 **Feature requests**: [GitHub Discussions](https://github.com/hannhu11/quiz_ai_system/discussions)
- 📧 **Email**: your-email@domain.com

---

## 🎯 So sánh phiên bản

| Tính năng | v1.0 | v2.0 |
|-----------|------|------|
| Lưu trữ | LocalStorage | Firebase + Backup |
| Giao diện | Single | Admin + User riêng |  
| Thống kê | Không | Có dashboard |
| Đồng bộ | Không | Có (multi-device) |
| API management | User tự nhập | Admin cung cấp |
| User tracking | Không | Có chi tiết |

⭐ **Nếu hữu ích, hãy star repo này nhé!** ⭐ 