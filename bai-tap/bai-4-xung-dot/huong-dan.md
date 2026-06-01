# Bài 4: Xử lý xung đột (merge conflict)

## Mục tiêu

- Hiểu vì sao xảy ra conflict
- Tự tạo ra một conflict (để hiểu bản chất)
- Giải conflict thủ công và hoàn tất merge

> Đừng sợ conflict! Đây là tình huống rất bình thường khi làm việc nhóm. Biết cách xử lý conflict là một kỹ năng quan trọng.

## Vì sao có conflict?

Conflict xảy ra khi **hai nhánh cùng sửa cùng một dòng** trong **cùng một file**. Git không thể tự quyết định giữ bản nào nên nhờ em chọn.

## Các bước thực hiện

### Bước 1: Chuẩn bị

```bash
mkdir tap-bai-4
cd tap-bai-4
git init
echo "Mau yeu thich cua lop la: xanh la" > khao-sat.txt
git add khao-sat.txt
git commit -m "Ghi nhan ket qua khao sat ban dau"
```

### Bước 2: Tạo nhánh và sửa dòng đó

```bash
git switch -c y-kien-to-1
echo "Mau yeu thich cua lop la: do" > khao-sat.txt
git add khao-sat.txt
git commit -m "To 1 cho rang mau do"
```

### Bước 3: Về main và sửa CÙNG dòng đó theo cách khác

```bash
git switch main
echo "Mau yeu thich cua lop la: vang" > khao-sat.txt
git add khao-sat.txt
git commit -m "Main ghi nhan mau vang"
```

### Bước 4: Merge và gặp conflict

```bash
git merge y-kien-to-1
```

> Quan sát: Git báo lỗi `CONFLICT (content): Merge conflict in khao-sat.txt` và `Automatic merge failed`.

### Bước 5: Mở file xem Git đánh dấu gì

Mở `khao-sat.txt`, em sẽ thấy:

```
<<<<<<< HEAD
Mau yeu thich cua lop la: vang
=======
Mau yeu thich cua lop la: do
>>>>>>> y-kien-to-1
```

Giải thích:

- Phần giữa `<<<<<<< HEAD` và `=======`: nội dung ở nhánh hiện tại (`main`).
- Phần giữa `=======` và `>>>>>>> y-kien-to-1`: nội dung ở nhánh được merge.

### Bước 6: Giải conflict

Quyết định giữ nội dung nào, rồi **xóa hết các dòng dấu** `<<<<<<<`, `=======`, `>>>>>>>`. Ví dụ em quyết định kết hợp cả hai:

```
Mau yeu thich cua lop la: do va vang
```

Lưu file lại.

### Bước 7: Hoàn tất merge

```bash
git add khao-sat.txt
git commit -m "Giai quyet xung dot: chon do va vang"
```

### Bước 8: Kiểm tra

```bash
git log --oneline --graph --all
cat khao-sat.txt
```

## Câu hỏi ôn tập

1. Điều kiện nào dẫn tới conflict?
2. Ba dấu hiệu `<<<<<<<`, `=======`, `>>>>>>>` có ý nghĩa gì?
3. Sau khi sửa xong file conflict, hai lệnh cần chạy là gì?

## Mẹo

- Nếu lỡ tay và muốn hủy merge để làm lại từ đầu: `git merge --abort`.
- Các editor như VS Code có nút bấm "Accept Current / Accept Incoming / Accept Both" giúp giải conflict nhanh hơn.
