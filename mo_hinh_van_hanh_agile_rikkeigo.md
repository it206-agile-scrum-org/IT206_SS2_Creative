# MÔ HÌNH VẬN HÀNH AGILE CHO TOÀN MẢNG RIKKEIGO

**Vai trò:** Agile Lead
**Phạm vi:** 3 đội sản phẩm — **Đặt xe**, **Thanh toán** (yêu cầu thay đổi liên tục) và **Đối soát** (yêu cầu ổn định, tuân thủ quy định thuế).

**Giả định:** Mỗi đội có 5–9 người, làm việc theo Sprint 2 tuần, bắt đầu và kết thúc cùng ngày để cả mảng có chung một nhịp.

---

## PHẦN 1 – KIẾN TRÚC MÔ HÌNH

### 1.1. Danh sách module quy trình

| # | Module | Nội dung | Chủ sở hữu (trách nhiệm chính) |
|---|--------|----------|-------------------------------|
| M1 | **Nền tảng giá trị** | 4 giá trị Agile (cá nhân & tương tác; phần mềm chạy được; hợp tác với khách hàng; phản hồi thay đổi) và 3 trụ cột Scrum (Minh bạch – Thanh tra – Thích nghi) làm "kim chỉ nam" khi ra quyết định. | Cả đội; Agile Lead gìn giữ |
| M2 | **Nhịp Sprint chung** | Sprint 2 tuần, **timebox cố định, không kéo dài, không rút ngắn riêng lẻ**. Sprint là khung chứa 4 sự kiện còn lại. | Scrum Master mỗi đội |
| M3 | **Phân vai** | 3 vai trò Scrum: **Product Owner (PO)** – quyết định *làm gì, thứ tự nào*, chấp nhận Increment; **Scrum Master (SM)** – bảo vệ quy trình, gỡ cản trở; **Developers** – quyết định *làm thế nào*, tự cam kết Sprint Goal và tạo Increment. Mỗi đội có 1 PO, 1 SM riêng. *Agile Lead không phải vai trò Scrum*: chỉ duy trì mô hình chung, không ra quyết định thay PO hay Developers. | PO / SM / Developers |
| M4 | **Artifacts & cam kết** | **Product Backlog** ↔ cam kết *Product Goal*; **Sprint Backlog** ↔ cam kết *Sprint Goal*; **Increment** ↔ cam kết *Definition of Done (DoD)*. | PO (PB), Developers (SB, Increment) |
| M5 | **5 sự kiện Scrum** | Sprint • Sprint Planning (≤ 4h) • Daily Scrum (15 phút) • Sprint Review (≤ 2h) • Sprint Retrospective (≤ 1.5h). | SM tổ chức; PO/Developers tham gia |
| M6 | **Chuẩn "Xong" (DoD)** | **DoD chung toàn mảng**: code review, test tự động đạt, tích hợp được, chạy trên môi trường staging, có thể phát hành. Mỗi đội được **bổ sung** (không được giảm) điều kiện riêng. | Developers; Agile Lead rà soát |
| M7 | **Vòng phản hồi & cải tiến** | Phản hồi người dùng/stakeholder tại Review → PO cập nhật Product Backlog. Hành động cải tiến từ Retro → đưa vào Sprint Backlog kế tiếp (ít nhất 1 hạng mục). Agile Lead tổng hợp xu hướng chung cho cả mảng mỗi 2 Sprint. | PO (phản hồi), Developers + SM (cải tiến) |

*Phân tách trách nhiệm:* quyết định **thứ tự ưu tiên** chỉ thuộc PO; **ước lượng và cách làm** chỉ thuộc Developers; **quy trình** thuộc SM; **chuẩn chất lượng chung** thuộc DoD (M6) – không module nào lấn sang phần của module khác.

### 1.2. Đội Đối soát có áp dụng mô hình chung không?

**Có – áp dụng khung chung** (cùng nhịp Sprint 2 tuần, 3 vai trò, 3 Artifacts, 5 sự kiện, DoD chung) vì tính minh bạch, kiểm tra định kỳ và cải tiến liên tục có giá trị với mọi đội, kể cả khi yêu cầu ổn định. **Chỉ tùy biến phần nội dung:** DoD bổ sung điều kiện "đối chiếu quy định thuế & có người kế toán/thuế xác nhận", Product Backlog ít biến động trong Sprint, và Sprint Review có mời chuyên gia thuế.

### 1.3. Luồng giá trị (khép kín)

```
Nhu cầu người dùng / Quy định thuế / Phản hồi thị trường
        │
        ▼
Product Backlog (PO sắp xếp theo giá trị, hướng tới Product Goal)
        │
        ▼
Sprint Planning ──► Sprint Goal + Sprint Backlog
        │
        ▼
Sprint 2 tuần  ◄── Daily Scrum (mỗi ngày: kiểm tra tiến độ, điều chỉnh kế hoạch)
        │
        ▼
Increment (đạt DoD) ──► có thể phát hành
        │
        ▼
Sprint Review (demo + thu phản hồi từ người dùng/stakeholder)
        │                              │
        │                              └──► phản hồi quay lại Product Backlog (vòng 1)
        ▼
Sprint Retrospective (cải tiến cách làm: người – quy trình – công cụ)
        │
        └──► hành động cải tiến đưa vào Sprint Planning kế tiếp (vòng 2)
```

