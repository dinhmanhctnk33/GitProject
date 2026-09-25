# Business Rules Specification & Clarification Report

## 1. Tổng quan

| Nội dung | Chi tiết |
|---|---|
| Project | Hệ thống quản lý Thực tập sinh |
| Source | Product Backlog trong `Hệ thống quản lý Thực tập sinh-TTCS_T926_K10S6.xlsx`, sheet `Product Backlog` |
| Phạm vi nguồn | 10 Epic, 42 User Story (US-001 đến US-042); không có Acceptance Criteria chi tiết, Estimate hoặc Priority được điền trong backlog |
| Mục tiêu | Làm rõ Business Rules để refinement và chốt nghiệp vụ trước Sprint Planning |
| Phương pháp | Phân biệt Functional Requirement / Business Rule / Validation Rule; phân tích Actor-Goal-Object-Trigger-Pre/Post-condition; phân loại rule; kiểm tra state, quyền, dữ liệu, workflow, thời gian, tài liệu, ngoại lệ và traceability |
| Skills sử dụng | **Domain Modeling** (xác định bounded concepts, object và quan hệ); **Grill Me** (stress-test bằng câu hỏi nhánh, ngoại lệ và điều kiện biên); các thực hành BA/Requirements Engineering trong prompt (rule catalog, Given-When-Then, state transition, traceability) |
| Quy ước | `Confirmed` chỉ dùng cho điều được phát biểu trực tiếp; `Implicit` là điều suy ra từ câu chữ; `Need Clarification` là điểm chưa đủ căn cứ; `Conflict` là mâu thuẫn đã quan sát; `Missing` chỉ dùng trong phần missing-rule, không phải requirement chính thức |

### 1.1. Domain vocabulary hiện có

| Thuật ngữ | Nghĩa theo backlog | Điểm cần chốt |
|---|---|---|
| Intern / thực tập sinh | Người đăng ký, nộp hồ sơ, làm việc, báo cáo và nhận đánh giá/phụ cấp | Một người có thể có bao nhiêu hồ sơ/đợt? |
| HR | Người quản lý hồ sơ, xét duyệt, chương trình, lịch, chấm công, phụ cấp và hỗ trợ | Phạm vi dữ liệu của HR theo công ty/phòng ban hay toàn hệ thống? |
| Mentor | Người được HR thêm/gán, giao việc, phản hồi và đánh giá | Mentor có thuộc một phòng ban không? |
| Chương trình thực tập | Chương trình được HR tạo theo phòng ban, có ngày bắt đầu/kết thúc | Có một hay nhiều đợt; có mã và trạng thái không? |
| Hồ sơ / tài liệu | Hồ sơ ứng viên cùng CV, đơn, hợp đồng và giấy tờ hỗ trợ | Lifecycle, phiên bản, quyền xem và retention chưa được định nghĩa |
| Admin | Người tạo tài khoản, phân quyền, tích hợp và xem nhật ký | Có được xem/sửa dữ liệu nghiệp vụ hay chỉ quản trị hệ thống? |

## 2. Business Rule Catalog

Nguồn `Product Backlog` được dẫn theo số thứ tự User Story trong workbook. Rule dưới đây mô tả phần nghiệp vụ tối thiểu có thể trích xuất, không thay thế Functional Requirement.

