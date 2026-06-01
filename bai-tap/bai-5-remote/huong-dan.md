# Bài 5: Làm việc với GitHub (remote)

## Mục tiêu

- Liên kết repo trên máy với GitHub (`git remote`)
- Đẩy code lên GitHub (`git push`)
- Kéo code mới về (`git pull`)
- Hiểu quy trình làm việc nhóm

## Chuẩn bị

Em cần:

- Một tài khoản GitHub (đăng ký miễn phí tại github.com).
- Một repo trống trên GitHub (bấm nút **New repository**).

## Phần A: Đẩy repo có sẵn lên GitHub

Đây chính là các lệnh đã dùng để tạo repo GitLearn này:

```bash
echo "# Du an cua toi" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/TEN-CUA-BAN/TEN-REPO.git
git push -u origin main
```

Giải thích từng lệnh:

| Lệnh | Ý nghĩa |
|------|---------|
| `git init` | Tạo repo Git trên máy |
| `git branch -M main` | Đổi tên nhánh chính thành `main` |
| `git remote add origin <url>` | Đặt tên `origin` cho repo trên GitHub |
| `git push -u origin main` | Đẩy nhánh `main` lên, `-u` để lần sau chỉ cần `git push` |

> `origin` chỉ là tên gọi (alias) cho địa chỉ GitHub, để khỏi gõ URL dài mỗi lần.

## Phần B: Tải repo từ GitHub về (clone)

```bash
git clone https://github.com/TEN-CUA-BAN/TEN-REPO.git
cd TEN-REPO
```

> `git clone` tự động làm luôn `init` + `remote add` + tải toàn bộ lịch sử về.

## Phần C: Quy trình làm việc hằng ngày

```bash
git pull                       # 1. Lấy code mới nhất từ GitHub
# ... viết / sửa code ...
git add .                      # 2. Đưa thay đổi vào staging
git commit -m "Mo ta thay doi" # 3. Lưu lại
git push                       # 4. Đẩy lên GitHub
```

**Luôn `git pull` trước khi bắt đầu làm** để tránh xung đột với người khác.

## Phần D: Bài tập làm việc nhóm (2 người)

Bài này cần 2 bạn, hoặc 1 bạn dùng 2 thư mục khác nhau để giả lập.

1. Bạn A: tạo repo, push file `thanh-vien.txt` lên GitHub.
2. Bạn B: `git clone` repo về, thêm tên mình vào file, `commit` và `push`.
3. Bạn A: chạy `git pull` để nhận thay đổi của bạn B.

> Quan sát: code của 2 người đã được đồng bộ qua GitHub.

## Câu hỏi ôn tập

1. `origin` là gì?
2. Vì sao nên `git pull` trước khi làm việc?
3. `git clone` khác `git pull` ở điểm nào?
4. Lần đầu push dùng `git push -u origin main`, các lần sau dùng gì?

## Lưu ý về xác thực

GitHub hiện không cho dùng mật khẩu khi push. Em cần dùng một trong hai cách:

- **Personal Access Token** (token thay cho mật khẩu), hoặc
- **SSH key**.

Tìm hiểu thêm tại phần Settings > Developer settings trên GitHub.
