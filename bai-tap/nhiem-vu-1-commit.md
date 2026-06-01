# Nhiệm vụ 1: Điền hồ sơ và commit

🎯 **Mục tiêu:** Làm quen với vòng lặp `sửa file → add → commit`.

## Việc cần làm

1. Đảm bảo em đang ở nhánh riêng của mình:

   ```bash
   git switch -c hoc-sinh/ten-cua-em
   ```

2. Mở file [san-tap/ho-so-cua-ban.txt](san-tap/ho-so-cua-ban.txt) và điền thông tin của em (họ tên, lớp, môn yêu thích...).

3. Xem Git nhận ra thay đổi gì:

   ```bash
   git status
   ```

4. Đưa file vào vùng chờ rồi commit:

   ```bash
   git add bai-tap/san-tap/ho-so-cua-ban.txt
   git commit -m "Dien ho so cua <ten em>"
   ```

5. Tạo thêm một file mới `bai-tap/san-tap/loi-chao-<ten>.txt` với một câu chào, rồi commit nó.

6. Xem lại lịch sử:

   ```bash
   git log --oneline
   ```

## ✅ Checklist

- [ ] Đang đứng trên nhánh `hoc-sinh/...` (kiểm tra bằng `git branch`)
- [ ] Đã điền hồ sơ và commit
- [ ] Đã tạo file lời chào và commit
- [ ] `git log --oneline` hiện ít nhất 2 commit của em

## 💡 Ghi nhớ

- `git add` = chọn thay đổi cho vào "thùng hàng".
- `git commit` = dán tem niêm phong thùng lại.
- Mỗi commit nên là một thay đổi nhỏ, có ý nghĩa.