| Rule ID | User Story | Category | Business Rule | Source | Status | Priority |
|---|---|---|---|---|---|---|
| BR-001 | US-001 | BR-AUTH / BR-DATA | HR được thêm mới hồ sơ thực tập sinh để lưu trữ thông tin. | Product Backlog | Confirmed | High |
| BR-002 | US-002 | BR-AUTH / BR-DATA | HR được chỉnh sửa hồ sơ thực tập sinh để cập nhật thông tin thay đổi. | Product Backlog | Confirmed | High |
| BR-003 | US-003 | BR-DATA | Hệ thống phải cho phép tìm kiếm/lọc thực tập sinh theo trường và ngành. | Product Backlog | Confirmed | Medium |
| BR-004 | US-004 | BR-DOCUMENT | Intern được upload CV và đơn xin thực tập để hoàn thiện hồ sơ. | Product Backlog | Confirmed | High |
| BR-005 | US-005 | BR-AUTH / BR-APPROVAL / BR-DOCUMENT | HR được xem và duyệt tài liệu của Intern để xác thực hồ sơ. | Product Backlog | Confirmed | High |
| BR-006 | US-006 | BR-AUTH / BR-WORKFLOW | Intern được đăng ký tài khoản và nộp hồ sơ trực tuyến tham gia chương trình. | Product Backlog | Confirmed | High |
| BR-007 | US-007 | BR-APPROVAL / BR-STATUS | HR được duyệt hoặc từ chối hồ sơ để chọn ứng viên phù hợp. | Product Backlog | Confirmed | High |
| BR-008 | US-008 | BR-WORKFLOW / BR-TIME | Hệ thống gửi email thông báo kết quả xét duyệt cho Intern. | Product Backlog | Confirmed | High |
| BR-009 | US-009 | BR-DOCUMENT / BR-AUTH | HR được tải hợp đồng thực tập lên hệ thống để quản lý giấy tờ. | Product Backlog | Confirmed | High |
| BR-010 | US-010 | BR-DOCUMENT / BR-WORKFLOW | Intern được xác nhận hợp đồng trên hệ thống để hoàn tất thủ tục. | Product Backlog | Confirmed | High |
| BR-011 | US-011 | BR-AUTH / BR-RELATION | HR được tạo chương trình thực tập theo phòng ban. | Product Backlog | Confirmed | High |
| BR-012 | US-012 | BR-AUTH / BR-RELATION | HR được phân công Intern cho Mentor để được hướng dẫn. | Product Backlog | Confirmed | High |
| BR-013 | US-013 | BR-TIME / BR-WORKFLOW | HR được thiết lập ngày bắt đầu và kết thúc chương trình. | Product Backlog | Confirmed | High |
| BR-014 | US-014 | BR-AUTH / BR-TIME | Intern được xem lịch thực tập cá nhân. | Product Backlog | Confirmed | Medium |
| BR-015 | US-015 | BR-AUTH / BR-RELATION | Mentor được giao nhiệm vụ cho Intern được hướng dẫn. | Product Backlog | Confirmed | High |
| BR-016 | US-016 | BR-AUTH / BR-WORKFLOW | Intern được cập nhật tiến độ công việc để Mentor theo dõi. | Product Backlog | Confirmed | High |
| BR-017 | US-017 | BR-DOCUMENT / BR-TIME | Intern được nộp báo cáo tuần để báo cáo kết quả thực tập. | Product Backlog | Confirmed | High |
| BR-018 | US-018 | BR-AUTH / BR-DOCUMENT | Mentor được xem báo cáo và phản hồi để hỗ trợ Intern. | Product Backlog | Confirmed | High |
| BR-019 | US-019 | BR-AUTH / BR-APPROVAL | Mentor được đánh giá kỹ năng và thái độ của Intern để tổng kết. | Product Backlog | Confirmed | High |
| BR-020 | US-020 | BR-REPORT | HR được tổng hợp đánh giá thành báo cáo cuối kỳ gửi trường/ban lãnh đạo. | Product Backlog | Confirmed | High |
| BR-021 | US-021 | BR-AUTH / BR-TIME | Intern được check-in/check-out để ghi nhận thời gian làm việc. | Product Backlog | Confirmed | High |
| BR-022 | US-022 | BR-AUTH / BR-REPORT | HR được xem báo cáo đi làm và nghỉ phép để quản lý chuyên cần. | Product Backlog | Confirmed | High |
| BR-023 | US-023 | BR-AUTH / BR-TIME | HR được thiết lập lịch làm việc linh hoạt cho từng nhóm. | Product Backlog | Confirmed | High |
| BR-024 | US-024 | BR-AUTH / BR-TIME / BR-WORKFLOW | Intern được đăng ký nghỉ phép để báo trước cho HR. | Product Backlog | Confirmed | High |
| BR-025 | US-025 | BR-AUTH / BR-DATA | HR được nhập thông tin phụ cấp của Intern để quản lý quyền lợi. | Product Backlog | Confirmed | High |
| BR-026 | US-026 | BR-AUTH / BR-REPORT | Intern được xem lịch sử nhận phụ cấp để theo dõi thu nhập. | Product Backlog | Confirmed | Medium |
| BR-027 | US-027 | BR-AUTH / BR-WORKFLOW | Intern được gửi yêu cầu hỗ trợ, ví dụ chứng nhận hoặc giấy tờ. | Product Backlog | Confirmed | High |
| BR-028 | US-028 | BR-AUTH / BR-WORKFLOW | HR được duyệt và phản hồi yêu cầu hỗ trợ của Intern. | Product Backlog | Confirmed | High |
| BR-029 | US-029 | BR-AUTH / BR-DATA | HR được thêm mới Mentor để phân công cho Intern. | Product Backlog | Confirmed | High |
| BR-030 | US-030 | BR-AUTH / BR-RELATION | HR được gán Mentor cho Intern để được hướng dẫn. | Product Backlog | Confirmed | High |
| BR-031 | US-031 | BR-REPORT / BR-RELATION | HR được xem số lượng Intern mỗi Mentor quản lý để cân bằng khối lượng. | Product Backlog | Confirmed | Medium |
| BR-032 | US-032 | BR-REPORT / BR-DATA | HR được xem số lượng Intern theo trường/ngành. | Product Backlog | Confirmed | Medium |
| BR-033 | US-033 | BR-REPORT | HR được xem tỷ lệ hoàn thành chương trình. | Product Backlog | Confirmed | High |
| BR-034 | US-034 | BR-REPORT / BR-DOCUMENT | HR được xuất báo cáo ra Excel/PDF để chia sẻ với lãnh đạo/trường. | Product Backlog | Confirmed | Medium |
| BR-035 | US-035 | BR-WORKFLOW / BR-TIME | Hệ thống gửi email tự động khi có lịch họp. | Product Backlog | Confirmed | High |
| BR-036 | US-036 | BR-AUTH / BR-WORKFLOW | Intern được nhận thông báo trên ứng dụng để không bỏ lỡ lịch trình. | Product Backlog | Confirmed | High |
| BR-037 | US-037 | BR-INTEGRATION / BR-DATA | Admin được tích hợp hệ thống với HRM để đồng bộ dữ liệu nhân sự. | Product Backlog | Confirmed | High |
| BR-038 | US-038 | BR-INTEGRATION / BR-TIME | Admin được tích hợp với hệ thống chấm công QR/thẻ. | Product Backlog | Confirmed | High |
| BR-039 | US-039 | BR-AUTH | Admin được tạo tài khoản cho HR, Mentor và Intern. | Product Backlog | Confirmed | High |
| BR-040 | US-040 | BR-AUTH | Admin được phân quyền chi tiết cho từng vai trò/chức năng. | Product Backlog | Confirmed | Critical |
| BR-041 | US-041 | BR-AUDIT / BR-DATA | Hệ thống phải sao lưu dữ liệu định kỳ để đảm bảo an toàn. | Product Backlog | Confirmed | Critical |
| BR-042 | US-042 | BR-AUDIT / BR-AUTH | Admin được xem nhật ký hoạt động để theo dõi thao tác trong hệ thống. | Product Backlog | Confirmed | Critical |

### 2.1. Rule ẩn xuyên suốt cần ghi nhận

Các điểm dưới đây xuất hiện ngầm từ nhiều story nhưng chưa thể coi là rule chính thức: mỗi thao tác cần gắn với actor có quyền; hồ sơ/tài liệu/công việc/báo cáo/chấm công/phụ cấp cần gắn với đúng Intern và chương trình; kết quả duyệt cần liên kết với thông báo; báo cáo phải lấy được dữ liệu từ các nghiệp vụ nguồn; tích hợp phải xử lý đồng bộ lỗi và trùng dữ liệu; nhật ký cần ghi nhận thao tác có tác động dữ liệu. Tất cả đều **Need Clarification** cho đến khi PO xác nhận phạm vi và logic cụ thể.

## 3. Business Rule Detail

Các detail dưới đây ưu tiên rule có ảnh hưởng lớn đến workflow, quyền, dữ liệu và tính nhất quán. Những trường chưa có trong backlog được đánh dấu rõ.

### BR-005 — HR xác thực tài liệu

- **Category:** BR-AUTH / BR-APPROVAL / BR-DOCUMENT
- **Business Rule:** HR được xem và duyệt tài liệu của Intern để xác thực hồ sơ.
- **Actor:** HR; Intern là chủ tài liệu.
- **Business Object:** CV, đơn xin thực tập, hồ sơ Intern.
- **Trigger:** HR mở và thực hiện duyệt tài liệu.
- **Pre-condition:** Tài liệu đã được Intern upload; quyền xem của HR được cấp. Điều kiện đầy đủ cụ thể: **[NEED CLARIFICATION]**.
- **Rule Logic:** Hệ thống chỉ cho phép actor có quyền HR thực hiện thao tác duyệt; kết quả duyệt phải gắn với tài liệu và hồ sơ tương ứng.
- **Post-condition:** Tài liệu có kết quả xác thực và có thể được dùng trong xét duyệt hồ sơ. Trạng thái cụ thể: **[NEED CLARIFICATION]**.
- **Exception:** Không có quyền; tài liệu thiếu/sai định dạng; tài liệu đã được duyệt; thao tác đồng thời: **[NEED CLARIFICATION]**.
- **Source / Status:** US-005 / Confirmed cho hành động và actor; các điều kiện còn lại Need Clarification.

### BR-007 — HR duyệt hoặc từ chối hồ sơ

- **Category:** BR-AUTH / BR-APPROVAL / BR-STATUS
- **Business Rule:** HR được duyệt hoặc từ chối hồ sơ để chọn ứng viên phù hợp.
- **Actor:** HR.
- **Business Object:** Hồ sơ thực tập.
- **Trigger:** HR chọn Approve hoặc Reject.
- **Pre-condition:** Hồ sơ đã được nộp; bộ tài liệu/điều kiện xét duyệt: **[NEED CLARIFICATION]**.
- **Rule Logic:** Chỉ HR có quyền quyết định; mỗi quyết định phải xác định hồ sơ và kết quả. Có cần lý do Reject, duyệt một hay nhiều cấp, và HR phụ trách hay HR bất kỳ: **[NEED CLARIFICATION]**.
- **Post-condition:** Hồ sơ có kết quả duyệt/từ chối và US-008 có thể phát thông báo.
- **Exception:** Hồ sơ chưa đủ dữ liệu, đã có quyết định, thiếu quyền hoặc quá hạn: **[NEED CLARIFICATION]**.
- **Source / Status:** US-007 / Confirmed về thao tác; trạng thái và điều kiện Need Clarification.

