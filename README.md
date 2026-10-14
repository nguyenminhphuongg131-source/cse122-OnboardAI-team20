# BTL-20 – OnboardAI – Hành trình hội nhập nhân sự mới

> **Học phần:** PHÁT TRIỂN ỨNG DỤNG WEB CƠ BẢN – CSE122  
> **Nhóm thực hiện:** Nhóm 3 sinh viên (Nguyễn Minh Phương, Nguyễn Trịnh Hòa Hợp, Lê Minh Hiếu)  
> **Loại sản phẩm:** Sản phẩm Web Frontend nguyên mẫu (Mini-product) đa vai trò, CRUD có ý nghĩa, responsive, tương tác DOM và trải nghiệm AI phía Frontend.

---

## 🌟 1. Giới thiệu tổng quan

**OnboardAI** là nền tảng quản trị và hỗ trợ hành trình hội nhập 60 ngày thử việc của nhân sự mới tại doanh nghiệp công nghệ. Sản phẩm giải quyết triệt để 4 vấn đề thực tế:
- **P1. Checklist phân tán:** Tập trung toàn bộ nhiệm vụ 4 giai đoạn vào một giao diện trực quan, tương tác thời gian thực.
- **P2. Tài liệu khó tìm:** Số hóa sổ tay văn hóa, quy chuẩn bảo mật và tài liệu kỹ thuật thành Thư viện số có trích xuất ngữ nghĩa.
- **P3. HR khó theo dõi tiến độ:** Bảng điều khiển phân tích tỷ lệ hoàn thành theo phòng ban kết hợp cảnh báo rủi ro tự động.
- **P4. Câu hỏi lặp lại nhiều:** Trợ lý AI Co-Pilot trả lời chính sách có trích dẫn nguồn minh bạch và lưu vào sổ tay ghi nhớ.

---

## 🚀 2. Hướng dẫn chạy sản phẩm (Quick Start)

Dự án được xây dựng hoàn toàn bằng **HTML5 Semantic, CSS3 Modular và Vanilla JavaScript hiện đại**, sử dụng **LocalStorage** làm tầng dữ liệu tập trung. Sản phẩm hoạt động ngay lập tức mà không yêu cầu cài đặt máy chủ backend hay cơ sở dữ liệu phức tạp.

