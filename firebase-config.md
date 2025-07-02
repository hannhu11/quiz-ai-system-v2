# 🔥 Hướng dẫn cấu hình Firebase

## Bước 1: Tạo project Firebase

1. Truy cập [Firebase Console](https://console.firebase.google.com/)
2. Click **"Add project"**
3. Đặt tên project: `quiz-ai-system`
4. Disable Google Analytics (không cần thiết)
5. Click **"Create project"**

## Bước 2: Thêm Web App

1. Trong project, click biểu tượng **Web** `</>`
2. Đặt tên app: `Quiz AI System`
3. **KHÔNG** check "Firebase Hosting"
4. Click **"Register app"**
5. **Copy** config object (sẽ cần paste vào code)

## Bước 3: Cấu hình Firestore Database

1. Trong sidebar, vào **"Firestore Database"**
2. Click **"Create database"**
3. Chọn **"Start in test mode"** (để dễ test)
4. Chọn location gần nhất (asia-southeast1)
5. Click **"Done"**

## Bước 4: Cập nhật code

Mở file `index.html`, tìm dòng:

```javascript
const firebaseConfig = {
    // Người dùng sẽ cần config này
    apiKey: "your-api-key",
    authDomain: "your-project.firebaseapp.com",
    projectId: "your-project-id",
    storageBucket: "your-project.appspot.com",
    messagingSenderId: "123456789",
    appId: "your-app-id"
};
```

Thay thế bằng config Firebase thực của bạn.

## Bước 5: Cấu hình Security Rules

Trong **Firestore Database → Rules**, thay rules bằng:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Cho phép đọc/ghi tất cả (chỉ dùng cho test)
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```

**⚠️ Lưu ý**: Rules này cho phép tất cả truy cập, chỉ dùng để test!

## Bước 6: Test kết nối

1. Deploy website lên GitHub Pages
2. Thử đăng nhập Admin (mật khẩu: `admin123`)
3. Thêm 1 câu hỏi test
4. Kiểm tra trong Firebase Console → Firestore → Collections

Nếu thấy data xuất hiện, nghĩa là đã kết nối thành công!

## 🔒 Bảo mật nâng cao (sau khi test xong)

Thay Security Rules bằng:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Chỉ cho phép đọc questions và userSessions
    match /questions/{questionId} {
      allow read: if true;
      allow write: if false; // Chỉ admin có thể ghi qua code
    }
    
    match /userSessions/{sessionId} {
      allow read, write: if true;
    }
    
    match /settings/{settingId} {
      allow read, write: if false; // Chỉ admin qua code
    }
  }
}
```

## 🆘 Troubleshooting

### Lỗi "Firebase not defined"
- Kiểm tra Internet connection
- Đảm bảo script Firebase đã load

### Lỗi "Permission denied"
- Kiểm tra Firestore Rules
- Thử rules test mode trước

### Data không sync giữa thiết bị
- Kiểm tra Firebase config đúng chưa
- Xem Network tab trong DevTools có lỗi gì không 