### BR-010 — Intern xác nhận hợp đồng

- **Category:** BR-DOCUMENT / BR-WORKFLOW
- **Business Rule:** Intern được xác nhận hợp đồng trên hệ thống để hoàn tất thủ tục.
- **Actor:** Intern.
- **Business Object:** Hợp đồng thực tập.
- **Trigger:** Intern thực hiện xác nhận.
- **Pre-condition:** HR đã tải hợp đồng; hợp đồng thuộc đúng Intern. Cơ chế xác nhận điện tử và hạn xác nhận: **[NEED CLARIFICATION]**.
- **Rule Logic:** Chỉ Intern được gắn với hợp đồng được xác nhận; hệ thống lưu thời điểm và người xác nhận nếu PO yêu cầu audit.
- **Post-condition:** Hợp đồng được ghi nhận đã xác nhận; trạng thái hồ sơ/chương trình tiếp theo: **[NEED CLARIFICATION]**.
- **Exception:** Hợp đồng thiếu, đã xác nhận, hết hạn hoặc bị thay thế: **[NEED CLARIFICATION]**.
- **Source / Status:** US-009, US-010 / Confirmed về vai trò và mục tiêu; Need Clarification về hiệu lực pháp lý.

### BR-011 — Tạo chương trình theo phòng ban

- **Category:** BR-AUTH / BR-RELATION
- **Business Rule:** HR được tạo chương trình thực tập theo phòng ban.
- **Actor:** HR.
- **Business Object:** Chương trình, phòng ban.
- **Trigger:** HR tạo chương trình.
- **Pre-condition:** Phòng ban tồn tại; quyền tạo được cấp. Mã chương trình, tên, thời gian và dữ liệu bắt buộc: **[NEED CLARIFICATION]**.
- **Rule Logic:** Chương trình phải tham chiếu một phòng ban đã chọn; phạm vi Intern/Mentor phải nhất quán với phòng ban.
- **Post-condition:** Chương trình được lưu và có thể nhận phân công/lịch.
- **Exception:** Phòng ban không tồn tại, dữ liệu trùng, ngày không hợp lệ: **[NEED CLARIFICATION]**.
- **Source / Status:** US-011 / Confirmed về quan hệ HR-chương trình-phòng ban; chi tiết Need Clarification.

### BR-013 — Khoảng thời gian chương trình

- **Category:** BR-TIME / BR-WORKFLOW
- **Business Rule:** HR được thiết lập ngày bắt đầu và kết thúc chương trình.
- **Actor:** HR.
- **Business Object:** Chương trình thực tập.
- **Trigger:** HR nhập hoặc cập nhật lịch chương trình.
- **Pre-condition:** Chương trình tồn tại. `Ngày bắt đầu < ngày kết thúc`, múi giờ, cho phép sửa sau khi bắt đầu: **[NEED CLARIFICATION]**.
- **Rule Logic:** Khoảng thời gian chương trình là cơ sở cho lịch cá nhân, báo cáo, chấm công và tỷ lệ hoàn thành; các quy tắc biên chưa được backlog nêu.
- **Post-condition:** Chương trình có thời gian áp dụng.
- **Exception:** Ngày đảo, trùng khoảng thời gian, sửa sau khi có dữ liệu: **[NEED CLARIFICATION]**.
- **Source / Status:** US-013 / Confirmed về khả năng thiết lập; logic thời gian Need Clarification.

### BR-017 — Nộp báo cáo tuần

- **Category:** BR-DOCUMENT / BR-TIME
- **Business Rule:** Intern được nộp báo cáo tuần để báo cáo kết quả thực tập.
- **Actor:** Intern.
- **Business Object:** Báo cáo tuần, chương trình, Intern.
- **Trigger:** Intern nộp báo cáo.
- **Pre-condition:** Intern thuộc chương trình; tuần báo cáo hợp lệ. Deadline, định dạng, cho sửa/nộp lại: **[NEED CLARIFICATION]**.
- **Rule Logic:** Mỗi báo cáo phải gắn với một Intern và một kỳ/tuần; uniqueness của báo cáo trong cùng kỳ: **[NEED CLARIFICATION]**.
- **Post-condition:** Báo cáo có thể được Mentor xem và phản hồi.
- **Exception:** Quá hạn, trùng kỳ, thiếu nội dung, upload lỗi hoặc không thuộc chương trình: **[NEED CLARIFICATION]**.
- **Source / Status:** US-017, US-018 / Confirmed về actor và mục đích; các constraint Need Clarification.

### BR-019 — Mentor đánh giá

- **Category:** BR-AUTH / BR-APPROVAL
- **Business Rule:** Mentor được đánh giá kỹ năng và thái độ của Intern để tổng kết.
- **Actor:** Mentor được gán cho Intern.
- **Business Object:** Đánh giá, Intern, Mentor.
- **Trigger:** Mentor thực hiện đánh giá.
- **Pre-condition:** Mentor-Intern đã được gán; kỳ đánh giá mở. Tiêu chí, thang điểm, số lần sửa và deadline: **[NEED CLARIFICATION]**.
- **Rule Logic:** Mentor chỉ đánh giá Intern thuộc phạm vi mình phụ trách; đánh giá phải gắn kỳ và người đánh giá.
- **Post-condition:** Đánh giá được lưu để HR tổng hợp.
- **Exception:** Mentor không được gán, kỳ đã khóa, thiếu tiêu chí hoặc đánh giá trùng: **[NEED CLARIFICATION]**.
- **Source / Status:** US-012, US-019, US-020 / Implicit quan hệ Mentor-Intern; Need Clarification về form và hiệu lực.

### BR-021 — Check-in/check-out

- **Category:** BR-AUTH / BR-TIME
- **Business Rule:** Intern được check-in/check-out để ghi nhận thời gian làm việc.
- **Actor:** Intern; có thể có nguồn QR/thẻ theo US-038.
- **Business Object:** Bản ghi chấm công, lịch làm việc.
- **Trigger:** Intern check-in hoặc check-out.
- **Pre-condition:** Intern đang thuộc chương trình; lịch làm việc áp dụng. Địa điểm, thiết bị, một hay nhiều lần/ngày, cho sửa: **[NEED CLARIFICATION]**.
- **Rule Logic:** Bản ghi phải liên kết Intern và thời điểm; check-out phải được xử lý theo một check-in hợp lệ nếu PO xác nhận.
- **Post-condition:** Bản ghi xuất hiện trong báo cáo đi làm/nghỉ phép.
- **Exception:** Ngoài lịch, thiếu check-in, trùng thao tác, offline, QR/thẻ không khớp: **[NEED CLARIFICATION]**.
- **Source / Status:** US-021, US-022, US-023, US-038 / Confirmed về mục tiêu; logic vận hành Need Clarification.

