# ĐỀ CƯƠNG DỰ ÁN BTL-20: ONBOARDAI – HÀNH TRÌNH HỘI NHẬP NHÂN SỰ MỚI
## Học phần: Phát triển Ứng dụng Web Cơ bản – CSE122

---

### 1. Lĩnh vực đề tài
**Nhân sự / HRTech (Human Resource Technology)**

### 2. Tóm tắt sản phẩm
**OnboardAI – Hành trình hội nhập nhân sự mới** là một sản phẩm Web Frontend hoàn chỉnh được thiết kế như một mini-product đa vai trò, bao phủ toàn diện chu trình 60 ngày thử việc của nhân viên mới tại doanh nghiệp công nghệ. Sản phẩm giải quyết bài toán giao tiếp, phân công nhiệm vụ và theo dõi tiến độ giữa 4 bên: **Nhân sự mới**, **Người hướng dẫn (Mentor)**, **Chuyên viên nhân sự (HR)** và **Quản trị viên (Admin)**.

Hệ thống tích hợp 3 mô-đun AI mô phỏng ở tầng Frontend (Policy Q&A, Checklist Personalizer, Progress Risk Detector) giúp tự động hóa khâu giải đáp thắc mắc, cá nhân hóa lộ trình và phát hiện nguy cơ chậm tiến độ từ sớm.

### 3. Ngữ cảnh bài toán thực tế
Tại các doanh nghiệp vừa và lớn, quá trình tiếp nhận nhân sự mới (Employee Onboarding) thường kéo dài từ 30 đến 60 ngày và liên quan đến nhiều phòng ban (Nhân sự, IT, Hành chính, Chuyên môn). Hiện trạng phổ biến là quy trình bị phân mảnh qua hàng chục luồng email rời rạc, các tài liệu PDF/Word nằm rải rác trên Google Drive và các bảng tính Excel theo dõi thủ công. Hậu quả là nhân viên mới thường rơi vào trạng thái bối rối, không biết việc tiếp theo phải làm gì; trong khi người quản lý và HR không nắm được bức tranh tổng thể để hỗ trợ kịp thời.

### 4. Phát biểu vấn đề (Problem Statements)
- **P1. Checklist phân tán:** Danh sách việc cần làm bị chia nhỏ ở nhiều nơi (email chào mừng, tin nhắn Slack, tài liệu in), thiếu một nơi tập trung để nhân sự mới theo dõi và đánh dấu hoàn thành.
- **P2. Tài liệu khó tìm:** Sổ tay nhân viên, quy chế bảo mật thông tin, cẩm nang kỹ thuật và quy định nghỉ phép nằm ở các thư mục khác nhau, khiến việc tra cứu mất nhiều thời gian.
- **P3. HR khó theo dõi tiến độ:** Bộ phận Nhân sự không có số liệu định lượng về việc nhân viên mới đã hòa nhập đến đâu, ai đang gặp bế tắc kỹ thuật, dẫn đến việc chỉ phát hiện nhân sự không đạt yêu cầu vào sát ngày kết thúc thử việc.
- **P4. Câu hỏi lặp lại nhiều:** Các câu hỏi phổ biến về giờ giấc làm việc, chế độ bảo hiểm, quy định làm việc từ xa (WFH) lặp đi lặp lại hàng tuần, làm tiêu tốn thời gian trả lời của HR và Mentor.

### 5. Mục tiêu dự án (Objectives)
- **O1.** Chuyển hóa bài toán thực tế thành một sản phẩm Web Frontend có hành trình người dùng xuyên suốt, thân thiện và mạch lạc.
- **O2.** Thiết kế đầy đủ 12 giao diện nền tảng cho 4 vai trò (tối thiểu 3 màn hình/vai trò) cùng các màn hình dùng chung.
- **O3.** Thể hiện các thao tác CRUD và trạng thái nghiệp vụ có ý nghĩa thay vì CRUD hình thức.
- **O4.** Khai thác triệt để JavaScript/DOM cho tìm kiếm, lọc dữ liệu thời gian thực, kiểm tra hợp lệ biểu mẫu, cửa sổ modal, thanh tiến độ và kết xuất dữ liệu phản ứng.
- **O5.** Xây dựng tầng lưu trữ dữ liệu tập trung qua LocalStorage và cơ chế Reactive Event Bus mô phỏng đồng bộ dữ liệu thời gian thực.
- **O6.** Hiện thực hóa 3 trải nghiệm AI mô phỏng phía Frontend tuân thủ nghiêm ngặt chu trình: Nhập liệu → Kiểm tra hợp lệ → Đang xử lý → Kết quả → Giải thích → Quyền kiểm soát của người dùng.
- **O7.** Chuẩn hóa quy trình làm việc nhóm theo mô hình Git Flow (main, dev, feature/*), gắn kết mã công việc Trello và minh chứng video OBS.

