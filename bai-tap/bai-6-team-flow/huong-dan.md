# Bài 6: Quy trình làm việc nhóm (Team workflow)

## Mục tiêu

- Hiểu quy trình chuẩn khi nhiều người cùng làm trên một repo
- Nắm vòng lặp: **pull → branch → code → commit → push → Pull Request → merge**
- Biết cách tránh và xử lý xung đột khi làm nhóm

> Đây là bài quan trọng nhất khi đi làm thật. Bài 1 đến 5 dạy lệnh, bài này dạy *cách phối hợp*.

---

## 1. Sơ đồ tổng quát

```
   GitHub (repo chung "origin")
   ┌──────────────────────────┐
   │         main             │  ← nhánh chính, luôn chạy được, KHÔNG code trực tiếp
   └──────────────────────────┘
        ▲                 │
        │ push + PR       │ pull / clone
        │                 ▼
   ┌──────────┐      ┌──────────┐
   │  Máy An   │      │  Máy Bình │   ← mỗi người làm trên nhánh riêng
   │ feature/A │      │ feature/B │
   └──────────┘      └──────────┘
```

**Nguyên tắc vàng:** không ai code trực tiếp lên `main`. Mỗi người tạo nhánh riêng cho từng tính năng, làm xong mới gộp về `main` qua Pull Request.

---

## 2. Vòng lặp một ngày làm việc

```bash
# 1. Đầu ngày: cập nhật main mới nhất
git switch main
git pull origin main

# 2. Tạo nhánh riêng cho việc mình làm
git switch -c feature/dang-nhap

# 3. Code... rồi lưu lại thành nhiều commit nhỏ
git add .
git commit -m "Them form dang nhap"
# ... code tiếp ...
git commit -m "Them kiem tra mat khau"

# 4. Đẩy nhánh của mình lên GitHub
git push -u origin feature/dang-nhap

# 5. Lên GitHub tạo Pull Request (PR) để xin gộp vào main
#    Đồng đội review, duyệt, rồi bấm Merge.

# 6. Sau khi PR được merge, cập nhật lại main ở máy
git switch main
git pull origin main
git branch -d feature/dang-nhap   # xóa nhánh đã xong
```

---

## 3. Pull Request (PR) là gì?

PR là một **đề nghị gộp code**: "Tôi đã làm xong nhánh này, xin gộp vào `main`". Trên GitHub, PR cho phép:

- Đồng đội **xem lại code** (code review) trước khi gộp.
- Thảo luận, góp ý ngay trên từng dòng.
- Chạy kiểm thử tự động (CI) trước khi merge.

PR giúp `main` luôn sạch và mọi người cùng kiểm soát chất lượng.

---

## 4. Khi nào dùng pull, push, merge?

| Lệnh | Khi nào dùng | Hướng dữ liệu |
|------|--------------|---------------|
| `git pull` | Lấy code mới nhất từ GitHub về máy | GitHub → Máy |
| `git push` | Đẩy code của mình lên GitHub | Máy → GitHub |
| `git merge` | Gộp một nhánh vào nhánh hiện tại (ở local) | Nhánh → Nhánh |

> `git pull` thực chất = `git fetch` (tải về) + `git merge` (gộp vào). Nên đôi khi `pull` cũng gây conflict.

---

## 5. Tình huống thường gặp khi làm nhóm

### Tình huống A: Push bị từ chối

```
! [rejected] main -> main (fetch first)
```

**Nguyên nhân:** có người đã push lên trước em, repo trên GitHub mới hơn ở máy.

**Cách xử lý:**

```bash
git pull origin main     # kéo thay đổi mới về (có thể phải giải conflict)
git push                 # rồi push lại
```

### Tình huống B: Nhánh của em đã cũ so với main

Trong lúc em làm, `main` đã có nhiều commit mới. Trước khi tạo PR, nên cập nhật nhánh:

```bash
git switch feature/cua-em
git merge main           # gộp main mới nhất vào nhánh của mình
# (giải conflict nếu có) rồi commit
```

### Tình huống C: Conflict khi merge PR

Xử lý y như Bài 4: mở file, xóa dấu `<<<<<<<` `=======` `>>>>>>>`, giữ nội dung đúng, `add` rồi `commit`.

---

## 6. Bài tập làm nhóm (2-3 người)

Giả lập một dự án nhỏ trên repo GitLearn này:

1. **Cả nhóm**: `git clone` repo về máy mỗi người.
2. **An**: tạo nhánh `feature/an`, thêm dòng tên mình vào `bai-tap/thanh-vien-nhom.txt`, commit, push, mở PR.
3. **Bình**: tạo nhánh `feature/binh`, cũng thêm tên mình vào *cùng file đó*, commit, push, mở PR.
4. Merge PR của An trước (vào main).
5. Bình `git pull origin main` rồi `git merge main` vào nhánh mình → **sẽ gặp conflict** → giải quyết.
6. Bình push lại và merge PR.

> Qua bài này nhóm sẽ thấy đầy đủ vòng đời: tách nhánh, làm song song, conflict, và gộp lại.

---

## 7. Quy ước đặt tên nhánh (theo chuẩn thực tế)

| Tiền tố | Dùng cho | Ví dụ |
|---------|----------|-------|
| `feature/` | Tính năng mới | `feature/gio-hang` |
| `fix/` hoặc `bugfix/` | Sửa lỗi | `fix/loi-dang-nhap` |
| `hotfix/` | Sửa lỗi gấp trên production | `hotfix/sap-server` |
| `docs/` | Sửa tài liệu | `docs/cap-nhat-readme` |

## Câu hỏi ôn tập

1. Vì sao không nên code trực tiếp trên `main`?
2. Pull Request dùng để làm gì?
3. Khi `git push` báo `rejected`, em làm gì tiếp theo?
4. `git pull` thực chất gồm hai lệnh nào?