### BR-024 — Đăng ký nghỉ phép

- **Category:** BR-AUTH / BR-TIME / BR-WORKFLOW
- **Business Rule:** Intern được đăng ký nghỉ phép để báo trước cho HR.
- **Actor:** Intern; HR là bên nhận/xử lý theo câu chuyện.
- **Business Object:** Yêu cầu nghỉ phép, lịch làm việc.
- **Trigger:** Intern gửi yêu cầu nghỉ.
- **Pre-condition:** Intern thuộc lịch/nhóm làm việc; khoảng nghỉ hợp lệ. Số ngày báo trước, loại nghỉ, duyệt/từ chối: **[NEED CLARIFICATION]**.
- **Rule Logic:** Yêu cầu phải xác định Intern, khoảng thời gian và lý do/loại nghỉ nếu bắt buộc; xung đột với lịch: **[NEED CLARIFICATION]**.
- **Post-condition:** HR có yêu cầu để xem trong báo cáo và xử lý.
- **Exception:** Trùng yêu cầu, quá hạn báo trước, vượt số ngày, ngoài chương trình: **[NEED CLARIFICATION]**.
- **Source / Status:** US-024 / Confirmed về gửi yêu cầu; Need Clarification về approval.

### BR-028 — HR xử lý yêu cầu hỗ trợ

- **Category:** BR-AUTH / BR-WORKFLOW
- **Business Rule:** HR được duyệt và phản hồi yêu cầu hỗ trợ của Intern.
- **Actor:** HR; Intern là người gửi.
- **Business Object:** Yêu cầu hỗ trợ, phản hồi, giấy tờ/chứng nhận.
- **Trigger:** HR mở và xử lý yêu cầu.
- **Pre-condition:** Yêu cầu tồn tại và thuộc Intern; quyền HR hợp lệ.
- **Rule Logic:** Yêu cầu phải có kết quả xử lý và phản hồi; trạng thái, lý do từ chối và SLA: **[NEED CLARIFICATION]**.
- **Post-condition:** Intern nhận được kết quả/phản hồi.
- **Exception:** Yêu cầu trùng, thiếu thông tin, không đủ điều kiện hoặc không thể cấp giấy tờ: **[NEED CLARIFICATION]**.
- **Source / Status:** US-027, US-028 / Confirmed về actor; workflow Need Clarification.

### BR-037 — Đồng bộ HRM

- **Category:** BR-INTEGRATION / BR-DATA
- **Business Rule:** Admin được tích hợp hệ thống với HRM để đồng bộ dữ liệu nhân sự.
- **Actor:** Admin; hệ thống HRM là external system.
- **Business Object:** Dữ liệu nhân sự/tài khoản.
- **Trigger:** Đồng bộ thủ công hoặc tự động: **[NEED CLARIFICATION]**.
- **Pre-condition:** Kết nối và mapping trường được cấu hình; thông tin xác thực: **[NEED CLARIFICATION]**.
- **Rule Logic:** Cần xác định nguồn dữ liệu chuẩn, chiều đồng bộ, khóa ghép, xử lý trùng/xung đột và dữ liệu bị xóa.
- **Post-condition:** Dữ liệu nhân sự được đồng bộ theo chính sách đã duyệt.
- **Exception:** Timeout, schema mismatch, duplicate, partial failure: **[NEED CLARIFICATION]**.
- **Source / Status:** US-037 / Confirmed về mục tiêu tích hợp; toàn bộ contract Need Clarification.

### BR-040 — Phân quyền chi tiết

- **Category:** BR-AUTH
- **Business Rule:** Admin được phân quyền chi tiết để kiểm soát chức năng từng vai trò.
- **Actor:** Admin.
- **Business Object:** Tài khoản, role, permission, resource.
- **Trigger:** Admin tạo/sửa phân quyền hoặc người dùng thực hiện chức năng.
- **Pre-condition:** Tài khoản và role tồn tại.
- **Rule Logic:** Mọi thao tác trên resource phải được kiểm tra quyền; tối thiểu cần phân biệt Admin, HR, Mentor, Intern. Phân quyền theo chức năng, dữ liệu, phòng ban hay chương trình: **[NEED CLARIFICATION]**.
- **Post-condition:** Quyền có hiệu lực theo chính sách; thay đổi quyền cần audit nếu được xác nhận.
- **Exception:** Không quyền, quyền hết hiệu lực, tài khoản khóa, privilege escalation: **[NEED CLARIFICATION]**.
- **Source / Status:** US-039, US-040 / Confirmed về vai trò và mục tiêu; matrix quyền Need Clarification.

### BR-042 — Nhật ký hoạt động

- **Category:** BR-AUDIT / BR-AUTH
- **Business Rule:** Admin được xem nhật ký hoạt động để theo dõi thao tác trong hệ thống.
- **Actor:** Hệ thống ghi log; Admin xem log.
- **Business Object:** Audit log.
- **Trigger:** Người dùng thực hiện thao tác có tác động hệ thống.
- **Pre-condition:** Cơ chế ghi log được bật.
- **Rule Logic:** Nội dung log, actor, thời điểm, resource, kết quả và dữ liệu trước/sau: **[NEED CLARIFICATION]**; log phải chống sửa/xóa trái phép nếu được yêu cầu.
- **Post-condition:** Admin có thể truy vết hoạt động trong phạm vi được cấp.
- **Exception:** Ghi log thất bại, log chứa dữ liệu nhạy cảm, retention hết hạn: **[NEED CLARIFICATION]**.
- **Source / Status:** US-042 / Confirmed về xem nhật ký; schema, retention Need Clarification.

## 4. Phân tích từng User Story

Bảng này áp dụng khung Actor-Goal-Object-Trigger-Pre/Post/Exception cho toàn bộ backlog. Dấu `?` là thông tin chưa có trong nguồn.

