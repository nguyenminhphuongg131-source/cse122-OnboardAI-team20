# BẢNG KIỂM KÊ MÀN HÌNH BẮT BUỘC (SCREEN INVENTORY)
## Dự án: OnboardAI – Hành trình hội nhập nhân sự mới (BTL-20 – CSE122)

> **Nhóm thực hiện:** Nhóm 3 sinh viên (SV1, SV2, SV3)  
> **Học phần:** Phát triển Ứng dụng Web Cơ bản – CSE122  
> **Nguyên tắc:** Độ đầy đủ của nghiệp vụ > Số lượng giao diện. Đảm bảo toàn bộ 12 màn hình nền tảng và các màn hình dùng chung đều có bao phủ trạng thái và lát cắt dọc.

---

### 1. Bảng kiểm kê chi tiết theo vai trò

| # | Vai trò | Mục tiêu người dùng | Nhiệm vụ người dùng | Tên màn hình | Tệp HTML tương ứng | CRUD / Nghiệp vụ | Tính năng AI | Người phụ trách |
|---|---|---|---|---|---|---|---|---|
| 1 | **Nhân sự mới** | Nắm bắt tổng quan tiến độ 60 ngày thử việc và việc cần làm | Xem tiến độ, nhiệm vụ sắp tới, thông tin Mentor, đăng ký 1-on-1 | Onboarding Dashboard | `pages/newhire-onboarding-dashboard.html` | **R** (Đọc, Xem tiến độ, Booking) | AI Co-Pilot Tip cá nhân hóa | **SV1** |
| 2 | **Nhân sự mới** | Thực hiện và quản lý lộ trình nhiệm vụ theo từng giai đoạn | Tích chọn hoàn thành, lọc trạng thái, ghi chú PR, thêm việc cá nhân | Checklist Hội nhập | `pages/newhire-checklist.html` | **C / R / U** (Tạo task cá nhân, Đọc, Sửa note/tick) | - | **SV1** |
| 3 | **Nhân sự mới** | Giải đáp thắc mắc về nội quy, chế độ, bảo mật, quy chuẩn kỹ thuật | Đặt câu hỏi tự nhiên, xem trích nguồn, lưu câu trả lời vào sổ tay | AI Help: Hỏi đáp Chính sách | `pages/newhire-ai-help.html` | **C / R / U / D** (Hỏi, Xem, Lưu vào Sổ tay, Xóa note) | **AI-1: Policy Q&A with Citations** | **SV1** |
| 4 | **Mentor** | Giám sát danh sách mentee phụ trách và phát hiện rủi ro | Tra cứu mentee, lọc theo phòng ban, theo dõi cảnh báo tiến độ | Mentee List & Cảnh báo | `pages/mentor-mentee-list.html` | **R** (Tra cứu, Lọc, Xem hồ sơ) | - | **SV2** |
| 5 | **Mentor** | Ghi nhận nội dung và thống nhất hành động sau buổi gặp 1-on-1 | Lập biên bản check-in, chấm điểm tinh thần, theo dõi khó khăn | Sổ tay Check-in 1-on-1 | `pages/mentor-checkin-note.html` | **C / R / U / D** (Thêm biên bản, Đọc lịch sử, Sửa, Xóa) | - | **SV2** |
| 6 | **Mentor** | Giao việc chuyên môn và gửi nhận xét nghiệm thu cho mentee | Tạo nhiệm vụ mới, phân công hạn chót, sửa yêu cầu, gửi feedback | Phân công Nhiệm vụ | `pages/mentor-task-assignment.html` | **C / R / U / D** (Giao việc, Đọc, Sửa, Xóa/Hủy) | - | **SV2** |
| 7 | **HR** | Xây dựng và chuẩn hóa các khuôn mẫu hành trình hội nhập | Thiết lập lộ trình theo phòng ban, sử dụng AI sinh checklist theo vị trí | Thiết kế Lộ trình (Journeys) | `pages/hr-journey-management.html` | **C / R / U / D** (Tạo template, Đọc, Sửa, Lưu trữ) | **AI-2: Checklist Personalizer** | **SV3** |
| 8 | **HR** | Quản lý kho chính sách, quy chế và cẩm nang số nội bộ | Tải lên tài liệu, gắn thẻ tags, xem trước nội dung, đếm lượt tải | Thư viện Tài liệu & Sổ tay | `pages/hr-document-library.html` | **C / R / U / D** (Upload doc, Đọc, Sửa, Xóa) | Trích xuất ngữ nghĩa RAG | **SV3** |
| 9 | **HR** | Phân tích toàn cảnh tiến độ công ty và ngăn ngừa tỷ lệ fail thử việc | Xem biểu đồ phòng ban, chạy AI quét rủi ro trễ hạn, can thiệp khẩn cấp | HR Dashboard & Risk Detector | `pages/hr-dashboard.html` | **C / R / U / D** (Phân tích, Can thiệp, Khen thưởng) | **AI-3: Progress Risk Detector** | **SV3** |
| 10 | **Quản trị viên** | Quản lý cơ cấu phòng ban và đầu mối phụ trách | Thêm phòng ban, chỉ định trưởng bộ phận, kiểm soát quy mô nhân sự | Quản lý Phòng ban | `pages/admin-department-management.html` | **C / R / U / D** (Thêm dept, Đọc, Sửa, Vô hiệu hóa) | - | **SV3** |
| 11 | **Quản trị viên** | Kiểm soát tài khoản truy cập, phân quyền và ghép cặp hướng dẫn | Tạo tài khoản, gán role (RBAC), kích hoạt/khóa, đăng nhập thử | Quản lý Tài khoản & Phân quyền | `pages/admin-user-management.html` | **C / R / U / D** (Tạo user, Đọc, Sửa, Khóa/Xóa) | - | **SV3** |
| 12 | **Quản trị viên** | Cấu hình tham số hệ thống, SLA cảnh báo và mô hình AI | Đặt thời hạn thử việc (60 ngày), ngưỡng cảnh báo, chỉnh prompt/temp AI | Cấu hình Hệ thống & AI SLA | `pages/admin-system-settings.html` | **C / R / U / D** (Cập nhật config, Reset DB, Xuất JSON) | Cấu hình tham số AI Engine | **SV3** |

