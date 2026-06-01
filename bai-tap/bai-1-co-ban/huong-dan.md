# Bài 1: Lệnh Git cơ bản

## Mục tiêu

Sau bài này em sẽ biết cách:

- Tạo một repo Git mới (`git init`)
- Theo dõi trạng thái file (`git status`)
- Đưa file vào vùng chờ (`git add`)
- Lưu lại thay đổi (`git commit`)
- Xem lại lịch sử (`git log`)

## Các bước thực hiện

### Bước 1: Tạo thư mục và khởi tạo repo

```bash
mkdir tap-bai-1
cd tap-bai-1
git init
```

Em sẽ thấy dòng thông báo `Initialized empty Git repository...`. Thư mục giờ đã được Git quản lý.

### Bước 2: Tạo một file mới

Tạo file `gioi-thieu.txt` với nội dung tự do, ví dụ:

```
Xin chao, day la bai tap Git dau tien cua toi.
```

### Bước 3: Kiểm tra trạng thái

```bash
git status
```

> Quan sát: Git báo `gioi-thieu.txt` đang ở trạng thái **Untracked** (màu đỏ), nghĩa là chưa được theo dõi.

### Bước 4: Đưa file vào staging

```bash
git add gioi-thieu.txt
git status
```

> Quan sát: file giờ chuyển sang **Changes to be committed** (màu xanh).

### Bước 5: Commit lần đầu

```bash
git commit -m "Them file gioi thieu"
```

### Bước 6: Sửa file và commit lần 2

Thêm một dòng vào `gioi-thieu.txt`:

```
Toi dang hoc cac lenh add va commit.
```

Rồi chạy:

```bash
git status
git add gioi-thieu.txt
git commit -m "Bo sung dong thu hai"
```

### Bước 7: Xem lịch sử

```bash
git log
git log --oneline
```

> Quan sát: em đã có 2 commit. Mỗi commit có một mã băm (hash) riêng.

## Câu hỏi ôn tập

1. Sự khác nhau giữa `git add` và `git commit` là gì?
2. Lệnh nào dùng để xem file nào đang chờ commit?
3. Tại sao nên viết commit message rõ ràng?

## Thử thách thêm

- Tạo thêm file `ghi-chu.txt` và commit nó.
- Dùng `git add .` để thêm nhiều file cùng lúc.
- Xem `git log --oneline --graph` trông như thế nào.