| US | Actor / Goal | Object / Trigger | Pre-condition | Post-condition | Exception / điểm cần làm rõ |
|---|---|---|---|---|---|
| US-001 | HR lưu hồ sơ mới | Hồ sơ / thêm mới | HR có quyền; trường bắt buộc ? | Hồ sơ được lưu | Trùng hồ sơ, dữ liệu thiếu ? |
| US-002 | HR cập nhật hồ sơ | Hồ sơ / chỉnh sửa | Hồ sơ tồn tại; trạng thái cho sửa ? | Thông tin cập nhật | Khóa sau duyệt, audit ? |
| US-003 | HR quản lý danh sách | Intern / tìm kiếm-lọc | Có dữ liệu | Danh sách theo trường/ngành | Phạm vi dữ liệu, phân trang ? |
| US-004 | Intern hoàn thiện hồ sơ | CV, đơn / upload | Tài khoản/hồ sơ ? | Tài liệu gắn hồ sơ | Định dạng, dung lượng, phiên bản ? |
| US-005 | HR xác thực | Tài liệu / xem-duyệt | Tài liệu tồn tại | Có kết quả duyệt | Quyền, lý do reject, sửa/xóa ? |
| US-006 | Intern tham gia chương trình | Tài khoản, hồ sơ / đăng ký-nộp | Điều kiện tham gia ? | Hồ sơ trực tuyến được nộp | Email trùng, deadline, nộp lại ? |
| US-007 | HR chọn ứng viên | Hồ sơ / approve-reject | Hồ sơ đủ điều kiện ? | Có kết quả xét duyệt | Lý do reject, nhiều cấp, re-submit ? |
| US-008 | Hệ thống thông báo | Kết quả / quyết định duyệt | Có email hợp lệ ? | Email được gửi | Retry, bounce, nội dung, thời điểm ? |
| US-009 | HR quản lý giấy tờ | Hợp đồng / upload | Hồ sơ phù hợp ? | Hợp đồng trên hệ thống | Phiên bản, quyền xem, ký ? |
| US-010 | Intern hoàn tất thủ tục | Hợp đồng / xác nhận | Hợp đồng đã upload | Hợp đồng được xác nhận | Xác nhận điện tử, deadline, thay đổi ? |
| US-011 | HR tổ chức kế hoạch | Chương trình/phòng ban / tạo | Phòng ban tồn tại | Chương trình được tạo | Mã, trùng, trạng thái, owner ? |
| US-012 | HR phân công hướng dẫn | Intern-Mentor / assign | Cả hai tồn tại; Mentor phù hợp ? | Quan hệ phân công | Một/nhiều Mentor, đổi Mentor ? |
| US-013 | HR quản lý thời gian | Chương trình / set dates | Chương trình tồn tại | Có khoảng thời gian | Start/end, sửa sau bắt đầu ? |
| US-014 | Intern xem kế hoạch | Lịch cá nhân / view | Được gán chương trình/lịch | Lịch hiển thị | Múi giờ, quyền xem, lịch trống ? |
| US-015 | Mentor giao việc | Nhiệm vụ / create | Mentor được gán ? | Nhiệm vụ thuộc Intern | Deadline, ưu tiên, sửa/xóa ? |
| US-016 | Intern báo tiến độ | Nhiệm vụ / update | Nhiệm vụ thuộc Intern | Tiến độ cập nhật | Giá trị hợp lệ, khóa sau deadline ? |
| US-017 | Intern báo cáo | Báo cáo tuần / submit | Thuộc chương trình | Báo cáo được nộp | Deadline, trùng tuần, file ? |
| US-018 | Mentor hỗ trợ | Báo cáo / view-feedback | Được gán với Intern | Phản hồi lưu | Sửa/xóa, thông báo, deadline ? |
| US-019 | Mentor tổng kết | Đánh giá / evaluate | Có kỳ đánh giá | Đánh giá lưu | Rubric, thang điểm, khóa kỳ ? |
| US-020 | HR chia sẻ tổng kết | Báo cáo cuối kỳ / aggregate-export | Có dữ liệu đánh giá | Báo cáo tổng hợp | Công thức tỷ lệ, dữ liệu thiếu, quyền gửi ? |
| US-021 | Intern ghi nhận giờ | Chấm công / check-in-out | Có lịch làm việc | Bản ghi thời gian | Ngoài ca, trùng, thiếu cặp, timezone ? |
| US-022 | HR quản lý chuyên cần | Chấm công/nghỉ / view report | Có dữ liệu | Báo cáo hiển thị | Công thức, chỉnh công, export ? |
| US-023 | HR tổ chức ca | Lịch nhóm / set schedule | Nhóm tồn tại | Lịch áp dụng | Overlap, timezone, thay đổi lịch ? |
| US-024 | Intern báo nghỉ | Nghỉ phép / submit | Lịch và chương trình hợp lệ | Yêu cầu được ghi nhận | Duyệt, báo trước, trùng, quota ? |
| US-025 | HR quản lý quyền lợi | Phụ cấp / enter | Intern đủ điều kiện ? | Khoản phụ cấp được lưu | Công thức, kỳ, chỉnh sửa, currency ? |
| US-026 | Intern theo dõi thu nhập | Lịch sử phụ cấp / view | Có dữ liệu và quyền | Lịch sử hiển thị | Phạm vi kỳ, dữ liệu nhạy cảm ? |
| US-027 | Intern yêu cầu giấy tờ | Yêu cầu hỗ trợ / submit | Tài khoản hợp lệ | Yêu cầu được ghi nhận | Loại yêu cầu, SLA, trùng ? |
| US-028 | HR xử lý yêu cầu | Yêu cầu / approve-respond | Yêu cầu tồn tại | Phản hồi gửi Intern | Reject reason, trạng thái, SLA ? |
| US-029 | HR quản lý Mentor | Mentor / create | HR có quyền | Mentor được lưu | Trùng tài khoản, phòng ban ? |
| US-030 | HR gán Mentor | Quan hệ Mentor-Intern / assign | Hai đối tượng tồn tại | Quan hệ được tạo | Capacity, đổi/hủy, nhiều Mentor ? |
| US-031 | HR cân bằng tải | Phân công / count | Có dữ liệu gán | Số lượng theo Mentor | Tính active/inactive, filter ? |
| US-032 | HR phân tích nguồn | Intern / aggregate | Dữ liệu trường/ngành | Số lượng theo nhóm | Giá trị thiếu, thời điểm snapshot ? |
| US-033 | HR đánh giá chất lượng | Chương trình / calculate | Có định nghĩa completion | Tỷ lệ hiển thị | Công thức mẫu số, kỳ, missing data ? |
| US-034 | HR chia sẻ báo cáo | Báo cáo / export | Có quyền và dữ liệu | File Excel/PDF tạo được | Mask dữ liệu, template, lỗi export ? |
| US-035 | Hệ thống nhắc lịch | Lịch họp / scheduled email | Có người nhận/email ? | Email được gửi | Trùng gửi, retry, timezone, hủy lịch ? |
| US-036 | Intern nhận lịch trình | Notification / deliver | Có đăng ký ứng dụng ? | Thông báo hiển thị | Offline, read status, preference ? |
| US-037 | Admin đồng bộ HRM | Dữ liệu nhân sự / sync | Kết nối/mapping ? | Dữ liệu đồng bộ | Conflict, retry, source of truth ? |
| US-038 | Admin kết nối chấm công | QR/thẻ / integration | Thiết bị/API ? | Dữ liệu chấm công nhận | Duplicate, offline, mapping, retry ? |
| US-039 | Admin cấp tài khoản | Account / create | Role và dữ liệu định danh ? | Account được tạo | Trùng email, reset, invite ? |
| US-040 | Admin kiểm soát quyền | Role/permission / configure | Account tồn tại | Policy có hiệu lực | Deny-by-default, data scope, audit ? |
| US-041 | Hệ thống bảo toàn dữ liệu | Backup / scheduled | Storage/chính sách ? | Backup hoàn tất | Restore, retention, encryption, failure ? |
| US-042 | Admin truy vết | Audit log / view | Log tồn tại; Admin có quyền | Log được xem/lọc | Tamper, retention, dữ liệu nhạy cảm ? |

## 5. State & Transition Rules

Backlog chỉ nêu hành động duyệt/từ chối/xác nhận/phản hồi, không nêu tên state chính thức. Vì vậy không được coi các state bên dưới là thiết kế đã chốt.

