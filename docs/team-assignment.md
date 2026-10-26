# KẾ HOẠCH PHÂN CÔNG NHÓM & QUY TRÌNH PHÁT TRIỂN
## Dự án: OnboardAI – BTL-20 CSE122 (Nhóm 3 Sinh viên)

---

### 1. Phân công Vai trò & Lát cắt dọc (Vertical Slice)

Theo quy định mục 14 của đề tài: *Mỗi sinh viên phải tự hoàn thành ít nhất một luồng end-to-end (Bản mô phỏng → HTML semantic → CSS → JavaScript DOM → Dữ liệu → Responsive → Nhánh Git → Commit chuẩn → Pull Request → Video OBS)*. Tuyệt đối không chấp nhận cách làm một người chỉ vẽ Figma, một người chỉ viết HTML.

| Sinh viên | Vai trò nghiệp vụ chính | Màn hình phụ trách | Trách nhiệm chéo toàn dự án | Luồng lát cắt dọc End-to-End |
|---|---|---|---|---|
| **Nguyễn Minh Phương** | **Nhân sự mới** (New Hire) | 1. `newhire-onboarding-dashboard.html`<br>2. `newhire-checklist.html`<br>3. `newhire-ai-help.html` | Hệ thống thiết kế Design Tokens, Typography, Khả năng tiếp cận (Accessibility), Tương thích Di động (Responsive) | Luồng Nhân sự mới: Xem dashboard → Tích hoàn thành checklist → Nhập câu hỏi AI chính sách → Nhận trích nguồn → Lưu sổ tay |
| **Lê Minh Hiếu** | **Mentor / Quản lý** (Mentor) | 4. `mentor-mentee-list.html`<br>5. `mentor-checkin-note.html`<br>6. `mentor-task-assignment.html` | Kiến trúc Tầng dữ liệu LocalStorage, Quản lý trạng thái tập trung (StorageManager), Đồng bộ sự kiện phản ứng (Reactive Event Bus) | Luồng Mentor: Kiểm tra danh sách mentee → Mở biên bản ghi nhận 1-on-1 → Tạo và giao nhiệm vụ mới → Theo dõi tiến độ |
| **Nguyễn Trịnh Hòa Hợp** | **HR & Quản trị viên** (HR & Admin) | 7. `hr-journey-management.html`<br>8. `hr-document-library.html`<br>9. `hr-dashboard.html`<br>10. `admin-department-management.html`<br>11. `admin-user-management.html`<br>12. `admin-system-settings.html` | Kiến trúc Điều hướng chung (UI Controller), 3 Mô-đun AI mô phỏng (AIEngine), Tích hợp Layout, Quản trị phát hành (Release QA) | Luồng HR/Admin: Thiết kế template lộ trình với AI-2 → Đăng tải tài liệu chính sách → Chạy quét AI-3 cảnh báo rủi ro → Quản lý tài khoản |

---

### 2. Chiến lược Nhánh Git (Git Flow)

Kho mã nguồn: `cse122-onboardai-team20`

```text
main (Nhánh phát hành ổn định)
 │
 └── dev (Nhánh tích hợp liên tục)
      ├── feature/newhire-onboarding-dashboard (SV1)
      ├── feature/newhire-checklist (SV1)
      ├── feature/newhire-ai-help (SV1)
      ├── feature/mentor-mentee-list (SV2)
      ├── feature/mentor-checkin-note (SV2)
      ├── feature/mentor-task-assignment (SV2)
      ├── feature/hr-journey-management (SV3)
      ├── feature/hr-document-library (SV3)
      ├── feature/hr-dashboard (SV3)
      ├── feature/admin-system-settings (SV3)
      └── fix/<bug-name>
```

#### Quy trình chuẩn từ Task đến Merge:
1. Nhận mã công việc trên bảng Trello (ví dụ: `TASK-02`).
2. Tạo nhánh từ `dev`: `git checkout -b feature/newhire-checklist`.
3. Viết mã HTML/CSS/JS và kiểm tra responsive đa thiết bị.
4. Ghi nhận thay đổi với thông điệp Conventional Commits.
5. Đẩy nhánh lên remote repository: `git push origin feature/newhire-checklist`.
6. Mở Pull Request (PR) vào nhánh `dev`.
7. Sinh viên khác trong nhóm đánh giá chéo (Code Review) và phê duyệt.
8. Merge PR vào nhánh `dev`, thực hiện test tích hợp, sau đó merge vào `main`.

---

### 3. Quy chuẩn Thông điệp Commit (Conventional Commits)

Nghiêm cấm các commit vô nghĩa như: `update`, `done`, `fix code`, `final`.  
Mẫu commit bắt buộc:

- `feat: add responsive newhire dashboard layout`
- `feat: implement interactive checklist with progress calculation`
- `feat: add ai policy qa simulation with citations and fallback mode`
- `feat: implement mentee risk indicator and filter tabs`
- `feat: add checkin note crud with localStorage persistence`
- `feat: add task assignment modal and mentor feedback synchronization`
- `feat: build hr journey personalizer with ai-2 simulation`
- `feat: add document library reader modal and tag filter`
- `feat: implement ai-3 progress risk detector with intervention actions`
- `refactor: extract shared storage manager and ui controller`
- `style: enhance mobile drawer and responsive data tables`
- `docs: update screen inventory table and obs video links`

---

### 4. Quy chuẩn Video Minh chứng OBS (OBS Evidence Protocol)

Theo nguyên tắc đề tài: **Mỗi giao diện thực tế đã được duyệt = 1 video OBS có mặt sinh viên**.

Mỗi video dài 2–3 phút, bao gồm đầy đủ 8 bước:
1. **Mở đầu:** Bật webcam góc màn hình hiển thị khuôn mặt sinh viên phụ trách, giới thiệu họ tên, mã sinh viên và vai trò.
2. **Khung dây & Bản mô phỏng:** Trình chiếu thiết kế Figma/Canva tương ứng với màn hình.
3. **Mã nguồn:** Mở tệp HTML, CSS và JavaScript của màn hình đó trong VS Code.
4. **Giải thích kiến trúc:** Giải thích bố cục HTML ngữ nghĩa, các thẻ CSS token và hàm JavaScript DOM xử lý sự kiện.
5. **Chỉnh sửa trực tiếp (Live Edit):** Thay đổi nhanh một thuộc tính (ví dụ: đổi màu badge, thêm trường dữ liệu hoặc đổi breakpoint) để chứng minh quyền làm chủ mã nguồn.
6. **Chạy thử tương tác:** Thao tác trên trình duyệt (thêm, sửa, xóa, lọc, chạy thử AI).
7. **Kiểm tra trạng thái:** Trình diễn trạng thái rỗng (empty state) hoặc trạng thái AI thất bại/không chắc chắn.
8. **Git Commit & Kết thúc:** Mở terminal, thực hiện commit thay đổi và nêu rõ mã công việc Trello + nhánh Git.

#### Quy tắc đặt tên video lưu trữ:
- `SV1-01-newhire-dashboard.mp4`
- `SV1-02-newhire-checklist.mp4`
- `SV1-03-newhire-ai-help.mp4`
- `SV2-01-mentor-mentee-list.mp4`
- `SV2-02-mentor-checkin-note.mp4`
- `SV2-03-mentor-task-assignment.mp4`
- `SV3-01-hr-journey-management.mp4`
- `SV3-02-hr-document-library.mp4`
- `SV3-03-hr-dashboard.mp4`
- `SV3-04-admin-department-management.mp4`
- `SV3-05-admin-user-management.mp4`
- `SV3-06-admin-system-settings.mp4`

