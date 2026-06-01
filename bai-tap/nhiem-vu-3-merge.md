# Nhiệm vụ 3: Gộp nhánh (merge)

🎯 **Mục tiêu:** Gộp một nhánh có sẵn vào nhánh của em.

Repo này đã có sẵn nhánh **`luyen-tap/them-mon-an`** (do thầy/cô chuẩn bị). Nhánh đó đã thêm vài món vào file [san-tap/thuc-don.txt](san-tap/thuc-don.txt). Việc của em là gộp nó vào nhánh mình.

## Việc cần làm

1. Lấy đầy đủ các nhánh từ GitHub về máy:

   ```bash
   git fetch origin
   git branch -a          # thay danh sach co luyen-tap/them-mon-an
   ```

2. Về nhánh của em và xem file thực đơn hiện tại (chỉ có "Nuoc loc"):

   ```bash
   git switch hoc-sinh/ten-cua-em
   ```

   Mở `bai-tap/san-tap/thuc-don.txt`.

3. Gộp nhánh có sẵn vào nhánh của em:

   ```bash
   git merge origin/luyen-tap/them-mon-an
   ```

4. Mở lại `thuc-don.txt`.

   > 👀 Quan sát: thực đơn giờ có thêm các món mới! Nội dung từ nhánh kia đã được gộp vào.

5. Xem sơ đồ để thấy hai nhánh đã nhập làm một:

   ```bash
   git log --oneline --graph --all
   ```

## ✅ Checklist

- [ ] Đã `git fetch` để thấy nhánh `luyen-tap/them-mon-an`
- [ ] Đã merge thành công (không lỗi)
- [ ] File `thuc-don.txt` có thêm món mới
- [ ] Hiểu được sơ đồ nhánh sau khi merge

## 💡 Ghi nhớ

- Luôn đứng ở **nhánh đích** (nhánh muốn NHẬN thay đổi) rồi mới `git merge nhanh-nguon`.
- Merge ở đây không bị xung đột vì hai nhánh sửa những dòng khác nhau. Nhiệm vụ 4 sẽ cho em gặp xung đột thật.