| Object | Current State | Action | Actor | Condition | Next State |
|---|---|---|---|---|---|
| Hồ sơ | `[NEED CLARIFICATION]` | Submit | Intern | Hồ sơ đủ dữ liệu và tài liệu ? | `[NEED CLARIFICATION]` |
| Hồ sơ | `[NEED CLARIFICATION]` | Approve | HR | Hồ sơ/tài liệu hợp lệ ? | `[NEED CLARIFICATION]` |
| Hồ sơ | `[NEED CLARIFICATION]` | Reject | HR | Có lý do và điều kiện reject ? | `[NEED CLARIFICATION]` |
| Hợp đồng | `[NEED CLARIFICATION]` | Upload | HR | Hợp đồng thuộc hồ sơ ? | `[NEED CLARIFICATION]` |
| Hợp đồng | `[NEED CLARIFICATION]` | Confirm | Intern | Hợp đồng hợp lệ, chưa hết hạn ? | `[NEED CLARIFICATION]` |
| Tài liệu | `[NEED CLARIFICATION]` | Approve | HR | Tài liệu xem xét xong ? | `[NEED CLARIFICATION]` |
| Báo cáo tuần | `[NEED CLARIFICATION]` | Submit | Intern | Đúng kỳ, trước deadline ? | `[NEED CLARIFICATION]` |
| Yêu cầu hỗ trợ | `[NEED CLARIFICATION]` | Approve / Respond | HR | Yêu cầu đủ thông tin ? | `[NEED CLARIFICATION]` |
| Yêu cầu nghỉ phép | `[NEED CLARIFICATION]` | Submit | Intern | Khoảng nghỉ hợp lệ ? | `[NEED CLARIFICATION]` |
| Đánh giá | `[NEED CLARIFICATION]` | Submit/Finalize | Mentor | Đúng Intern và kỳ đánh giá ? | `[NEED CLARIFICATION]` |

Cần chốt tối thiểu: state mặc định, state cuối, quyền chuyển state, điều kiện chuyển, có quay lại hay không, chỉnh sửa sau approve/reject, lý do reject, và audit cho từng transition.

## 6. Business Rule Questions

| Question ID | Business Area | Question | Reason | Impact |
|---|---|---|---|---|
| BQ-001 | Hồ sơ | Hồ sơ mới tạo có trạng thái mặc định nào? | Chưa có lifecycle | High |
| BQ-002 | Hồ sơ | Một Intern được có bao nhiêu hồ sơ trong cùng một chương trình? | Chưa có uniqueness | Critical |
| BQ-003 | Hồ sơ | Email, số điện thoại, mã Intern và mã hồ sơ unique ở phạm vi nào? | Ảnh hưởng định danh | Critical |
| BQ-004 | Hồ sơ | HR nào được sửa/xem hồ sơ: mọi HR hay HR phụ trách công ty/phòng ban? | Chưa có data scope | Critical |
| BQ-005 | Tài liệu | CV và đơn xin thực tập bắt buộc ở thời điểm upload hay nộp hồ sơ? | Ảnh hưởng submit | High |
| BQ-006 | Tài liệu | Định dạng, dung lượng, số phiên bản và chính sách thay thế tài liệu là gì? | Chưa có validation | High |
| BQ-007 | Tài liệu | Sau khi HR duyệt, Intern có được thay/xóa tài liệu không? | Ảnh hưởng integrity | High |
| BQ-008 | Phê duyệt | HR duyệt một cấp hay nhiều cấp; HR nào có thẩm quyền? | Chưa có approval policy | Critical |
| BQ-009 | Phê duyệt | Reject có bắt buộc lý do không, và Intern có được sửa rồi nộp lại không? | Chưa có exception flow | Critical |
| BQ-010 | Thông báo | Email kết quả gửi khi nào, retry ra sao và xử lý email bounce thế nào? | Ảnh hưởng communication | High |
| BQ-011 | Hợp đồng | “Xác nhận” có giá trị ký điện tử không? Có deadline và cho xác nhận lại không? | Ảnh hưởng pháp lý | Critical |
| BQ-012 | Chương trình | Chương trình có mã unique, state và owner không? Có thể sửa sau khi có dữ liệu không? | Quản lý lifecycle | High |
| BQ-013 | Phân công | Intern có thể có một hay nhiều Mentor; Mentor có giới hạn số Intern không? | Ảnh hưởng quan hệ/capacity | High |
| BQ-014 | Lịch | Ngày bắt đầu có phải trước ngày kết thúc? Múi giờ nào? Có cho overlap không? | Validation thời gian | High |
| BQ-015 | Công việc | Ai đặt deadline/ưu tiên; Intern có được sửa nhiệm vụ hay chỉ cập nhật tiến độ? | Phân quyền workflow | High |
| BQ-016 | Báo cáo | Một tuần có một báo cáo hay nhiều phiên bản? Deadline, nộp trễ và sửa sau phản hồi thế nào? | Tính duy nhất/workflow | High |
| BQ-017 | Đánh giá | Rubric, thang điểm, kỳ đánh giá, deadline và cơ chế khóa đánh giá là gì? | Cần kiểm thử được | Critical |
| BQ-018 | Chấm công | Một ngày cho phép bao nhiêu check-in/out; xử lý quên check-out và sửa công thế nào? | Tính đúng dữ liệu | Critical |
| BQ-019 | Nghỉ phép | Có cần HR duyệt không; báo trước tối thiểu, loại nghỉ và giới hạn ngày là gì? | Backlog chỉ nói báo trước | High |
| BQ-020 | Phụ cấp | Ai đủ điều kiện, kỳ tính, đơn vị tiền tệ, công thức và quyền sửa là gì? | Dữ liệu quyền lợi | Critical |
| BQ-021 | Hỗ trợ | Các trạng thái, SLA, lý do từ chối và thông báo của yêu cầu hỗ trợ là gì? | Chưa có workflow | High |
| BQ-022 | Báo cáo | Công thức “tỷ lệ hoàn thành chương trình” và mẫu số là gì? | Tránh báo cáo sai | Critical |
| BQ-023 | Xuất dữ liệu | Excel/PDF có che dữ liệu nhạy cảm, template và giới hạn phạm vi không? | Rủi ro privacy | High |
| BQ-024 | Notification | Thông báo trong app có lưu lịch sử, trạng thái đã đọc và tùy chọn tắt không? | Chưa có delivery policy | Medium |
| BQ-025 | Tích hợp HRM | Hệ thống nào là source of truth; đồng bộ một chiều/hai chiều; khóa mapping nào? | Tránh xung đột dữ liệu | Critical |
| BQ-026 | Tích hợp chấm công | QR/thẻ được định danh thế nào; offline, duplicate và retry xử lý ra sao? | Tính toàn vẹn chấm công | Critical |
| BQ-027 | Tài khoản | Email có unique toàn hệ thống không; cơ chế mời, reset, khóa và vô hiệu hóa là gì? | Quyền truy cập | Critical |
| BQ-028 | Phân quyền | Matrix quyền chi tiết theo role, resource, phòng ban/chương trình là gì? | US-040 quá rộng | Critical |
| BQ-029 | Backup | Chu kỳ, retention, encryption, nơi lưu, kiểm thử restore và RPO/RTO là gì? | US-041 chưa đủ vận hành | Critical |
| BQ-030 | Audit | Log trường nào, retention bao lâu, ai xem, có log đọc dữ liệu và chống sửa/xóa không? | US-042 chưa đủ kiểm toán | Critical |