### Cách 1: Mở trực tiếp bằng Trình duyệt
- Click đúp vào tệp [`index.html`](file:///c:/Users/DELL/Desktop/LTWeb/index.html) để mở trang chủ trên trình duyệt (Chrome, Edge, Firefox, Safari).

### Cách 2: Chạy qua Live Server (Khuyến nghị để tối ưu trải nghiệm)
```bash
# Sử dụng Python (nếu có):
python -m http.server 8000

# Hoặc sử dụng Node.js (npx):
npx serve .

# Sau đó truy cập: http://localhost:8000
```

---

## 👥 3. Tài khoản thử nghiệm theo 4 Vai trò (1-Click Login)

Hệ thống hỗ trợ cơ chế **chuyển đổi vai trò tức thì** trên Sidebar và trang [`login.html`](file:///c:/Users/DELL/Desktop/LTWeb/login.html):

| Vai trò | Người dùng mẫu | Chức vụ | Phòng ban | Lối vào nhanh |
|---|---|---|---|---|
| **Nhân sự mới** | Trần Minh Anh | Frontend Developer | Công nghệ thông tin (IT) | [`newhire-onboarding-dashboard.html`](file:///c:/Users/DELL/Desktop/LTWeb/pages/newhire-onboarding-dashboard.html) |
| **Mentor** | Lê Hoàng Long | Lead Architect | Công nghệ thông tin (IT) | [`mentor-mentee-list.html`](file:///c:/Users/DELL/Desktop/LTWeb/pages/mentor-mentee-list.html) |
| **HR People Ops** | Nguyễn Thu Hà | People Operations Lead | Nhân sự & Đào tạo | [`hr-journey-management.html`](file:///c:/Users/DELL/Desktop/LTWeb/pages/hr-journey-management.html) |
| **Quản trị viên** | Bùi Quốc Cường | Head of Infrastructure | Quản trị hệ thống | [`admin-department-management.html`](file:///c:/Users/DELL/Desktop/LTWeb/pages/admin-department-management.html) |

---

## 📋 4. Bảng kiểm kê 12 Giao diện nền tảng bắt buộc

| # | Giao diện | Tệp HTML | Vai trò | CRUD | Tính năng AI | Người phụ trách |
|:---:|---|---|:---:|:---:|:---:|:---:|
| 1 | Onboarding Dashboard | `pages/newhire-onboarding-dashboard.html` | Nhân sự mới | R | Gợi ý tiến độ | Nguyễn Minh Phương |
| 2 | Checklist Hội nhập | `pages/newhire-checklist.html` | Nhân sự mới | C / R / U | - | Nguyễn Minh Phương |
| 3 | AI Help: Hỏi đáp Chính sách | `pages/newhire-ai-help.html` | Nhân sự mới | C / R / U / D | **AI-1: Policy Q&A** | Nguyễn Minh Phương |
| 4 | Mentee List & Cảnh báo | `pages/mentor-mentee-list.html` | Mentor | R | Cảnh báo trễ | Lê Minh Hiếu |
| 5 | Checkin Note 1-on-1 | `pages/mentor-checkin-note.html` | Mentor | C / R / U / D | - | Lê Minh Hiếu |
| 6 | Task Assignment | `pages/mentor-task-assignment.html` | Mentor | C / R / U / D | Đồng bộ phản hồi | Lê Minh Hiếu |
| 7 | Journey Management | `pages/hr-journey-management.html` | HR | C / R / U / D | **AI-2: Personalizer** | Nguyễn Trịnh Hòa Hợp |
| 8 | Document Library | `pages/hr-document-library.html` | HR | C / R / U / D | Tri thức RAG | Nguyễn Trịnh Hòa Hợp |
| 9 | HR Dashboard & Analytics | `pages/hr-dashboard.html` | HR | C / R / U / D | **AI-3: Progress Risk** | Nguyễn Trịnh Hòa Hợp |
| 10 | Department Management | `pages/admin-department-management.html` | Admin | C / R / U / D | - | Nguyễn Trịnh Hòa Hợp |
| 11 | User Management | `pages/admin-user-management.html` | Admin | C / R / U / D | Phân quyền RBAC | Nguyễn Trịnh Hòa Hợp |
| 12 | System Settings & AI SLA | `pages/admin-system-settings.html` | Admin | C / R / U / D | Cấu hình Engine | Nguyễn Trịnh Hòa Hợp |

### Các màn hình dùng chung:
- `index.html`: Cổng thông tin giới thiệu đồ án và điều phối vai trò.
- `login.html`: Trang đăng nhập và chuyển nhanh tài khoản.
- `403.html`: Màn hình cảnh báo từ chối quyền truy cập.
- `404.html`: Màn hình xử lý liên kết không tồn tại.

---

## 🤖 5. Hướng dẫn thử nghiệm 3 Tính năng AI

### AI-1: Policy Q&A with Citations (Nhân sự mới)
- Mở trang [`newhire-ai-help.html`](file:///c:/Users/DELL/Desktop/LTWeb/pages/newhire-ai-help.html).
- Bấm vào câu hỏi gợi ý nhanh (ví dụ: *"Thử việc có được nghỉ ốm hưởng lương không?"* hoặc *"Chuẩn Git flow"*).
- Quan sát:
  1. Trạng thái Loading có animation vòng tròn tím (Thinking state).
  2. Kết quả trả lời kèm trích dẫn văn bản số điều, tên tài liệu.
  3. Khối giải thích: *"Vì sao AI đưa ra kết quả này?"*.
  4. Các nút kiểm soát: Chấp nhận lưu vào Sổ tay, Chỉnh sửa câu trả lời, Hỏi lại hoặc Từ chối.
- **Thử nghiệm trạng thái thất bại (Failure mode):** Bấm nút *"🧪 Thử nghiệm AI Thất bại: BẬT"*, đặt câu hỏi bất kỳ để kiểm chứng trạng thái AI không chắc chắn và đề xuất liên hệ HR theo yêu cầu mục 11 & 12.

### AI-2: Checklist Personalizer (HR)
- Mở trang [`hr-journey-management.html`](file:///c:/Users/DELL/Desktop/LTWeb/pages/hr-journey-management.html).
- Bấm nút *"Tạo Lộ trình Bằng AI (AI-2)"*.
- Chọn cấp bậc: *Senior* hoặc *Intern*, chọn phòng ban.
- Quan sát AI sinh lộ trình 4 giai đoạn thích ứng, giải thích lý do vì sao Senior cần tập trung vào kiến trúc và release thay vì học lý thuyết.
- Bấm *"Chấp nhận & Lưu thành Lộ trình Mới"* để cập nhật vào cơ sở dữ liệu.

### AI-3: Progress Risk Detector (HR)
- Mở trang [`hr-dashboard.html`](file:///c:/Users/DELL/Desktop/LTWeb/pages/hr-dashboard.html).
- Bấm nút *"Kích hoạt AI Quét Rủi Ro Toàn Bộ"*.
- AI phát hiện 01 trường hợp nguy cơ cao (**Nguyễn Văn An** - 33% tiến độ sau 23 ngày, 14 ngày chưa check-in).
- Xem phân tích nguyên nhân gốc rễ (Root Cause) và bấm thử các nút hành động can thiệp 1 chạm (*Lên lịch 1-on-1 khẩn cấp*, *Bổ sung Buddy*).

---

## 📁 6. Cấu trúc Thư mục Dự án

```text
LTWeb/
├── index.html                           # Cổng thông tin chính & Ma trận giao diện
├── login.html                           # Trang đăng nhập đa vai trò
├── 403.html                             # Trang lỗi phân quyền
├── 404.html                             # Trang lỗi điều hướng
├── README.md                            # Tài liệu báo cáo chính
├── css/
│   ├── style.css                        # Design System tokens, typography, layout, widgets
│   └── responsive.css                   # Quy chuẩn responsive desktop/tablet/mobile
├── js/
│   ├── data.js                          # Cơ sở dữ liệu mẫu ban đầu (7 thực thể)
│   ├── storage.js                       # Quản trị LocalStorage CRUD & Reactive Event Bus
│   ├── ui.js                            # UI Controller (Render Sidebar, Topbar, Toast, Modal)
│   └── ai-engine.js                     # Mô phỏng 3 động cơ AI (AI-1, AI-2, AI-3)
├── pages/
│   ├── newhire-onboarding-dashboard.html # Màn hình 1
│   ├── newhire-checklist.html           # Màn hình 2
│   ├── newhire-ai-help.html             # Màn hình 3 (AI-1)
│   ├── mentor-mentee-list.html          # Màn hình 4
│   ├── mentor-checkin-note.html         # Màn hình 5
│   ├── mentor-task-assignment.html      # Màn hình 6
│   ├── hr-journey-management.html       # Màn hình 7 (AI-2)
│   ├── hr-document-library.html         # Màn hình 8
│   ├── hr-dashboard.html                # Màn hình 9 (AI-3)
│   ├── admin-department-management.html # Màn hình 10
│   ├── admin-user-management.html       # Màn hình 11
│   └── admin-system-settings.html       # Màn hình 12
└── docs/
    ├── project-proposal.md              # Đề cương đề tài BTL-20
    ├── screen-list.md                   # Bảng kiểm kê màn hình bắt buộc
    ├── roles-and-features.md            # Phân tích 4 vai trò & ma trận CRUD
    ├── team-assignment.md               # Phân công nhóm, Git Flow & chuẩn video OBS
    └── ai-usage-report.md               # Báo cáo khai báo sử dụng AI
```

---

## 🏆 7. Báo cáo Tuân thủ Chuẩn Đầu ra (CSE122)

- [x] **Độ đầy đủ của nghiệp vụ:** Triển khai toàn vẹn cả 12 màn hình theo mục 8 + 4 màn hình dùng chung.
- [x] **Thao tác CRUD có ý nghĩa:** Mọi thao tác thêm/sửa/xóa đều tác động thực tế đến thanh tiến độ, chỉ số rủi ro và các màn hình liên quan.
- [x] **Bao phủ trạng thái:** Đầy đủ trạng thái Bình thường, Đang tải, Rỗng, Thành công và Lỗi.
- [x] **Responsive:** Kiểm thử mượt mà trên Desktop, Tablet (1024px) và Mobile (768px, 480px).
- [x] **Mô phỏng AI có kiểm soát:** Tuân thủ quy trình 6 bước mục 12 và có kịch bản xử lý thất bại.
- [x] **Hồ sơ tài liệu chuẩn mực:** Đầy đủ 5 tài liệu trong thư mục `docs/`.

