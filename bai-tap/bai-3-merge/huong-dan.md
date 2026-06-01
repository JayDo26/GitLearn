# Bài 3: Gộp nhánh (merge)

## Mục tiêu

- Hiểu merge là gì
- Thực hiện merge kiểu **fast-forward**
- Thực hiện merge kiểu **merge commit**
- Đọc được sơ đồ nhánh sau khi merge

## Phần A: Merge fast-forward

Đây là trường hợp đơn giản nhất: nhánh `main` không thay đổi gì kể từ lúc tách nhánh.

### Bước 1: Chuẩn bị

```bash
mkdir tap-bai-3
cd tap-bai-3
git init
echo "Danh sach mon an:" > thuc-don.txt
git add thuc-don.txt
git commit -m "Tao thuc don"
```

### Bước 2: Tạo nhánh và thêm món

```bash
git switch -c them-mon-an
echo "- Pho bo" >> thuc-don.txt
git add thuc-don.txt
git commit -m "Them pho bo"
echo "- Bun cha" >> thuc-don.txt
git add thuc-don.txt
git commit -m "Them bun cha"
```

### Bước 3: Quay về main và merge

```bash
git switch main
git merge them-mon-an
```

> Quan sát: Git báo `Fast-forward`. Vì `main` không có commit mới nào, Git chỉ cần "tua tới" là xong. Mở `thuc-don.txt` sẽ thấy đủ 2 món.

### Bước 4: Dọn dẹp

```bash
git branch -d them-mon-an
git log --oneline --graph --all
```

---

## Phần B: Merge commit (có phân nhánh thật sự)

Trường hợp này cả hai nhánh đều có commit mới, Git phải tạo một commit gộp.

### Bước 1: Tạo nhánh tính năng

```bash
git switch -c them-trang-mieng
echo "- Che ba mau" >> thuc-don.txt
git add thuc-don.txt
git commit -m "Them trang mieng"
```

### Bước 2: Trong khi đó, main cũng thay đổi

```bash
git switch main
echo "(Cap nhat ngay 01/06)" >> ghi-chu.txt
git add ghi-chu.txt
git commit -m "Them ghi chu cho main"
```

> Lúc này 2 nhánh đã "rẽ đôi": mỗi nhánh có commit riêng.

### Bước 3: Merge

```bash
git merge them-trang-mieng
```

> Quan sát: Git mở cửa sổ soạn thảo yêu cầu nhập message cho **merge commit**. Cứ để mặc định, lưu và đóng lại (nếu là vim: gõ `:wq` rồi Enter; nếu là nano: `Ctrl+O` Enter rồi `Ctrl+X`).

### Bước 4: Xem kết quả

```bash
git log --oneline --graph --all
```

> Quan sát: sơ đồ rẽ nhánh rồi nhập lại tại một "merge commit" (chữ M).

## Câu hỏi ôn tập

1. Khi nào merge là fast-forward, khi nào tạo merge commit?
2. Trước khi merge, em phải đứng ở nhánh nào: nhánh nguồn hay nhánh đích?
3. Sau khi merge xong, có nên xóa nhánh tính năng không? Vì sao?

## Lưu ý

Trong Phần B, vì 2 nhánh sửa **hai file khác nhau** nên merge không bị xung đột. Nếu chúng sửa **cùng một dòng cùng một file**, em sẽ gặp conflict, đó chính là nội dung Bài 4.
