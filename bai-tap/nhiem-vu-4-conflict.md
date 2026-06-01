# Nhiệm vụ 4: Tạo và giải quyết xung đột (conflict)

🎯 **Mục tiêu:** Gặp một conflict thật và tự tay giải quyết. Đây là kỹ năng quan trọng nhất khi làm nhóm.

Repo có sẵn **hai nhánh** cùng sửa **một dòng** trong file [san-tap/khao-sat.txt](san-tap/khao-sat.txt) theo hai cách khác nhau:

- `luyen-tap/y-kien-to-1` cho rằng môn thể thao yêu thích là **Bóng đá**.
- `luyen-tap/y-kien-to-2` cho rằng đó là **Cầu lông**.

Khi gộp cả hai, Git không biết nghe ai, sẽ báo conflict.

## Việc cần làm

1. Lấy các nhánh về và đứng ở nhánh của em:

   ```bash
   git fetch origin
   git checkout hoc-sinh/ten-cua-em
   ```

2. Gộp nhánh tổ 1 (lần này êm xuôi):

   ```bash
   git merge origin/luyen-tap/y-kien-to-1
   ```

3. Bây giờ gộp tiếp nhánh tổ 2 (sẽ ra conflict):

   ```bash
   git merge origin/luyen-tap/y-kien-to-2
   ```

   > 👀 Git báo: `CONFLICT (content): Merge conflict in bai-tap/san-tap/khao-sat.txt`

4. Mở file `bai-tap/san-tap/khao-sat.txt`, em sẽ thấy:

   ```
   <<<<<<< HEAD
   Mon the thao yeu thich nhat cua lop la: Bong da
   =======
   Mon the thao yeu thich nhat cua lop la: Cau long
   >>>>>>> origin/luyen-tap/y-kien-to-2
   ```

5. **Giải quyết:** xóa hết các dòng dấu `<<<<<<<`, `=======`, `>>>>>>>`, và quyết định nội dung cuối cùng. Ví dụ kết hợp cả hai:

   ```
   Mon the thao yeu thich nhat cua lop la: Bong da va Cau long
   ```

6. Lưu file, rồi hoàn tất merge:

   ```bash
   git add bai-tap/san-tap/khao-sat.txt
   git commit -m "Giai quyet xung dot khao sat the thao"
   ```

## ✅ Checklist

- [ ] Đã gây ra được conflict (Git báo CONFLICT)
- [ ] Đã xóa hết 3 loại dấu `<<<<<<<` `=======` `>>>>>>>`
- [ ] Đã `git add` + `git commit` để hoàn tất
- [ ] `git status` báo sạch sẽ (working tree clean)

## 💡 Mẹo

- Lỡ rối quá muốn làm lại từ đầu: `git merge --abort`.
- VS Code có nút "Accept Current / Incoming / Both" giúp giải conflict bằng chuột.
