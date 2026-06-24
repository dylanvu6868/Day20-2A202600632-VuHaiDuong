# BÁO CÁO LAB DAY 20: RETENTION, ENGAGEMENT & HABIT LOOP
## HỌ VÀ TÊN: VŨ HẢI DƯƠNG
## MÃ SỐ SINH VIÊN: 2A202600632
## ĐỀ TÀI: BUDGETBUDDY AI (TRACK 1 · AI PERSONAL ASSISTANT FOR STUDENTS)

---

## 1. Giới thiệu chung & Định hướng sản phẩm
**BudgetBuddy AI** là trợ lý quản lý tài chính cá nhân dành riêng cho sinh viên đại học, được thiết kế để giải quyết bài toán stress tài chính và mất kiểm soát chi tiêu thông qua việc tự động phát hiện, phân loại giao dịch từ SMS ngân hàng/ví điện tử, lập kế hoạch ngân sách và đề xuất insight tiêu dùng tối ưu.

Sản phẩm kế thừa các nguyên lý thiết kế **Human-Centered AI (HCAI)** của Day 18 (thiết kế minh bạch explainability, ranh giới quyền lực Act/Ask/Don't Act, vòng lặp recovery sửa sai) và tích hợp các phân tích chuyên sâu về **Retention, Engagement, Habit Loop** của Day 20 để tối ưu hóa phễu Onboarding và gia tăng tỷ lệ giữ chân người dùng (Retention Rate).

---

## 2. Chi tiết 12 Nội dung Phân tích & Thiết kế (Day 20)

### 01 · Customer Retention Canvas (Use Case & Persona)
* **The Problem (Bằng lời của User):** *"Tôi không biết tiền mình đi đâu, cuối tháng luôn thiếu và phải đi vay mượn. Các tin nhắn SMS biến động số dư quá nhiều khiến tôi lười đọc và thống kê thủ công."*
* **Persona (Minh - Sinh viên năm 1-2):** Sống xa nhà, tự quản lý chi tiêu trong ngân sách gia đình gửi hàng tháng (~3-5 triệu VND). Thói quen chi tiêu chưa định hình, dễ bị cám dỗ bởi các chi phí phát sinh như trà sữa, tụ tập bạn bè, mua sắm ngẫu hứng.
* **Anti-Persona:** Sinh viên có hoàn cảnh tài chính quá dư dả không cần quản lý chi tiêu, hoặc người đi làm đã có thu nhập cao ổn định và quy trình quản lý tài chính chuyên nghiệp (dùng Excel hoặc app trả phí khác).
* **The Why (Động lực cốt lõi):** Giảm bớt stress tài chính cuối tháng, tự chủ chi tiêu để có tiền tiết kiệm cho các dự án cá nhân (học ngoại ngữ, mua máy tính).
* **The Alternative:** Ghi chú thủ công ra sổ/Excel (thường bỏ dở sau 3 ngày), đọc lại lịch sử giao dịch SMS ngân hàng khi sắp hết tiền, hoặc chấp nhận sống thiếu kiểm soát.
* **The Frequency (Tần suất tự nhiên):** **Daily (Hàng ngày)** — Giao dịch chi tiêu ăn uống, đi lại xảy ra hàng ngày và nhu cầu kiểm tra ngân sách xuất hiện liên tục.

### 02 · Core Action & định nghĩa Active User
* **Core Job:** Giúp sinh viên nắm rõ bức tranh tài chính cá nhân của họ hiện tại.
* **Core Action:** **Xem báo cáo chi tiêu đã phân loại (Spending Report View)**. Đây là hành vi mang lại giá trị thực (Aha Moment) khi người dùng thấy rõ tỷ lệ phân bổ dòng tiền và cảnh báo ngân sách.
* **Active User Definition:** Một người dùng được tính là Active User trong ngày khi **xem báo cáo chi tiêu ít nhất 1 lần/ngày**.
* *Lý do:* Không tính lượt mở app (App Open) thuần túy vì mở app mà không tương tác với số liệu chi tiêu thì chưa nhận được giá trị thực của sản phẩm.

### 03 · Natural Frequency & Retention Metric
* **Natural Frequency:** Daily (Hàng ngày).
* **Retention Metrics được chọn:**
  * **D1 Retention:** Đo lường tỷ lệ tạo thói quen ban đầu ngay ngày đầu tiên sau Onboarding.
  * **D7 Retention (Metric chính):** Đo lường tỷ lệ giữ chân ngắn hạn sau 1 tuần.
  * **D30 Retention:** Đo lường sức khỏe giữ chân dài hạn.
  * **DAU/MAU (Stickiness Metric):** Đánh giá mức độ gắn bó hàng ngày của người dùng.
* *Phân đoạn mùa vụ (Seasonality Segment):* Đo lường retention cần tách biệt giai đoạn **Đầu tháng** (vừa nhận tiền trợ cấp từ gia đình) và **Cuối tháng** (ngân sách cạn kiệt, cần kiểm soát gắt gao).

### 04 · Onboarding Audit (Đánh giá quy trình cũ)
* **Onboarding cũ (Ngày 18):** Gồm 6 bước kéo dài: Product Tour (3 bước) → Giải thích ranh giới AI → Xin quyền SMS → Nhập thông tin/Kết nối → Xem báo cáo.
* **Friction & Drop-off Points:**
  * Xin quyền SMS quá sớm khi user chưa thấy giá trị sản phẩm.
  * Product Tour chứa quá nhiều text khiến người dùng bỏ qua (Drop-off Rate ước tính ~50%).
  * **Time to First Core Action (TTFC):** ~2 phút.
  * **Time to Value (TTV):** ~3 phút.

### 05 · Redesigned Onboarding (Quy trình tối ưu mới)
Quy trình mới rút ngắn xuống **3 bước nhanh gọn** nhằm đạt **Time to Value nhanh nhất**:
1. **Welcome Screen (15s):** Giải thích ngắn gọn 1 câu giá trị cốt lõi và nút "Thử ngay".
2. **Interactive Input Screen (20s):** Nhập 1 khoản chi demo (Ví dụ: Trà sữa 50,000đ).
3. **Instant Report Screen (10s):** Hiển thị ngay báo cáo chi tiêu và đề xuất insight đầu tiên (TTV đạt được trong 45 giây).
* **Delaying Permissions:** Dịch chuyển yêu cầu cấp quyền đọc SMS ra sau màn hình báo cáo đầu tiên (sau khi user đã hiểu sản phẩm hoạt động như thế nào).
* **No-data Recovery Path:** Nếu user từ chối cấp quyền SMS, chuyển hướng mượt mà sang chế độ nhập thủ công (Manual Mode) hoặc nạp dữ liệu mẫu (Sample Mode), đảm bảo không chặn đứng trải nghiệm của user.

### 06 · So sánh Before / After (Bảng cải tiến)
| Tiêu chí | Trước cải tiến (Day 18) | Sau cải tiến (Day 20) | Lý do thay đổi & Rationale |
| :--- | :--- | :--- | :--- |
| **Số bước tới Core Action** | 6 bước | 3 bước | Cắt bỏ Product Tour rườm rà, tập trung đưa user hành động ngay. |
| **Quyền truy cập trước Core Action** | Yêu cầu kết nối SMS ngay | Không yêu cầu (Cho phép dùng sample/nhập tay) | Giảm e ngại bảo mật quyền riêng tư của người dùng mới. |
| **Time to Value (TTV)** | ~3 phút | **≤ 45 giây** | Tăng xác suất kích hoạt (Activation Rate) thông qua instant gratification. |
| **Báo cáo ban đầu** | Trống rỗng (No data) | Hiển thị dữ liệu mẫu/khoản chi demo | Tránh trải nghiệm "lạnh" khi mở app chưa có giao dịch. |
| **Recovery Path** | Sửa sai sau khi đã vào app | Đưa inline ngay trên màn hình demo và review | Xử lý lỗi AI gán sai danh mục ngay lập tức để xây dựng lòng tin. |

### 07 · Measurement Ladder
1. **Marketing / Traffic:** Số lượt tải app từ các kênh sinh viên (Group Facebook, CLB).
2. **Qualified Visitor:** User mở app và bắt đầu Onboarding.
3. **Activation:** User hoàn thành nhập khoản chi đầu tiên và nhận insight báo cáo đầu tiên.
4. **Core Action:** Tần suất xem báo cáo chi tiêu (Daily).
5. **Retention:** Tỷ lệ D1, D7, D30 Retention.
6. **Revenue:** Tỷ lệ chuyển đổi nâng cấp tài khoản VIP (Premium) để tự động hóa hoàn toàn các tài khoản ngân hàng.

### 08 · North Star Metric & Input Metrics
* **North Star Metric:** **Daily Active Users who View Spending Report (DAU-Report)** — Số người dùng xem báo cáo chi tiêu ít nhất 1 lần trong ngày.
* **Input Metrics (3 lever chính để tác động North Star):**
  1. **Activation Rate:** Tỷ lệ người dùng kích hoạt thành công trong phiên đầu tiên.
  2. **Median Time to Value (TTV):** Rút ngắn thời gian chạm mốc Aha Moment.
  3. **D7 Retention Rate:** Tỷ lệ người dùng duy trì thói quen sau 1 tuần.
* **Trade-off & Guardrail Metrics:** Cảnh báo chi tiêu (Push notification) gửi quá nhiều sẽ làm tăng DAU-Report ngắn hạn nhưng dễ khiến user tắt thông báo. *Guardrail Metric:* **Notification Opt-out Rate** (Tỷ lệ tắt thông báo) và **Uninstall Rate** phải duy trì dưới mức cho phép.

### 09 · Nature vs Nurture
* **Nature (Nhịp tự nhiên):** Nhu cầu kiểm tra tiền phát sinh hàng ngày sau mỗi giao dịch chi tiêu thực tế.
* **Nurture (Tác động nuôi dưỡng):**
  * Gửi **Daily Push Notification** vào cuối ngày (21:00) nhắc nhở rà soát chi tiêu.
  * Gửi **Weekly Financial Digest** vào Chủ nhật thống kê tuần qua kèm so sánh ngân sách.
  * Chỉ trigger thông báo khẩn cấp khi ví tiền chạm ngưỡng cảnh báo (dưới 10% ngân sách tuần).

### 10 · Hook Model (Vòng lặp thói quen)
* **Trigger:**
  * *Internal:* Cảm giác bất an, mơ hồ không biết mình còn bao nhiêu tiền tiêu.
  * *External:* Thông báo biến động số dư SMS hoặc thông báo đẩy nhắc nhở của BudgetBuddy.
* **Action:** Mở app và xem màn hình Báo cáo tổng quan chi tiêu (thao tác tối giản chỉ mất 2 giây).
* **Variable Reward (The Self):** Cảm giác an tâm, tự chủ tài chính khi thấy ngân sách vẫn trong tầm kiểm soát; cảm giác vui mừng khi tiết kiệm được nhiều hơn dự kiến.
* **Investment:** Dữ liệu chi tiêu lịch sử (càng dùng lâu dữ liệu càng chính xác, AI phân loại càng chuẩn và báo cáo càng chi tiết, tạo chi phí cơ hội chuyển đổi nền tảng cao).

### 11 · Metric Tracking Requirement (Yêu cầu Tracking)
* **Event Mapping:**
  * `onboarding_started`: Ghi khi user mở Welcome Screen (chống trùng bằng `flow_instance_id`).
  * `permission_result`: Ghi lựa chọn SMS connection (`allowed` hoặc `denied`).
  * `expense_added`: Ghi khi khoản chi mới được ghi nhận (Manual/SMS).
  * `report_viewed`: Ghi khi user xem màn hình báo cáo chi tiêu (Debounce 5 phút để tránh spam log).
  * `insight_received`: Ghi khi insight được render thành công trên thiết bị của user.
* **Privacy Guard:** Tuyệt đối không thu thập nội dung tin nhắn SMS đầy đủ hoặc thông tin số tài khoản ngân hàng nhạy cảm vào database phân tích.

### 12 · Demo Path (Kịch bản trình bày 8 phút)
* **0:00 - 1:00:** Trình bày Use Case, Persona và Natural Frequency từ Customer Retention Canvas (Mục 01).
* **1:00 - 1:50:** Giải thích Core Action (Xem báo cáo) và lý do từ chối metric App Open (Mục 02).
* **1:50 - 2:40:** Phân tích Retention Metric và lý do chọn Cadence hàng ngày (Mục 03).
* **2:40 - 4:20:** Trình bày Onboarding cũ, phân tích Friction và chạy thử demo Onboarding mới trên Prototype để chứng minh TTV giảm từ 3 phút xuống 45 giây (Mục 04, 05).
* **4:20 - 5:15:** Giới thiệu North Star Metric (DAU-Report) và Input Metrics (Mục 08).
* **5:15 - 6:20:** Trình bày chiến lược Nature vs Nurture và mô hình Hook Model (Mục 09, 10).
* **6:20 - 7:15:** Trình bày yêu cầu Metric Tracking và các tiêu chí an toàn dữ liệu (Mục 11).
* **7:15 - 8:00:** Tổng kết so sánh Before/After và quyết định trì hoãn cấp quyền (Delaying Permissions) (Mục 06, chạy thử demo Recovery S6 trên Prototype).

---

## 3. Hướng dẫn trải nghiệm Prototype
Tệp prototype tương tác hoàn chỉnh đã được xây dựng tại: [lab_day20.html](file:///e:/AI20K/Lab&Lessons/Day20/lab_day20.html)

### Các tính năng chính của Prototype:
1. **Giao diện Hài hòa - Responsive:** Thừa hưởng hệ thống thiết kế hiện đại, tinh tế từ `index_demo.html` (chữ Serif Cambria sang trọng, màu sắc phân cấp rõ ràng, sidebar tiện dụng).
2. **Interactive Phone Demo (Page 05):**
   * Cho phép đi từ Welcome Screen → Nhập khoản chi demo (tùy chọn Trà sữa, Ăn uống, Đi lại, Giải trí và số tiền) → Xem báo cáo trực quan với tổng tiền cập nhật động → Xem insight Aha Moment.
   * Tiếp tục dẫn hướng sang **Thiết lập nâng cao** (Trì hoãn cấp quyền SMS) → Báo cáo trạng thái permission kết nối → Đi tới màn hình **Habit Loop** (Thống kê chuỗi 7 ngày liên tiếp xem báo cáo hàng ngày).
   * **Live Event Log:** Hộp console hiển thị thời gian thực các sự kiện phân tích (`onboarding_started`, `expense_added`, `report_viewed`, `permission_result`, `habit_loop_entered`) được gửi đi khi user thao tác trên điện thoại ảo.
3. **Interactive Recovery Path (Page 06):**
   * Mô phỏng kịch bản khôi phục lỗi khi AI phân loại nhầm danh mục chi tiêu (Sửa từ "Giải trí" thành "Ăn uống" và tiến hành rà soát các khoản chi liên đới).
#
