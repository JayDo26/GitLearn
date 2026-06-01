# Nhiệm vụ 2: Tạo và chuyển nhánh

🎯 **Mục tiêu:** Hiểu nhánh là các "dòng làm việc song song" và chuyển qua lại được giữa chúng.

## Việc cần làm

1. Xem các nhánh hiện có:

   ```bash
   git branch
   ```

2. Từ nhánh của em, tạo một nhánh con để thử nghiệm:

   ```bash
   git switch -c hoc-sinh/ten-cua-em-thu-nghiem
   ```

3. Sửa file [san-tap/ho-so-cua-ban.txt](san-tap/ho-so-cua-ban.txt): thêm một dòng "So thich:" rồi commit.

4. **Quay lại nhánh trước đó** và mở lại file:

   ```bash
   git switch hoc-sinh/ten-cua-em
   ```

   > 👀 Quan sát: dòng "So thich:" **biến mất**! Vì nó chỉ tồn tại ở nhánh thử nghiệm. Đây chính là điều kỳ diệu của nhánh.

5. Chuyển qua lại vài lần để thấy rõ nội dung file thay đổi theo nhánh:

   ```bash
   git switch hoc-sinh/ten-cua-em-thu-nghiem   # co dong So thich
   git switch hoc-sinh/ten-cua-em              # khong co
   ```

6. Xem sơ đồ nhánh:

   ```bash
   git log --oneline --graph --all
   ```

## ✅ Checklist

- [ ] Đã tạo nhánh thử nghiệm
- [ ] Hiểu vì sao nội dung file đổi khi chuyển nhánh
- [ ] Xem được sơ đồ nhánh dạng cây

## 💡 Ghi nhớ

- `git switch -c <ten>` = tạo mới + chuyển sang.
- `git switch <ten>` = chuyển sang nhánh đã có.
- Thay đổi trên nhánh này KHÔNG ảnh hưởng nhánh kia, cho tới khi em `merge`.
