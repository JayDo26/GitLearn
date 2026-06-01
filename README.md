# 🎓 GitLearn - Sân chơi thực hành Git

Chào mừng các em! Đây là **repo chung của cả lớp** để luyện tập Git: tạo commit, làm việc với nhánh, merge và xử lý xung đột.

> ⚠️ Đây là nơi để **làm bài tập thật**. Các em sẽ trực tiếp tạo nhánh, commit và push lên repo này. Cứ mạnh dạn thử, làm sai cũng không sao, sửa lại được hết!

---

## 🚀 Bắt đầu trong 3 bước

### Bước 1: Tải repo về máy

```bash
git clone https://github.com/JayDo26/GitLearn.git
cd GitLearn
```

### Bước 2: Tạo nhánh riêng của em

**Quy tắc số 1: KHÔNG bao giờ làm việc trực tiếp trên `main`.** Mỗi em tự tạo một nhánh mang tên mình:

```bash
git checkout -b hoc-sinh/ten-cua-em
```

Ví dụ: `git checkout -b hoc-sinh/an`, `git checkout -b hoc-sinh/binh`.

### Bước 3: Vào làm bài tập

Mở thư mục [bai-tap/](bai-tap/) và làm theo thứ tự các nhiệm vụ.

---

## 📋 Các quy tắc của sân chơi chung

Vì cả lớp dùng chung repo này, hãy nhớ:

1. **Mỗi em một nhánh riêng** tên `hoc-sinh/<tên>`. Đừng push vào `main`.
2. **Luôn `git pull origin main`** trước khi bắt đầu để có nội dung mới nhất.
3. **Commit message viết bằng tiếng Việt không dấu**, rõ ràng (vd: "Them ten An vao danh sach lop").
4. **Đẩy nhánh của mình lên** bằng `git push -u origin hoc-sinh/<tên>`.
5. Khi làm bài nhóm, muốn đưa vào `main` thì **tạo Pull Request** trên GitHub để cô/thầy duyệt.

---

## 🗂️ Có gì trong repo này?

| Đường dẫn | Nội dung |
|-----------|----------|
| [bai-tap/](bai-tap/) | Các nhiệm vụ thực hành (làm theo thứ tự) |
| [bai-tap/san-tap/](bai-tap/san-tap/) | File mẫu để em tập sửa, commit |
| [bai-tap/danh-sach-lop.txt](bai-tap/danh-sach-lop.txt) | File chung cả lớp cùng điền (bài tập nhóm) |

Ngoài ra repo có sẵn vài **nhánh đặc biệt** để luyện merge và conflict (xem Nhiệm vụ 3 và 4):

```bash
git branch -a        # liệt kê cả các nhánh trên GitHub
```

| Nhánh | Dùng cho |
|-------|----------|
| `luyen-tap/them-mon-an` | Luyện merge đơn giản (Nhiệm vụ 3) |
| `luyen-tap/y-kien-to-1` | Luyện xử lý conflict (Nhiệm vụ 4) |
| `luyen-tap/y-kien-to-2` | Luyện xử lý conflict (Nhiệm vụ 4) |

---

## 🆘 Khi bí thì làm gì?

- Gõ `git status` để xem mình đang ở đâu, file nào đang chờ.
- Gõ `git log --oneline --graph --all` để nhìn sơ đồ các nhánh.
- Lỡ tay khi đang merge? Gõ `git merge --abort` để quay lại lúc đầu.
- Hỏi thầy/cô. 🙂

Chúc các em thực hành vui và nhớ lâu!
