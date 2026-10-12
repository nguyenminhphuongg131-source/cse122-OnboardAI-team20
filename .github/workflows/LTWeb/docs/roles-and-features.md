# PHÂN TÍCH VAI TRÒ, TÍNH NĂNG VÀ MA TRẬN CRUD
## Dự án: OnboardAI – Hành trình hội nhập nhân sự mới

---

### 1. Phân tích 4 Vai trò Người dùng

#### 1.1. Nhân sự mới (New Hire)
- **Chân dung:** Nhân viên mới gia nhập công ty (Thực tập sinh, Junior, Mid, Senior) đang trong giai đoạn thử việc 60 ngày.
- **Trách nhiệm chính:** Theo dõi hành trình hội nhập, tiếp cận tài liệu số, hoàn thành checklist và chủ động giải quyết vướng mắc.
- **Các màn hình phụ trách:**
  1. `newhire-onboarding-dashboard.html`: Tổng quan chỉ số, thanh tiến độ 60 ngày, nhiệm vụ sắp tới, thẻ liên hệ Mentor, đăng ký lịch check-in 1-on-1.
  2. `newhire-checklist.html`: Lộ trình 4 giai đoạn (Ngày 1, Tuần 1, Tháng 1, Tháng 2), lọc theo trạng thái/chuyên mục, đánh dấu hoàn thành, viết ghi chú PR cá nhân, tự tạo nhiệm vụ bổ sung (C/R/U).
  3. `newhire-ai-help.html`: Khung hỏi đáp chính sách (AI-1), xem trích dẫn văn bản, lưu vào sổ tay ghi nhớ cá nhân (C/R/U/D), kiểm thử lỗi không chắc chắn.

#### 1.2. Cố vấn / Quản lý trực tiếp (Mentor / Direct Manager)
- **Chân dung:** Kỹ sư trưởng (Lead Engineer) hoặc Trưởng nhóm chuyên môn chịu trách nhiệm bảo trợ cho mentee.
- **Trách nhiệm chính:** Theo dõi sát sao tiến độ học tập, tháo gỡ rào cản kỹ thuật và ghi nhận phản hồi định kỳ.
- **Các màn hình phụ trách:**
  4. `mentor-mentee-list.html`: Danh sách nhân sự phụ trách, tỷ lệ % hoàn thành, trạng thái cảnh báo nguy cơ chậm (Normal, Warning, Critical), xem chi tiết hồ sơ.
  5. `mentor-checkin-note.html`: Quản lý nhật ký các buổi gặp 1-on-1, chấm điểm tinh thần 1-5 sao, ghi nhận khó khăn và thống nhất các Action Items (C/R/U/D).
  6. `mentor-task-assignment.html`: Phân công nhiệm vụ chuyên môn cụ thể, đặt hạn chót, gán độ ưu tiên và viết nhận xét nghiệm thu (DoD) (C/R/U/D).

#### 1.3. Chuyên viên Nhân sự (HR People Operations)
- **Chân dung:** Chuyên viên phụ trách trải nghiệm nhân viên và quản lý quy trình thử việc toàn diện.
- **Trách nhiệm chính:** Thiết kế khuôn mẫu hành trình chuẩn, quản lý kho chính sách và giám sát sức khỏe onboarding toàn công ty.
- **Các màn hình phụ trách:**
  7. `hr-journey-management.html`: Quản lý danh mục lộ trình chuẩn theo phòng ban, sử dụng AI Checklist Personalizer (AI-2) để tự động sinh lộ trình thích ứng theo vị trí và cấp bậc (C/R/U/D).
  8. `hr-document-library.html`: Quản lý kho văn bản số (Sổ tay văn hóa, Quy chế bảo mật, Git flow, Quy trình thử việc), đọc nội dung, tìm kiếm đa tiêu chí, tải xuống (C/R/U/D).
  9. `hr-dashboard.html`: Bảng phân tích tỷ lệ hoàn thành theo khối phòng ban, kích hoạt AI Progress Risk Detector (AI-3) để quét và đề xuất giải pháp can thiệp khẩn cấp (C/R/U/D).

#### 1.4. Quản trị viên Hệ thống (System Admin)
- **Chân dung:** Quản trị viên phụ trách vận hành nền tảng nội bộ và cấu hình chính sách hệ thống.
- **Trách nhiệm chính:** Quản lý cơ cấu phòng ban, định danh tài khoản, phân quyền truy cập và kiểm soát tham số SLA.
- **Các màn hình phụ trách:**
  10. `admin-department-management.html`: Quản trị cơ cấu phòng ban, mã đơn vị, chỉ định trưởng bộ phận và quy mô nhân sự (C/R/U/D).
  11. `admin-user-management.html`: Quản trị danh mục tài khoản, gán quyền RBAC, ghép cặp Mentor - Mentee, tính năng đăng nhập thử 1 chạm (C/R/U/D).
  12. `admin-system-settings.html`: Thiết lập thời hạn thử việc chuẩn (60 ngày), chu kỳ cảnh báo check-in (7 ngày), ngưỡng rủi ro checklist (50%), cấu hình AI Engine và sao lưu dữ liệu JSON (C/R/U/D).

---

### 2. Ma trận Thực thể & Phép toán Nghiệp vụ CRUD