---

### 2. Các màn hình dùng chung (Common Screens)

| # | Tệp | Chức năng | Nghiệp vụ |
|---|---|---|---|
| 13 | `index.html` | Cổng thông tin giới thiệu BTL-20, ma trận màn hình, lối vào nhanh 4 vai trò | Điều phối, Giới thiệu sản phẩm |
| 14 | `login.html` | Xác thực người dùng, 1-click test login chuyển đổi nhanh 4 vai trò | Đăng nhập hệ thống |
| 15 | `403.html` | Báo lỗi không có đặc quyền truy cập vai trò tương ứng | Xử lý lỗi bảo mật |
| 16 | `404.html` | Báo lỗi đường dẫn trang không tồn tại | Xử lý điều hướng |

---

### 3. Bao phủ trạng thái bắt buộc (State Coverage)
Tất cả các chức năng quan trọng đều được kiểm thử và bảo đảm hiển thị các trạng thái:
- **Bình thường (Normal):** Kết xuất đầy đủ bảng/danh sách từ LocalStorage.
- **Đang tải (Loading):** Thanh progress loader, hiệu ứng pulse vòng tròn khi AI suy luận.
- **Rỗng (Empty State):** Minh họa SVG kèm thông báo và nút hành động khi bộ lọc không có dữ liệu.
- **Thành công (Success):** Toast notification xanh lá nổi góc dưới kèm thông điệp rõ ràng.
- **Lỗi & Không chắc chắn (Failure/Uncertainty):** Chế độ kiểm thử AI thất bại (mục 11 & 12), cảnh báo validation biểu mẫu.