## 7. Business Rule Conflicts

Chưa phát hiện mâu thuẫn trực tiếp giữa hai User Story trong Product Backlog. Tuy nhiên có các **potential conflict / ambiguity** cần xác nhận:

| Conflict ID | Source A | Source B | Nội dung mâu thuẫn/không nhất quán | Câu hỏi cần xác nhận |
|---|---|---|---|---|
| BC-001 | US-004 | US-005, US-007 | Intern upload tài liệu nhưng chưa rõ HR duyệt tài liệu trước hay sau xét duyệt hồ sơ. | Thứ tự bắt buộc giữa upload, document approval và application approval là gì? |
| BC-002 | US-007 | US-008 | Kết quả xét duyệt được email, nhưng chưa nói kết quả nào kích hoạt email và retry thế nào. | Cả Approve và Reject có gửi email không? |
| BC-003 | US-012, US-030 | US-031 | Có phân công Mentor và đếm số Intern, nhưng chưa có giới hạn capacity hay rule đổi Mentor. | Có giới hạn số Intern/Mentor và hiệu lực tính là active assignment không? |
| BC-004 | US-013 | US-021, US-023 | Chương trình có ngày bắt đầu/kết thúc, lịch làm việc và chấm công nhưng chưa rõ nguồn thời gian chuẩn. | Chấm công dựa trên program dates hay work schedule? |
| BC-005 | US-019 | US-020, US-033 | Đánh giá Mentor được tổng hợp và tỷ lệ hoàn thành được báo cáo, nhưng thiếu định nghĩa “hoàn thành”. | Công thức, nguồn dữ liệu và thời điểm khóa báo cáo là gì? |
| BC-006 | US-021 | US-038 | Chấm công trực tiếp và qua QR/thẻ cùng tồn tại nhưng chưa có quy tắc chống ghi nhận trùng. | Nguồn nào là authoritative và hệ thống gộp duplicate ra sao? |
| BC-007 | US-037 | US-039 | HRM có thể đồng bộ dữ liệu nhân sự trong khi Admin tạo tài khoản cho cùng các vai trò. | Account nào là source of truth và xử lý bản ghi trùng thế nào? |
| BC-008 | US-002 | US-005, US-007, US-010 | HR sửa hồ sơ, HR duyệt tài liệu/hồ sơ và Intern xác nhận hợp đồng nhưng chưa quy định khóa dữ liệu sau các mốc đó. | Object nào bị khóa sau approve/confirm và ai được mở lại? |

## 8. Missing Business Rules

Các mục sau là **Potential Missing Rule — Need Clarification**, không phải requirement chính thức:

1. Lifecycle và state mặc định/cuối của hồ sơ, tài liệu, hợp đồng, chương trình, báo cáo, nghỉ phép, hỗ trợ, đánh giá và tài khoản.
2. Phạm vi uniqueness của email, mã Intern, mã hồ sơ, mã chương trình, mã Mentor và bản ghi theo kỳ.
3. Điều kiện bắt buộc để Submit, Approve, Reject, Confirm, Finalize, Export và Sync.
4. Matrix quyền cụ thể theo role và phạm vi dữ liệu theo công ty/phòng ban/chương trình.
5. Chính sách chỉnh sửa, xóa, thay thế phiên bản sau duyệt hoặc sau khi kỳ đã khóa.
6. Deadline, timezone, grace period, xử lý nộp trễ và thông báo gần deadline.
7. Chuẩn file, size, virus scan, versioning và retention cho CV, đơn, hợp đồng, báo cáo và giấy tờ.
8. Lý do bắt buộc khi Reject hoặc từ chối yêu cầu; khả năng sửa và nộp lại.
9. Công thức và nguồn dữ liệu cho tỷ lệ hoàn thành, chuyên cần, số lượng theo trường/ngành và tổng hợp đánh giá.
10. Quy tắc một hay nhiều Mentor/Intern assignment, capacity và hiệu lực assignment.
11. Quy tắc chấm công: cặp check-in/out, duplicate, ngoại lệ, chỉnh công, timezone và offline.
12. Quy trình duyệt nghỉ phép, quota, loại nghỉ, báo trước tối thiểu và overlap.
13. Điều kiện, công thức, kỳ, currency và approval của phụ cấp.
14. SLA, state, escalation và notification cho yêu cầu hỗ trợ.
15. Hợp đồng: ý nghĩa pháp lý của “xác nhận”, chữ ký điện tử, deadline và thay thế.
16. Email/app notification: preference, read/unread, retry, bounce, idempotency và lịch sử.
17. HRM/QR-card integration: source of truth, mapping, direction, conflict, retry và reconciliation.
18. Tài khoản: invite, reset, MFA, lockout, deactivation, email uniqueness và offboarding.
19. Backup: RPO/RTO, restore test, retention, encryption, access và cảnh báo thất bại.
20. Audit: schema, dữ liệu trước/sau, actor, timestamp, correlation ID, retention, tamper protection và quyền xem.
21. Quyền riêng tư: dữ liệu nào được xuất/gửi trường/ban lãnh đạo, masking và thời hạn lưu.
22. Idempotency và optimistic locking cho thao tác đồng thời hoặc retry.

## 9. Traceability

Backlog hiện không có Acceptance Criteria và Functional Requirement ID. Cột tương ứng được đánh dấu `TBD` để PO/BA bổ sung, tránh tạo quan hệ giả.

| User Story | Business Rule | Acceptance Criteria | Requirement | Test Case |
|---|---|---|---|---|
| US-001 | BR-001 | TBD-AC-001 | TBD-FR-001 | TBD-TC-001 |
| US-004 | BR-004, BR-005 | TBD-AC-004/005 | TBD-FR-004/005 | TBD-TC-004/005 |
| US-006 | BR-006, BR-007 | TBD-AC-006/007 | TBD-FR-006/007 | TBD-TC-006/007 |
| US-009/010 | BR-009, BR-010 | TBD-AC-009/010 | TBD-FR-009/010 | TBD-TC-009/010 |
| US-011/013 | BR-011, BR-013 | TBD-AC-011/013 | TBD-FR-011/013 | TBD-TC-011/013 |
| US-012/015/019 | BR-012, BR-015, BR-019 | TBD-AC-012/015/019 | TBD-FR-012/015/019 | TBD-TC-012/015/019 |
| US-017/018 | BR-017, BR-018 | TBD-AC-017/018 | TBD-FR-017/018 | TBD-TC-017/018 |
| US-021/024 | BR-021, BR-024 | TBD-AC-021/024 | TBD-FR-021/024 | TBD-TC-021/024 |
| US-025/028 | BR-025, BR-028 | TBD-AC-025/028 | TBD-FR-025/028 | TBD-TC-025/028 |
| US-032/033/034 | BR-032, BR-033, BR-034 | TBD-AC-032/033/034 | TBD-FR-032/033/034 | TBD-TC-032/033/034 |
| US-037/038 | BR-037, BR-038 | TBD-AC-037/038 | TBD-FR-037/038 | TBD-TC-037/038 |
| US-039/040/042 | BR-039, BR-040, BR-042 | TBD-AC-039/040/042 | TBD-FR-039/040/042 | TBD-TC-039/040/042 |

