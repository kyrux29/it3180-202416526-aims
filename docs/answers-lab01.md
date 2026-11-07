**Lab 01 — Thiết lập môi trường và refactor**

Sinh viên: Vũ Trọng Quốc Khánh — MSSV: 202416526.

**Cấu hình global khác local thế nào?**

Cấu hình global thường được lưu trong `~/.gitconfig`, áp dụng cho các kho
của người dùng hiện tại. Cấu hình local nằm trong `.git/config` của từng
kho và ghi đè giá trị global cùng tên. Trong bài này, tên tác giả được đặt
ở local để việc thực hành không đổi tên tác giả của các dự án khác.

**Vì sao dùng git mv khi refactor?**

Lệnh này di chuyển tệp và stage thay đổi trong một thao tác. Git nhận diện
rename dựa trên độ giống nội dung; nó không lưu một bản ghi rename riêng
biệt. Khi chuyển `cart.py` sang `aims/cart.py` và giữ nguyên nội dung,
`git diff --cached --summary` nhận diện rename 100%. Có thể lần theo lịch
sử bằng `git log --oneline --follow -- aims/cart.py`.

**release/lab01 có phải baseline không?**

Nhánh này là baseline bài nộp khi được tạo từ trạng thái đã kiểm tra và
chấp nhận. Các cập nhật tiếp theo phải đi qua quy trình sửa bài và PR,
thay vì chỉnh trực tiếp. Một tag gắn vào commit giúp định danh một trạng
thái cố định; nhánh release có thể nhận bản vá có kiểm soát.

**Vì sao vẫn cần PR khi làm một mình?**

PR ghi lại mục đích, diff và kết quả kiểm tra của mỗi thay đổi. Việc đọc
diff trước khi tích hợp giúp phát hiện tệp ngoài phạm vi và giữ lịch sử
dễ xem lại. Với một tài khoản, bài dùng 0 approval theo phương án solo
trong slide; tác giả không thể tự approve PR của chính mình.

**Đã kiểm tra gì ở local?**

- Chạy chương trình trước và sau refactor, tổng đều là `63.89 $`.
- `__pycache__/` được tạo khi chạy Python nhưng bị `.gitignore` loại bỏ.
- Thử sửa comment trong `cart.py`, xem diff rồi dùng `git restore` để bỏ.
- Thử stage comment trong `main.py`, dùng `git restore --staged`; nội
  dung vẫn còn trong working directory trước khi phục hồi tệp.
- Thực hành sửa message của commit tài liệu chưa push bằng `--amend`.
