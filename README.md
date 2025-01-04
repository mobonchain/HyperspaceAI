# Hướng Dẫn Chạy Node CLI Hyperspace AI

Chào mừng bạn đến với hướng dẫn chạy **Node CLI** trên hệ điều hành **Linux (Ubuntu)** Nếu bạn muốn chạy trên **Windows** hay **macOS** với các tùy chọn **CPU/GPU** vui lòng tham khảo tại **[https://hyper.space/downloads](https://hyper.space/downloads)**.

## 1. Lấy Key
Truy cập: **[https://node.hyper.space/](https://node.hyper.space/)** để lấy key và lưu lại.

## 2. Chuẩn bị môi trường
Chuẩn bị VPS Ubuntu với phiên bản mới nhất (24.04).

## 3. Thực hiện các bước cài đặt

Chạy lần lượt các lệnh sau:

### Bước 1: Tải và cài đặt Hyperspace
```bash
curl https://download.hyper.space/api/install | bash
```

### Bước 2: Tải lại cấu hình bash
```bash
source /root/.bashrc
```

### Bước 3: Tạo file chứa key
```bash
nano key.pem
```
- Dán key đã lấy từ bước 1 vào file.
- Nhấn `Ctrl + O`, rồi nhấn `Enter` để lưu file.
- Nhấn `Ctrl + X` để thoát.

### Bước 4: Mở screen để chạy node
```bash
screen -S hyperspace
```

### Bước 5: Khởi chạy node
```bash
aios-cli start
```

### Bước 6: Thoát khỏi screen
Nhấn tổ hợp phím `Ctrl + A + D` để thoát khỏi phiên screen mà không dừng node đang chạy.

### Bước 7: Kiểm tra các model khả dụng (Tùy chọn có thể bỏ qua)
```bash
aios-cli models available
```

### Bước 8: Thêm model
```bash
aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf
```

### Bước 9: Nhập key để kết nối Hive
```bash
aios-cli hive import-keys ./key.pem
```

### Bước 10: Đăng nhập Hive
```bash
aios-cli hive login
```

### Bước 11: Kết nối với Hive
```bash
aios-cli hive connect
```

## 4. Kiểm tra thông tin

### Kiểm tra điểm tích lũy
```bash
aios-cli hive points
```

### Kiểm tra trạng thái node
```bash
aios-cli status
```

## 5. Khắc phục sự cố

Nếu node dừng hoặc gặp lỗi:

### Bước 1: Dừng node
```bash
aios-cli kill
```

### Bước 2: Mở lại screen và khởi động node
```bash
screen -S hyperspace
aios-cli start
```

### Bước 3: Thoát khỏi screen
Nhấn tổ hợp phím `Ctrl + A + D` để thoát khỏi phiên screen.

### Bước 4: Kết nối lại Hive
```bash
aios-cli hive connect
```