Traceability đầy đủ cho từng US được lập bằng cách ghép `US-xxx -> BR-xxx` theo Catalog; cần bổ sung AC/FR/TC sau khi PO trả lời BQ-001 đến BQ-030.

## 10. Acceptance Criteria đề xuất

Chỉ đề xuất AC cho phần actor/action đã được backlog xác nhận. Điều kiện chưa xác nhận được ghi `TBD` và không được coi là AC chính thức.

### AC-001 — Tạo hồ sơ

```text
Given người dùng có role HR
When HR tạo hồ sơ thực tập sinh với dữ liệu hợp lệ theo schema đã chốt
Then hệ thống lưu hồ sơ và liên kết hồ sơ với thực tập sinh tương ứng
And hệ thống từ chối thao tác nếu người dùng không có quyền HR
```

### AC-004 — Upload tài liệu

```text
Given Intern có tài khoản và hồ sơ hợp lệ
When Intern upload CV hoặc đơn xin thực tập theo giới hạn file đã chốt
Then tài liệu được lưu và liên kết với hồ sơ
And tài liệu có thể được HR xem để xác thực
```

### AC-007 — Xét duyệt hồ sơ

```text
Given hồ sơ đã được nộp
And HR có quyền xét duyệt
When HR chọn Approve hoặc Reject
Then hệ thống lưu kết quả xét duyệt gắn với hồ sơ
And hệ thống thực hiện thông báo theo chính sách đã chốt
```

### AC-010 — Xác nhận hợp đồng

```text
Given HR đã tải hợp đồng thuộc về Intern
When Intern xác nhận hợp đồng trong điều kiện hiệu lực đã chốt
Then hệ thống ghi nhận xác nhận của Intern
And thủ tục hợp đồng chuyển sang kết quả đã được chốt
```

### AC-017 — Nộp báo cáo tuần

```text
Given Intern thuộc một chương trình thực tập
When Intern nộp báo cáo cho kỳ tuần hợp lệ
Then báo cáo được lưu, gắn với Intern và kỳ tuần
And Mentor phụ trách có thể xem và phản hồi
```

### AC-021 — Chấm công

```text
Given Intern có lịch làm việc đang áp dụng
When Intern thực hiện check-in hoặc check-out hợp lệ
Then hệ thống ghi nhận thời điểm và Intern tương ứng
And bản ghi xuất hiện trong báo cáo chấm công của HR
```

### AC-028 — Xử lý hỗ trợ

```text
Given Intern đã gửi một yêu cầu hỗ trợ
When HR xử lý yêu cầu theo quyền được cấp
Then hệ thống lưu kết quả và phản hồi
And Intern có thể nhận kết quả theo kênh thông báo đã chốt
```

### AC-037 — Đồng bộ HRM

```text
Given Admin đã cấu hình kết nối và mapping được phê duyệt
When tác vụ đồng bộ được kích hoạt
Then hệ thống đồng bộ dữ liệu theo source of truth đã chốt
And hệ thống ghi nhận lỗi, bản ghi thất bại và khả năng retry
```

### AC-040 — Kiểm tra quyền

```text
Given tài khoản có role và permission đã cấu hình
When tài khoản gọi một chức năng hoặc truy cập một resource
Then hệ thống cho phép hoặc từ chối theo permission và data scope đã chốt
And thao tác thay đổi quyền được ghi audit nếu chính sách audit yêu cầu
```

## 11. Báo cáo cuối cùng

### 11.1. Thống kê rule

| Chỉ số | Kết quả |
|---|---:|
| User Story phân tích | 42 |
| Business Rule trong Catalog | 42 |
| Confirmed | 42 (actor/action/goal được phát biểu trực tiếp; không đồng nghĩa mọi điều kiện đã rõ) |
| Implicit | 6 nhóm rule ẩn xuyên suốt; chưa tách thành ID chính thức |
| Need Clarification | 22 nhóm missing rule và các trường/điều kiện trong detail/state |
| Conflict | 8 potential conflicts/ambiguities; chưa có mâu thuẫn trực tiếp được khẳng định |
| Missing Rules | 22 nhóm |
| Business Rule Questions | 30 |
| Acceptance Criteria hiện có trong nguồn | 0 |

### 11.2. Rule ảnh hưởng cao

- **BR-007 / BR-005 / BR-010:** quyết định hồ sơ, tài liệu và hợp đồng; cần chốt lifecycle, quyền và hiệu lực.
- **BR-012 / BR-019 / BR-021 / BR-024:** quan hệ phân công, đánh giá, chấm công và nghỉ phép; tác động dữ liệu vận hành và báo cáo.
- **BR-033 / BR-034:** công thức báo cáo và quyền xuất dữ liệu; rủi ro sai số và lộ dữ liệu.
- **BR-037 / BR-038:** tích hợp ngoài hệ thống; cần source of truth, idempotency và xử lý lỗi.
- **BR-040 / BR-041 / BR-042:** phân quyền, backup và audit; là nền tảng kiểm soát rủi ro hệ thống.

### 11.3. Việc phải chốt trước Sprint Planning

1. Chốt lifecycle/state và transition của hồ sơ, tài liệu, hợp đồng, chương trình, báo cáo, nghỉ phép, hỗ trợ và đánh giá.
2. Chốt permission matrix và data scope cho Admin, HR, Mentor, Intern.
3. Chốt uniqueness, required fields, upload validation, versioning và dữ liệu được phép sửa/xóa.
4. Chốt approval, reject/re-submit, deadline, timezone và ngoại lệ chấm công/nghỉ phép.
5. Chốt công thức báo cáo, phạm vi export và privacy/masking.
6. Chốt integration contract với HRM và QR/thẻ, bao gồm retry, duplicate, conflict và reconciliation.
7. Chốt backup/audit policy và các AC có thể kiểm thử.

### 11.4. Dependencies giữa Business Rules

```text
BR-039/040 (account + permission)
  -> tất cả rule actor-based

BR-011/013 (program + dates)
  -> BR-012/014/015/017/019/021/023/024

BR-004/005 (documents)
  -> BR-006/007/008/009/010

BR-012 (assignment)
  -> BR-015/018/019/031

BR-021/023/024 (attendance + schedule + leave)
  -> BR-022/033

BR-037/038 (integrations)
  -> BR-021/022/039 và báo cáo liên quan

BR-040/042 (authorization + audit)
  -> mọi thao tác thay đổi hoặc truy cập dữ liệu
```

### 11.5. Kết luận

Backlog đủ để xác nhận **ai muốn làm gì và vì mục tiêu nào**, nhưng chưa đủ để chốt các Business Rule vận hành có thể kiểm thử. Không có conflict trực tiếp được chứng minh từ nguồn; các mục trong phần Conflict là ambiguity cần PO xác nhận. Tài liệu này không biến assumption thành requirement. Sau khi trả lời BQ-001 đến BQ-030, cần cập nhật lại Catalog/State/Traceability và viết AC chính thức cho từng User Story trước khi đưa vào Sprint Planning.
