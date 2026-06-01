# Bài 2: Làm việc với nhánh (branch)

## Mục tiêu

- Hiểu nhánh là gì và tại sao cần dùng nhánh
- Tạo nhánh mới (`git branch`, `git switch -c`)
- Chuyển qua lại giữa các nhánh (`git switch`)
- Quan sát code thay đổi theo từng nhánh

## Bối cảnh

Tưởng tượng em đang viết một bài văn (`bai-van.txt`) trên nhánh `main`. Em muốn thử một cách mở bài khác nhưng chưa chắc hay hơn. Thay vì sửa thẳng, em tạo một nhánh riêng để thử.

## Các bước thực hiện

### Bước 1: Chuẩn bị

```bash
mkdir tap-bai-2
cd tap-bai-2
git init
```

Tạo file `bai-van.txt`:

```
Mo bai: Mua he la mua cua nhung ki niem.
```

Commit lại:

```bash
git add bai-van.txt
git commit -m "Viet mo bai ban dau"
```

### Bước 2: Xem nhánh hiện tại

```bash
git branch
```

> Quan sát: chỉ có một nhánh `main` (hoặc `master`), có dấu `*` phía trước.

### Bước 3: Tạo và chuyển sang nhánh mới

```bash
git switch -c thu-mo-bai-moi
git branch
```

> Quan sát: giờ có 2 nhánh, dấu `*` đã chuyển sang `thu-mo-bai-moi`.

### Bước 4: Sửa file trên nhánh mới

Sửa `bai-van.txt` thành:

```
Mo bai: Tieng ve keu ran ri bao hieu mua he da ve.
```

Commit:

```bash
git add bai-van.txt
git commit -m "Thu cach mo bai khac"
```

### Bước 5: Quay lại nhánh main và quan sát

```bash
git switch main
```

Bây giờ **mở file `bai-van.txt`** xem nội dung.

> Quan sát quan trọng: nội dung file trở về phiên bản cũ ("Mua he la mua cua nhung ki niem"). Thay đổi ở nhánh kia **không** ảnh hưởng tới `main`. Đây chính là sức mạnh của nhánh!

### Bước 6: Chuyển qua lại để thấy rõ

```bash
git switch thu-mo-bai-moi    # mở file: bản mới
git switch main              # mở file: bản cũ
```

### Bước 7: Xem sơ đồ nhánh

```bash
git log --oneline --graph --all
```

## Câu hỏi ôn tập

1. Vì sao dùng nhánh lại an toàn hơn sửa trực tiếp trên `main`?
2. `git switch -c ten-nhanh` khác gì `git switch ten-nhanh`?
3. Khi chuyển nhánh, tại sao nội dung file lại thay đổi?

## Thử thách thêm

- Tạo thêm nhánh `thu-ket-bai` và sửa phần kết.
- Dùng `git branch -d` để xóa một nhánh (lưu ý: phải đứng ở nhánh khác mới xóa được).
