# BÁO CÁO KHAI BÁO SỬ DỤNG TRÍ TUỆ NHÂN TẠO (AI USAGE REPORT)
## Dự án: OnboardAI – BTL-20 CSE122 (Nhóm 3 Sinh viên)

> Căn cứ theo quy định tại **Mục 20: Khai báo sử dụng AI** của đề cương đồ án, nhóm sinh viên công khai và minh bạch toàn bộ quá trình sử dụng các công cụ AI trong quá trình nghiên cứu và phát triển sản phẩm.

---

### 1. Danh sách các công cụ AI đã sử dụng
1. **Google Gemini / Antigravity AI:** Hỗ trợ kiến trúc hệ thống, gợi ý cấu trúc dữ liệu LocalStorage và sinh mã khởi tạo các màn hình.
2. **GitHub Copilot:** Hỗ trợ tự động hoàn thành mã (auto-complete) trong VS Code cho các sự kiện DOM và hàm thao tác mảng JavaScript (`map`, `filter`, `find`).
3. **v0.dev / ChatGPT:** Tham khảo ý tưởng bố cục giao diện bảng điều khiển SaaS hiện đại.

---

### 2. Bảng kê khai các câu lệnh (Prompts) chính và phạm vi áp dụng

| STT | Công cụ | Câu lệnh chính (Prompt tóm tắt) | Phần AI sinh ra | Phần sinh viên đã chỉnh sửa & tối ưu |
|:---:|---|---|---|---|
| 1 | Gemini | *"Xây dựng mô hình cơ sở dữ liệu mẫu bằng JavaScript cho hệ thống Onboarding 4 vai trò (New Hire, Mentor, HR, Admin) bao gồm 7 thực thể liên kết."* | Cấu trúc mảng đối tượng `INITIAL_DATA` trong `data.js`. | Sinh viên bổ sung logic tính toán phần trăm hoàn thành, quy chuẩn dữ liệu tiếng Việt thực tế và liên kết khóa ngoại `mentorId`, `newHireId`. |
| 2 | Gemini | *"Thiết kế hệ thống Design Tokens bằng CSS Variables hỗ trợ bố cục Dashboard, sidebar cố định, topbar và responsive drawer cho mobile."* | Bộ biến màu sắc, shadow và khung cơ bản trong `style.css`. | Sinh viên tùy chỉnh breakpoint tablet/mobile trong `responsive.css`, bổ sung hiệu ứng animation cho thinking AI và custom checkbox checklist. |
| 3 | Gemini | *"Viết module mô phỏng 3 tính năng AI ở Frontend: Policy Q&A trích nguồn, Checklist Personalizer và Progress Risk Detector."* | Thuật toán mô phỏng trong `ai-engine.js`. | Sinh viên bổ sung trạng thái xử lý lỗi (failure mode), điều chỉnh thời gian trễ tự nhiên (800ms) và thiết kế hộp giải thích *"Vì sao có kết quả này?"*. |
| 4 | Copilot | *"Viết hàm StorageManager thực hiện CRUD cho tasks và checkins kèm phát sự kiện Event Bus."* | Các phương thức thao tác LocalStorage cơ bản. | Sinh viên bổ sung cơ chế tự động tính lại tiến độ của nhân sự mới (`recalculateNewHireProgress`) mỗi khi task được cập nhật. |

---

### 3. Các lỗi và hạn chế AI gặp phải & Cách sinh viên kiểm chứng, sửa lỗi

1. **Lỗi bất đồng bộ trạng thái khi nhiều vai trò tương tác:**
   - *Vấn đề AI gặp phải:* Khi AI sinh mã ban đầu, việc Mentor cập nhật task hoặc thêm check-in không tự động cập nhật lại thanh tiến độ của New Hire trên Dashboard.
   - *Cách sinh viên phát hiện:* Kiểm thử chéo giữa 2 tab trình duyệt: đăng nhập Mentor giao việc nhưng New Hire kiểm tra thì số task không tăng.
   - *Cách sửa của sinh viên:* Tự thiết kế thêm hàm `StorageManager.recalculateNewHireProgress()` và gắn cờ `window.dispatchEvent(new CustomEvent('onboardai_db_updated'))` để toàn bộ giao diện phản ứng đồng bộ.

2. **Lỗi kiểm tra hợp lệ dữ liệu biểu mẫu (Form Validation):**
   - *Vấn đề AI gặp phải:* Một số form do AI gợi ý không kiểm tra giá trị rỗng hoặc nhập chuỗi toàn dấu cách trước khi đẩy vào LocalStorage.
   - *Cách sửa của sinh viên:* Tự thêm kiểm tra `.trim().length < 3`, hiển thị Toast thông báo cảnh báo màu vàng và ngăn chặn submit form không hợp lệ.

3. **Lỗi Responsive bảng dữ liệu trên màn hình điện thoại:**
   - *Vấn đề AI gặp phải:* Thẻ `table` bị tràn khung hình ngang trên thiết bị di động dưới 480px làm vỡ giao diện.
   - *Cách sửa của sinh viên:* Bọc bảng trong `.table-responsive` với thuộc tính `overflow-x: auto` và bổ sung CSS rút gọn văn bản `text-overflow: ellipsis`.

---

### 4. Phân định tính năng Mock và API thật

| Tính năng | Phương thức triển khai | Lý do kỹ thuật |
|---|---|---|
| **Lưu trữ dữ liệu (CRUD)** | `LocalStorage` + JSON mô phỏng | Phù hợp nguyên tắc mục 13 của đề tài CSE122 (Frontend Prototype, không phụ thuộc server backend phức tạp, chạy độc lập mọi máy chấm bài). |
| **AI-1: Policy Q&A** | Semantic Rule-based Engine + RAG Mock | Mô phỏng chính xác luồng RAG nội bộ: quét tài liệu JSON, trích dẫn số trang/điều khoản và cung cấp trạng thái thất bại. Có sẵn tùy chọn nhập API Key thật trong System Settings. |
| **AI-2: Checklist Personalizer** | Heuristic Matrix Engine | Sinh linh hoạt checklist 4 giai đoạn dựa trên kết hợp ma trận Phòng ban x Cấp bậc x Chức danh. |
| **AI-3: Progress Risk Detector** | Matrix Multi-factor Algorithm | Thuật toán đánh giá đối chiếu thời gian trôi qua, tỷ lệ hoàn thành tasks và khoảng cách ngày check-in để chấm điểm rủi ro. |

---

### 5. Bài học nhóm sinh viên rút ra
- AI là trợ lý đắc lực giúp đẩy nhanh khâu viết boilerplate code và gợi ý ý tưởng bố cục, nhưng **không thể thay thế tư duy nghiệp vụ và kiểm thử logic của kỹ sư phần mềm**.
- Việc sinh viên tự tay chỉnh sửa, cấu trúc lại mã nguồn và hiểu cặn kẽ từng dòng lệnh là điều kiện tiên quyết để tự tin bảo vệ đồ án và thực hiện các yêu cầu "chỉnh sửa ngẫu nhiên 5–10 phút" của Giảng viên.

