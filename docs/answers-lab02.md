**Lab 02 — Feature/topic flow và Pull Request**

**Vì sao đồng bộ master trước khi PR?**

Nhánh tính năng có thể dựa trên mã cũ. Merge `origin/master` đưa những
thay đổi mới vào nhánh để phát hiện xung đột và kiểm tra tích hợp trước
khi đề xuất merge. Trong bài, clone Dev 2 tạo nhánh tìm kiếm trước khi
PR in giỏ được merge; sau đó fetch và merge master, chạy lại chương
trình cho tổng `63.89 $` rồi mới gửi PR tìm kiếm.

**Khi nào không nên rebase?**

Không viết lại lịch sử chung của master/release hay commit mà người
khác đã dựa vào. Rebase thay SHA nên có thể làm các bản clone lệch nhau.
Rebase trên nhánh nháp chưa chia sẻ giúp sắp xếp thay đổi an toàn hơn.
Rebase and merge trên GitHub là cách tích hợp được chọn cho PR tài liệu,
khác với force push lại lịch sử master.

**feature khác topic ra sao?**

Feature phục vụ chức năng của chương trình, ví dụ in giỏ hoặc tìm kiếm.
Topic là nhánh cho một chủ đề khác như PR template hay tài liệu use
case. Cả hai đều được tạo từ master và tích hợp qua PR.

**Ba kiểu merge đã dùng**

- PR #4 dùng merge commit: giữ ba commit phát triển in giỏ và tạo một
  commit tích hợp có hai cha.
- PR #5 dùng squash: toàn bộ tính năng tìm kiếm có một commit tổng hợp
  trên master, dù nhánh trước đó đã đồng bộ bằng merge.
- PR tài liệu use case dùng rebase and merge để tạo lịch sử tuyến tính.

**Review và bảo vệ nhánh trong phương án solo**

Master yêu cầu PR, áp dụng cả admin, không cho force push hoặc xóa. Thử
đẩy một commit tài liệu mới thẳng vào master đã bị GH006 từ chối.
Repo sử dụng 0 approval như phương án solo trong slide. PR #4 ghi lại
việc tự phát hiện giỏ trống chưa có thông báo và commit bổ sung xử lý;
không có review Changes requested/Approved từ người thứ hai.

Dismiss stale approvals yêu cầu duyệt lại khi nội dung thay đổi sau
lần duyệt. Khi thực hành có partner, đây là cách giữ mã được tích hợp
phù hợp với đúng nội dung đã được reviewer chấp thuận.