- **Vòng phản hồi sản phẩm (vòng 1):** Review → Product Backlog → Planning.
- **Vòng cải tiến quy trình (vòng 2):** Retro → Sprint Backlog kế tiếp.
- **Vòng điều chỉnh mảng (vòng 3):** Agile Lead tổng hợp Retro của 3 đội mỗi 2 Sprint, cập nhật DoD chung nếu cần.

---

## PHẦN 2 – XỬ LÝ TÌNH HUỐNG NGOÀI DỰ KIẾN

### Tình huống 1: Đến Sprint Review nhưng không có hạng mục nào đạt "xong"

| Nội dung | Cách xử lý |
|----------|-----------|
| **Phát hiện ở đâu** | Dấu hiệu sớm tại **Daily Scrum** (hạng mục dồn vào cuối Sprint, chưa qua test); xác nhận chính thức tại **Sprint Review** khi PO/Developers đối chiếu với DoD. |
| **Ai xử lý** | **PO** quyết định không chấp nhận Increment và sắp xếp lại backlog; **Developers** trình bày trung thực; **SM** dẫn dắt Retro tìm nguyên nhân gốc; **Agile Lead** theo dõi nếu lặp lại. |
| **Xử lý thế nào** | (1) **Vẫn tổ chức Review đúng timebox** – trình bày tình trạng thật, không demo phần "gần xong" như đã xong (giữ **Minh bạch**), nhưng vẫn thu phản hồi về phần dở dang. (2) Các hạng mục chưa xong **quay về Product Backlog**, PO xếp lại thứ tự theo giá trị. (3) **Retro** tập trung nguyên nhân: hạng mục quá lớn? DoD chưa rõ? phụ thuộc bên ngoài? (4) **Planning kế tiếp** cắt nhỏ hạng mục, giảm cam kết xuống mức thực tế. (5) Nếu xảy ra **2 Sprint liên tiếp**, Agile Lead cùng SM rà soát lại cách chia nhỏ backlog và năng lực/cản trở của đội. |

*Tinh thần giữ nguyên:* không nới DoD, không "đánh dấu xong" cho đẹp, không đổ lỗi cá nhân – coi đây là dữ liệu để **Thích nghi**.

### Tình huống 2: Đội Thanh toán muốn kéo dài riêng Sprint thêm 1 tuần

| Nội dung | Cách xử lý |
|----------|-----------|
| **Phát hiện ở đâu** | Tại **Daily Scrum** (khoảng giữa/cuối Sprint) khi Developers thấy Sprint Goal có nguy cơ không đạt; đề xuất được nêu với SM và PO. |
| **Ai xử lý** | **SM** của đội Thanh toán giữ nguyên nguyên tắc timebox; **PO** quyết định điều chỉnh phạm vi; **Developers** đề xuất phần cắt; **Agile Lead** chỉ hỗ trợ, không tự quyết thay đội. |
| **Xử lý thế nào** | (1) **Từ chối kéo dài Sprint**: Sprint là timebox cố định; kéo dài riêng làm lệch nhịp với các đội khác và làm mất ý nghĩa kiểm tra – thích nghi định kỳ. (2) Thay vào đó, **Developers cùng PO thương lượng lại phạm vi** (không đổi Sprint Goal nếu còn đạt được): cắt hạng mục nhỏ ra khỏi Sprint, giữ phần quan trọng nhất. (3) **Phần chưa xong** quay về Product Backlog, PO quyết định ưu tiên cho Sprint kế tiếp (có thể đứng đầu). (4) Nếu Sprint Goal **không còn giá trị** (ví dụ yêu cầu thay đổi lớn), chỉ **PO** có quyền **hủy Sprint**, rồi họp Planning mới. (5) **Retro** xem lại vì sao ước lượng sai để lần sau chia nhỏ tốt hơn. |

*Tinh thần giữ nguyên:* "làm cho xong" không có nghĩa là kéo dài thời gian; **phản hồi thay đổi** được đáp ứng bằng cách điều chỉnh phạm vi, không phá nhịp chung.

---

## KẾT LUẬN

Mô hình gồm **7 module** có trách nhiệm tách bạch, một **luồng giá trị khép kín** với 3 vòng phản hồi/cải tiến, áp dụng thống nhất cho cả 3 đội (Đối soát tùy biến DoD và nội dung backlog nhưng giữ khung chung), và có cách xử lý cụ thể cho cả hai tình huống ngoài dự kiến mà vẫn giữ đúng tinh thần Agile và Scrum.
