🎨 2. Hệ Thống UI/UX Design System (Figma Specifications)
Để đảm bảo tính nhất quán (Consistency) của giao diện toàn hệ thống, lập trình viên cần tuân thủ nghiêm ngặt các thông số UI Kit sau:

🌟 Bảng Màu Chủ Đạo (Color Palette)
Màu chính (Primary Blue): #0288D1 (Dùng cho Sidebar, Tiêu đề lớn, Nút hành động chính).

Màu phụ (Success Green): #388E3C (Dùng cho nút "Lưu", trạng thái "Hoạt động", điểm đạt).

Màu cảnh báo (Danger Red): #D32F2F (Dùng cho nút "Xóa", trạng thái "Đã thôi học", cảnh báo lỗi số liệu).

Màu nền chính (Background): #F8F9FA (Nền xám nhạt chống mỏi mắt cho người dùng nhập liệu).

✍️ Quy Chuẩn Phông Chữ (Typography)
Font Family: Inter, Roboto hoặc Arial (Ưu tiên phông không chân để tối ưu hiển thị bảng dữ liệu).

Tiêu đề trang (Heading 1): 24px, Bold, Màu #212121.

Tiêu đề phân hệ (Heading 2): 18px, Semi-Bold, Màu #424242.

Văn bản/Dữ liệu bảng (Body/Table Text): 14px, Regular, Màu #212121.

🖥️ 3. Danh Sách Đặc Tả Chi Tiết Màn Hình (Screen Specifications)
Dưới đây là cấu trúc các file giao diện cần lập trình, ánh xạ trực tiếp từ các lớp Biên (Boundary) của mô hình phân tích BCE:

🔑 3.1. Phân Hệ Xác Thực (Screen_Login)
Tên File Code Gợi Ý: login_page.py hoặc Login.jsx

Thành Phần Giao Diện:

Hộp đăng nhập căn giữa màn hình (Card layout).

Trường nhập txtTenDangNhap (Icon người dùng).

Trường nhập txtMatKhau (Dạng ẩn ký tự, có nút toggle hiển thị).

Nút bấm btnDangNhap (Màu Primary Blue).

Luồng Xử Lý (Logic kết nối): Gọi hàm validate_login() từ AuthController để kiểm tra quyền hạn (Admin hoặc Giáo viên) trước khi chuyển hướng trang.

👥 3.2. Quản Lý Giáo Viên & Học Sinh (Screen_TeacherManagement & Screen_StudentManagement)
Tên File Code Gợi Ý: teacher_mgmt.py và student_mgmt.py

Thành Phần Giao Diện:

Thanh công cụ trên cùng (Top Bar): Ô tìm kiếm nhanh (Search Bar) + Dropdown bộ lọc (Lọc theo Môn học đối với GV, lọc theo Lớp/Khối đối với HS).

Nút hành động: Khởi tạo Button btnThemMoi (Kích hoạt Popup modal Form_AddTeacher / Form_AddStudent).

Bảng dữ liệu (Data Table): Hiển thị danh sách dạng lưới. Cột cuối cùng chứa các nút thao tác nhanh: Sửa (Icon bút chì), Vô hiệu hóa (Icon công tắc bật/tắt).

🏫 3.3. Thiết Lập Lớp Học & Phân Công (Screen_ClassManagement & Screen_Assignment)
Tên File Code Gợi Ý: class_config.py

Thành Phần Giao Diện:

Tab 1 - Tạo lớp: Form điền tên lớp, chọn khối (10, 11, 12), ban chuyên môn.

Tab 2 - Phân công chủ nhiệm: Giao diện cột đôi. Bên trái chọn Lớp Học, bên phải hiển thị danh sách Giáo Viên khả dụng qua một ô Dropdown Searchable.

Tab 3 - Phân công giảng dạy: Bảng ma trận lưới (Grid): Dòng là tên lớp, Cột là tên Môn học, Ô giao nhau là Dropdown chọn Giáo viên bộ môn.

📝 3.4. Nghiệp Vụ Nhập Điểm Môn Học (Screen_ScoreInput)
Tên File Code Gợi Ý: score_entry.py

Thành Phần Giao Diện:

Vùng lọc (Filter Zone): 3 Dropdown liên hoàn: Chọn Lớp -> Chọn Môn Học -> Chọn Học Kỳ. (Hệ thống tự khóa nếu Giáo viên đăng nhập không được phân công dạy lớp/môn này).

Lưới nhập liệu Excel-like (Data Editor):

Cột cố định: STT, Mã Học Sinh, Họ Tên.

Cột cho phép sửa trực tiếp: Điểm Miệng, Điểm 15 Phút, Điểm Giữa Kỳ, Điểm Cuối Kỳ.

Cột chỉ hiển thị (Read-only): Điểm Trung Bình Môn (TBM) - Tự động thay đổi realtime khi giáo viên gõ điểm thành phần.

Chân trang (Footer): Nút btnLuuBangDiem (Màu xanh lá) và nút btnHuyBo.

📊 3.5. Chuyên Cần, Hạnh Kiểm & Tổng Kết (Screen_Attendance & Screen_FinalSummary)
Tên File Code Gợi Ý: academic_summary.py

Thành Phần Giao Diện:

Giao diện điểm danh: Danh sách học sinh kèm 3 cột số nguyên (NghiCoPhep, NghiKhongPhep, DiMuon) có nút tăng giảm số (+/-).

Giao diện xếp loại: Dropdown chọn Hạnh kiểm (Tốt, Khá, Trung bình, Yếu) cho từng học sinh.

Bảng tổng kết: Nút btnXepHang để chạy thuật toán tính điểm TBHK và hiển thị thứ tự thi đua của học sinh trong lớp.


school-mgmt-system/
│
├── app/                        # Tầng Nghiệp vụ (App-Business Layer)
│   ├── controllers/            # Bộ điều phối (TeacherController, ScoreController,...)
│   └── services/               # Logic thuật toán xử lý dữ liệu sâu
│
├── database/                   # Tầng Dữ liệu (DB Layer)
│   ├── models.py               # Khai báo thực thể CSDL vật lý (ERD mapping)
│   └── connection.py           # Cấu hình kết nối SQLAlchemy / Database Engine
│
└── ui/                         # Tầng Giao Diện (UI Layer - ĐÂY LÀ NƠI BẠN CODE)
    ├── components/             # Các thành phần giao diện dùng chung (Sidebar, Navbar, Custom Table)
    ├── pages/                  # Các màn hình chức năng chính (Ánh xạ từ Boundary)
    │   ├── login.py
    │   ├── dashboard.py
    │   ├── teachers.py
    │   ├── students.py
    │   ├── classes.py
    │   └── scores.py
    └── app.py                  # File chạy chính điều hướng ứng dụng (Main Entry Point)
