# Đáp án câu hỏi ôn tập (dành cho giáo viên)

## Bài 1: Lệnh cơ bản

1. **`git add` vs `git commit`**: `git add` đưa thay đổi vào vùng chờ (staging), `git commit` lưu vĩnh viễn các thay đổi đã add vào lịch sử repo. Nói cách khác: `add` là chọn, `commit` là chốt.
2. Lệnh **`git status`** cho biết file nào đang chờ commit.
3. Commit message rõ ràng giúp người khác (và chính em sau này) hiểu mỗi commit làm gì, dễ tìm lại và dễ quay về phiên bản cần thiết.

## Bài 2: Nhánh

1. Dùng nhánh an toàn hơn vì thử nghiệm không ảnh hưởng tới `main`. Nếu hỏng, chỉ cần xóa nhánh, `main` vẫn nguyên vẹn.
2. `git switch -c ten-nhanh` **tạo mới rồi chuyển** sang nhánh đó; `git switch ten-nhanh` chỉ **chuyển** sang nhánh đã tồn tại.
3. Vì mỗi nhánh trỏ tới một commit khác nhau. Khi chuyển nhánh, Git khôi phục lại trạng thái file đúng theo commit của nhánh đó.

## Bài 3: Merge

1. **Fast-forward** khi nhánh đích (`main`) không có commit mới kể từ lúc tách. **Merge commit** khi cả hai nhánh đều có commit mới.
2. Phải đứng ở **nhánh đích** (nhánh muốn nhận thay đổi), thường là `main`, rồi mới `git merge nhanh-nguon`.
3. Nên xóa nhánh tính năng sau khi merge để repo gọn gàng, tránh rối khi có nhiều nhánh cũ không dùng.

## Bài 4: Xung đột

1. Conflict xảy ra khi hai nhánh sửa **cùng một dòng** trong **cùng một file**.
2. `<<<<<<< HEAD` mở đầu phần của nhánh hiện tại; `=======` ngăn cách; `>>>>>>>` kết thúc phần của nhánh được merge.
3. Sau khi sửa: chạy **`git add <file>`** rồi **`git commit`**.

## Bài 5: Remote

1. `origin` là tên gọi (alias) cho địa chỉ URL của repo trên GitHub.
2. `git pull` trước để có code mới nhất, tránh làm trùng/xung đột với thay đổi của người khác.
3. `git clone` tải **toàn bộ repo lần đầu** (kèm lịch sử và thiết lập remote); `git pull` chỉ **cập nhật thay đổi mới** vào repo đã có sẵn.
4. Các lần sau chỉ cần **`git push`** (vì `-u` ở lần đầu đã ghi nhớ nhánh upstream).
