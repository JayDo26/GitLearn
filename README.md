# GitLearn - Học Git từ cơ bản đến merge nhánh

Đây là repo bài tập dùng để **dạy và thực hành Git**: các lệnh cơ bản, làm việc với nhánh (branch) và gộp nhánh (merge).

Tài liệu được chia làm 2 phần:

- **Phần lý thuyết** (file README này): giải thích từng nhóm lệnh Git.
- **Phần thực hành** (thư mục [bai-tap/](bai-tap/)): 5 bài tập theo cấp độ tăng dần, mỗi bài có hướng dẫn từng bước.

> Gợi ý cho giáo viên: cho học sinh làm lần lượt từ Bài 1 đến Bài 5. Mỗi bài nên làm trong một thư mục riêng để không ảnh hưởng lẫn nhau.

---

## Mục lục

1. [Git là gì?](#1-git-là-gì)
2. [Cài đặt và cấu hình ban đầu](#2-cài-đặt-và-cấu-hình-ban-đầu)
3. [3 vùng làm việc trong Git](#3-ba-vùng-làm-việc-trong-git)
4. [Nhóm lệnh cơ bản](#4-nhóm-lệnh-cơ-bản)
5. [Làm việc với nhánh (branch)](#5-làm-việc-với-nhánh-branch)
6. [Gộp nhánh (merge)](#6-gộp-nhánh-merge)
7. [Xử lý xung đột (conflict)](#7-xử-lý-xung-đột-conflict)
8. [Làm việc với remote (GitHub)](#8-làm-việc-với-remote-github)
9. [Bảng tra lệnh nhanh](#9-bảng-tra-lệnh-nhanh)

---

## 1. Git là gì?

**Git** là hệ thống quản lý phiên bản (version control). Nó giúp bạn:

- Lưu lại lịch sử thay đổi của code (ai sửa gì, lúc nào, tại sao).
- Quay về phiên bản cũ khi có lỗi.
- Nhiều người cùng làm trên một dự án mà không ghi đè lên nhau.

**GitHub** là dịch vụ lưu trữ repo Git trên mạng (giống như Google Drive nhưng dành cho code).

Phân biệt nhanh:

| Khái niệm | Ý nghĩa |
|-----------|---------|
| Git | Phần mềm chạy trên máy bạn |
| GitHub | Trang web lưu repo trên Internet |
| Repository (repo) | Một dự án được Git quản lý |
| Commit | Một "ảnh chụp" trạng thái code tại một thời điểm |
| Branch (nhánh) | Một dòng phát triển song song |

---

## 2. Cài đặt và cấu hình ban đầu

Sau khi cài Git, chạy 2 lệnh sau **một lần duy nhất** để khai báo tên và email (thông tin này sẽ gắn vào mỗi commit):

```bash
git config --global user.name "Tên của bạn"
git config --global user.email "email@example.com"
```

Kiểm tra cấu hình:

```bash
git config --list
```

---

## 3. Ba vùng làm việc trong Git

Đây là khái niệm **quan trọng nhất** cần hiểu. Một file trong Git đi qua 3 vùng:

```
  Working Directory   →   Staging Area   →   Repository
  (thư mục làm việc)      (vùng chờ)         (kho lưu trữ)

       git add  ────────────►
                              git commit  ────────────►
```

- **Working Directory**: nơi bạn sửa file thực tế.
- **Staging Area**: nơi "đánh dấu" những thay đổi sẽ được lưu (dùng `git add`).
- **Repository**: nơi lưu vĩnh viễn sau khi `git commit`.

Hãy hình dung như đóng gói hàng: `git add` = chọn món hàng cho vào thùng, `git commit` = dán tem niêm phong thùng lại.

---

## 4. Nhóm lệnh cơ bản

### Khởi tạo repo

```bash
git init          # Biến thư mục hiện tại thành một repo Git
```

### Kiểm tra trạng thái

```bash
git status        # Xem file nào đã sửa, file nào đang chờ commit
```

### Đưa file vào staging

```bash
git add ten-file.txt    # Thêm 1 file
git add .               # Thêm tất cả file đã thay đổi
```

### Lưu thay đổi (commit)

```bash
git commit -m "Mô tả ngắn gọn thay đổi"
```

> Lời khuyên: viết commit message rõ ràng, ví dụ "Them trang dang nhap" thay vì "sua bug".

### Xem lịch sử

```bash
git log                 # Xem toàn bộ lịch sử commit
git log --oneline       # Xem gọn, mỗi commit 1 dòng
git log --oneline --graph --all   # Xem dạng sơ đồ cây (rất hữu ích khi học nhánh)
```

### Xem chi tiết thay đổi

```bash
git diff                # Xem những dòng đã sửa nhưng chưa add
git diff --staged       # Xem những dòng đã add nhưng chưa commit
```

---

## 5. Làm việc với nhánh (branch)

Nhánh giống như một "bản sao song song" của dự án. Bạn có thể thử nghiệm tính năng mới trên nhánh riêng mà không làm hỏng nhánh chính (`main`).

```bash
git branch                  # Liệt kê các nhánh (dấu * là nhánh hiện tại)
git branch ten-nhanh        # Tạo nhánh mới
git switch ten-nhanh        # Chuyển sang nhánh đó (lệnh mới, khuyên dùng)
git switch -c ten-nhanh     # Tạo VÀ chuyển sang nhánh mới cùng lúc
git branch -d ten-nhanh     # Xóa nhánh (sau khi đã merge)
```

> Lệnh cũ `git checkout ten-nhanh` cũng dùng để chuyển nhánh. Hiện nay `git switch` được khuyên dùng vì rõ nghĩa hơn.

Hình dung về nhánh:

```
            o---o---o   nhanh-tinh-nang
           /
  o---o---o---o   main
```

---

## 6. Gộp nhánh (merge)

Sau khi làm xong tính năng trên nhánh riêng, bạn gộp nó về nhánh chính.

**Quy trình chuẩn:**

```bash
git switch main             # 1. Về nhánh đích (nhánh muốn nhận thay đổi)
git merge ten-nhanh         # 2. Gộp nhánh kia vào nhánh hiện tại
```

Có 2 kiểu merge:

**a) Fast-forward** (tua nhanh): khi nhánh `main` không có commit mới nào kể từ lúc tách nhánh. Git chỉ cần "dời con trỏ" tới.

```
Trước:  o---o---o (main)
                 \
                  o---o (feature)

Sau:    o---o---o---o---o (main, feature)
```

**b) Merge commit** (commit gộp): khi cả 2 nhánh đều có commit mới. Git tạo một commit đặc biệt nối 2 nhánh.

```
Trước:  o---o---o---A (main)
                 \
                  o---B (feature)

Sau:    o---o---o---A---M (main)
                 \     /
                  o---B
```

---

## 7. Xử lý xung đột (conflict)

**Conflict** xảy ra khi 2 nhánh cùng sửa **cùng một dòng** trong **cùng một file**. Git không biết giữ bản nào nên nhờ bạn quyết định.

Khi merge bị conflict, Git đánh dấu trong file như sau:

```
<<<<<<< HEAD
Nội dung ở nhánh hiện tại (main)
=======
Nội dung ở nhánh được merge vào (feature)
>>>>>>> feature
```

**Cách xử lý:**

1. Mở file bị conflict, xóa các dòng dấu `<<<<<<<`, `=======`, `>>>>>>>`.
2. Giữ lại nội dung đúng (có thể giữ một bên, hoặc kết hợp cả hai).
3. Lưu file, rồi chạy:

```bash
git add ten-file-da-sua.txt
git commit               # Hoàn tất việc merge
```

> Đừng hoảng khi gặp conflict, đây là chuyện bình thường. Bài 4 trong thư mục bài tập sẽ hướng dẫn tạo và giải conflict từng bước.

---

## 8. Làm việc với remote (GitHub)

```bash
git clone <url>                       # Tải repo từ GitHub về máy
git remote add origin <url>           # Liên kết repo local với repo trên GitHub
git remote -v                         # Xem các remote đang có

git push -u origin main               # Đẩy nhánh main lên (lần đầu, có -u)
git push                              # Đẩy lên (các lần sau)
git pull                             # Kéo thay đổi mới nhất từ GitHub về
git fetch                            # Tải về nhưng chưa gộp (xem trước)
```

Quy trình làm việc nhóm điển hình:

```
git pull          → lấy code mới nhất về
... viết code ...
git add .
git commit -m "..."
git push          → đẩy code của mình lên
```

---

## 9. Bảng tra lệnh nhanh

| Mục đích | Lệnh |
|----------|------|
| Khởi tạo repo | `git init` |
| Xem trạng thái | `git status` |
| Thêm vào staging | `git add .` |
| Lưu commit | `git commit -m "..."` |
| Xem lịch sử | `git log --oneline --graph --all` |
| Tạo + chuyển nhánh | `git switch -c ten-nhanh` |
| Chuyển nhánh | `git switch ten-nhanh` |
| Liệt kê nhánh | `git branch` |
| Gộp nhánh | `git merge ten-nhanh` |
| Xóa nhánh | `git branch -d ten-nhanh` |
| Liên kết GitHub | `git remote add origin <url>` |
| Đẩy lên | `git push` |
| Kéo về | `git pull` |
| Tải repo về | `git clone <url>` |

---

## Bắt đầu thực hành

Mở thư mục [bai-tap/](bai-tap/) và làm theo thứ tự:

1. [Bài 1: Lệnh cơ bản](bai-tap/bai-1-co-ban/huong-dan.md)
2. [Bài 2: Làm việc với nhánh](bai-tap/bai-2-nhanh/huong-dan.md)
3. [Bài 3: Gộp nhánh (merge)](bai-tap/bai-3-merge/huong-dan.md)
4. [Bài 4: Xử lý xung đột](bai-tap/bai-4-xung-dot/huong-dan.md)
5. [Bài 5: Làm việc với GitHub](bai-tap/bai-5-remote/huong-dan.md)
6. [Bài 6: Quy trình làm việc nhóm (pull/push/merge, Pull Request)](bai-tap/bai-6-team-flow/huong-dan.md)

Chúc các em học vui và nhớ lâu!
