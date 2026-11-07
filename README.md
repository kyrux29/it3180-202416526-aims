# AIMS-mini

Bài thực hành quản lý cấu hình phần mềm với Git và GitHub, học phần IT3180.

- Sinh viên: Vũ Trọng Quốc Khánh
- MSSV: 202416526
- GitHub: [kyrux29](https://github.com/kyrux29)

Ứng dụng dòng lệnh quản lý giỏ hàng DVD, dùng thư viện chuẩn Python.

Yêu cầu Python từ 3.10. Chạy chương trình từ thư mục gốc của repo:

```bash
python3 main.py
```

Tổng tiền của dữ liệu mẫu: `63.89 $`.

Các tệp cache Python (`__pycache__/`, `*.pyc`) được loại khỏi Git bằng
`.gitignore`; không cần cài thêm thư viện để chạy chương trình mẫu.

Run the unit tests from the repository root:

```bash
python3 -m unittest discover -s tests -v
```

Source files are in `aims/`, tests in `tests/`, and discussion answers
and command evidence in `docs/`. Each lab is submitted through its
`release/labXX` branch. Development changes go through a pull request
to `master`; fixes for a submitted version start from its release line.