| Thực thể | Mô tả thuộc tính | Tạo (Create) | Đọc (Read) | Sửa (Update) | Xóa/Hủy (Delete/Archive) | Đồng bộ liên kết |
|---|---|:---:|:---:|:---:|:---:|---|
| `users` | id, name, email, role, dept, position, avatar, status | ✓ | ✓ | ✓ | ✓ (Archive) | Định danh toàn hệ thống |
| `newHires` | id, name, role, dept, mentorId, startDate, progress, riskStatus | ✓ | ✓ | ✓ | ✓ (Archive) | Tự động sinh khi tạo user mới |
| `tasks` | id, newHireId, title, desc, phase, priority, status, note, feedback | ✓ | ✓ | ✓ | ✓ | Tự động tính lại % tiến độ của newHire |
| `checkins` | id, mentorId, newHireId, date, moraleRating, challenges, actions | ✓ | ✓ | ✓ | ✓ | Tự động cập nhật `lastCheckinDate` |
| `documents` | id, title, category, summary, content, tags, downloads, format | ✓ | ✓ | ✓ | ✓ | Cung cấp tri thức cho AI-1 tra cứu |
| `journeys` | id, name, department, targetRole, phasesCount, tasksCount, desc | ✓ | ✓ | ✓ | ✓ | Lưu trữ khuôn mẫu từ AI-2 |
| `departments` | id, name, code, headName, memberCount, activeOnboardingCount | ✓ | ✓ | ✓ | ✓ | Liên kết phân nhóm người dùng |

---

### 3. Phân tích 3 Trải nghiệm AI Cốt lõi

#### 3.1. AI-1: Policy Q&A with Citations (Hỏi đáp Chính sách có Trích dẫn)
- **Mục tiêu:** Giúp nhân sự mới tự giải đáp thắc mắc về nội quy, giờ làm việc linh hoạt, bảo hiểm VIP, nghỉ ốm thử việc và quy chuẩn Git flow mà không làm phiền đồng nghiệp.
- **Chu trình trải nghiệm:**
  1. *Người dùng nhập:* Câu hỏi tự nhiên (ví dụ: *"Thử việc có được nghỉ ốm hưởng lương không?"*).
  2. *Kiểm tra hợp lệ:* Ngăn chặn để trống, yêu cầu tối thiểu 3 ký tự.
  3. *AI đang xử lý:* Hiệu ứng pulse vòng tròn tím, thanh loader đang suy luận mô phỏng tra cứu RAG trong 800ms.
  4. *Kết quả AI:* Trả lời súc tích, định dạng markdown rõ ràng.
  5. *Trích dẫn minh bạch:* Hiển thị hộp trích dẫn văn bản: Tên tài liệu, Điều khoản số mấy, kèm nút mở tài liệu gốc.
  6. *Giải thích:* Khối *"Vì sao có kết quả này?"* giải thích cơ chế so khớp ngữ nghĩa.
  7. *Kiểm soát của người dùng:* Chấp nhận & Lưu vào Sổ tay cá nhân, Chỉnh sửa nội dung trước khi lưu, Hỏi lại câu khác, Từ chối kết quả.
  8. *Trải nghiệm khi AI thất bại:* Chế độ mô phỏng khi tài liệu không đủ dữ liệu (Độ tin cậy <30%), hiển thị cảnh báo, các gợi ý thay thế, nút thử lại và liên hệ HR.

#### 3.2. AI-2: Checklist Personalizer (Cá nhân hóa Lộ trình theo Vai trò)
- **Mục tiêu:** Giúp HR không phải soạn thảo thủ công hàng chục danh sách checklist cho từng vị trí kỹ thuật hoặc kinh doanh.
- **Chu trình trải nghiệm:**
  1. *Người dùng nhập:* Chọn Phòng ban, Cấp bậc (Intern, Junior, Senior) và Chức danh công việc.
  2. *AI đang xử lý:* Phân tích bộ kỹ năng cần thiết cho cấp bậc tương ứng.
  3. *Kết quả AI:* Sinh ra 4 giai đoạn nhiệm vụ có độ ưu tiên và thời lượng đo lường.
  4. *Giải thích:* Nêu rõ lý do (ví dụ: Cấp bậc Senior được miễn trừ việc học lý thuyết, tập trung vào audit kiến trúc và release sớm).
  5. *Kiểm soát:* HR duyệt Chấp nhận để lưu thành khuôn mẫu Lộ trình mới của công ty, hoặc Thử lại (Regenerate).

#### 3.3. AI-3: Progress Risk Detector (Dự báo Rủi ro Chậm Tiến độ)
- **Mục tiêu:** Giúp HR và Quản lý phát hiện sớm các dấu hiệu nhân viên mới bị ngợp, chậm deadline hoặc thiếu kết nối với Mentor để can thiệp kịp thời.
- **Chu trình trải nghiệm:**
  1. *Kích hoạt:* Tự động phân tích khi tải Dashboard hoặc bấm nút *"Kích hoạt AI Quét Rủi Ro"*.
  2. *Thuật toán đánh giá:* So sánh ma trận: Tỷ lệ hoàn thành % thực tế vs Số ngày thử việc đã qua vs Khoảng cách từ buổi check-in 1-on-1 gần nhất vs Đánh giá tinh thần (morale score).
  3. *Kết quả:* Phân loại nhân sự thành: Normal (Bình thường), Warning (Hơi chậm), Critical (Nguy cơ cao kèm điểm rủi ro /100).
  4. *Giải thích căn nguyên (Root Cause):* Phân tích điểm nghẽn cụ thể (ví dụ: 14 ngày chưa có 1-on-1, vướng mắc Docker chưa giải quyết).
  5. *Đề xuất can thiệp (Actionable recommendations):* Đưa ra các nút hành động 1 chạm: *Lên lịch 1-on-1 khẩn cấp*, *Bổ sung Buddy hỗ trợ*, *Gia hạn mốc đánh giá sprint thêm 7 ngày*.

