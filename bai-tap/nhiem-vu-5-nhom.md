# Nhiệm vụ 5: Bài tập nhóm cả lớp

🎯 **Mục tiêu:** Trải nghiệm trọn vẹn quy trình làm việc nhóm thật: push nhánh lên GitHub và tạo Pull Request để gộp vào `main`.

Cả lớp sẽ cùng điền tên vào file chung [danh-sach-lop.txt](danh-sach-lop.txt).

## Việc cần làm

1. Cập nhật `main` mới nhất rồi tạo nhánh từ đó:

   ```bash
   git switch main
   git pull origin main
   git switch -c hoc-sinh/ten-cua-em-ds
   ```

2. Mở file [danh-sach-lop.txt](danh-sach-lop.txt) và thêm tên em vào một dòng mới ở cuối (đánh số tiếp theo).

3. Commit:

   ```bash
   git add bai-tap/danh-sach-lop.txt
   git commit -m "Them ten <ten em> vao danh sach lop"
   ```

4. Đẩy nhánh của em lên GitHub:

   ```bash
   git push -u origin hoc-sinh/ten-cua-em-ds
   ```

5. Vào trang GitHub của repo, bấm nút **"Compare & pull request"**, viết mô tả ngắn rồi tạo **Pull Request**.

6. Thầy/cô (hoặc bạn được phân công) sẽ xem và bấm **Merge** PR vào `main`.

7. Sau khi PR của em được merge, cập nhật lại:

   ```bash
   git switch main
   git pull origin main
   ```

   > 👀 Quan sát: file `danh-sach-lop.txt` trên `main` giờ có tên em cùng tên các bạn khác!

## ⚠️ Tình huống dễ gặp

Nếu khi push hoặc merge mà báo conflict ở `danh-sach-lop.txt` (vì bạn khác vừa thêm tên vào cùng vị trí), đừng lo, hãy xử lý y như **Nhiệm vụ 4**: mở file, giữ lại tên của cả hai, xóa các dấu xung đột, rồi `add` + `commit`.

## ✅ Checklist

- [ ] Đã tạo nhánh từ `main` mới nhất
- [ ] Đã thêm tên mình và commit
- [ ] Đã `git push` nhánh lên GitHub
- [ ] Đã tạo Pull Request
- [ ] Sau khi merge, thấy tên mình trong `main`

## 💡 Ghi nhớ quy trình làm nhóm

```
pull main  →  tao nhanh  →  code + commit  →  push nhanh  →  tao PR  →  merge  →  pull main
```
