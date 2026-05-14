---
artifact: 3 — Outline 5 mục cho slide deck Analysis Report
bai-tap: 2 — Phân tích 2 sản phẩm AI (nhóm 2 học viên)
phase: Phase 3 — Dựng slide deck (15 phút)
time: 15 phút outline
input: 1-research-notes.md + 2-comparison-table.md + screenshots/
nop-cuoi: Có gián tiếp — outline này là cốt cho analysis-report.pdf
---

# 3 — Outline 5 mục: Cursor vs GitHub Copilot (Ngành Lập trình)

## Thông tin chung

- **Mã học viên + tên**: 2A202600138 (Nguyễn Bình Thành) — thực hiện cá nhân
- **Ngành chọn**: B — Lập trình
- **Nhiệm vụ chung đã test**: Viết hàm Python tính khoảng cách Levenshtein bằng dynamic programming, có docstring và unit test
- **Sản phẩm A**: Cursor — https://www.cursor.com
- **Sản phẩm B**: GitHub Copilot — https://github.com/features/copilot
- **Câu prompt chính xác đã dùng**: "Viết hàm Python tính khoảng cách Levenshtein giữa 2 chuỗi. Yêu cầu: dùng dynamic programming, có docstring, và viết kèm ít nhất 3 unit test bao phủ trường hợp chuỗi rỗng, chuỗi giống nhau, và chuỗi khác hoàn toàn."

---

## S1 — Product Moment

### S1.1 — Bảng so sánh nhanh

| Yếu tố | Cursor | GitHub Copilot |
|---|---|---|
| Tên + URL | Cursor (cursor.com) | GitHub Copilot (github.com/features/copilot) |
| Entry point | IDE (VS Code fork) → Composer (Ctrl+I) hoặc inline Cmd+K | VS Code sidebar → Copilot Chat sidebar / inline autocomplete |
| Ý định người dùng | Viết / tạo / sửa code mới từ prompt | Hỏi đáp trong khi code + autocomplete liên tục |
| Surface chính | Editor canvas + Composer floating | Sidebar chat + inline suggestions trong editor |
| Cần đăng nhập / paywall ngay | Login bắt buộc; Free tier giới hạn 50 slow requests/tháng | Login GitHub bắt buộc; Free tier có cho students/OSS |

### S1.2 — Bằng chứng

- `screenshots/product-A-1-entry.png` — Composer interface mở trong Cursor, placeholder "Describe changes..."
- `screenshots/product-B-1-entry.png` — Copilot Chat sidebar mở trong VS Code, slash commands hiển thị

### S1.3 — Nhận định so sánh entry point

Cursor tạo first impression "tool đặc biệt cho AI coding" — IDE riêng biệt tập trung 100% vào AI. GitHub Copilot tạo first impression "AI làm đồng hành trong môi trường tôi đã quen" — không cần chuyển IDE. Với developer đang dùng VS Code, Copilot có entry friction thấp hơn nhiều vì không cần cài tool mới; nhưng với developer muốn power features, Cursor rõ ràng là lựa chọn mạnh hơn.

---

## S2 — Workflow Evidence

### S2.1 — Luồng người dùng

```text
TRƯỚC khi gặp AI:
- Developer mở file Python trống, biết muốn implement Levenshtein distance

TRONG khi dùng Cursor:
1. Ctrl+I để mở Composer (floating window)
2. Paste prompt → Enter
3. Đọc code streaming xuất hiện (3-4 giây)
4. Click "Apply" để insert vào file
5. Chạy tests trong terminal tích hợp

TRONG khi dùng Copilot:
1. Click icon Copilot hoặc Ctrl+Alt+I để mở sidebar
2. Paste prompt trong chat box → Enter
3. Đọc code xuất hiện trong sidebar (2-3 giây)
4. Click "Insert at Cursor" hoặc copy code
5. Paste vào file editor, chạy tests

SAU khi dùng AI:
- Đọc, verify, chạy unit tests, sửa nếu cần
- Cursor: sửa trực tiếp trong Composer ("make the tests more comprehensive")
- Copilot: tiếp tục chat trong sidebar ("add a space-optimized version")
```

### S2.2 — 3 Friction Areas

| Friction | Cursor | GitHub Copilot |
|---|---|---|
| **Physical load** (click, tab, copy-paste) | 3 bước: Ctrl+I → prompt → Apply. Ít friction nhất. | 4 bước: mở sidebar → prompt → scroll → Insert. Thêm 1 bước. |
| **Cognitive burden** (prompt eng., context) | Ít — Composer tự detect context file. Không cần nhớ commands. | Có slash commands (/explain, /fix, /test) giúp ích nhưng cần nhớ. |
| **User workarounds** | Với file lớn, đôi khi cần chỉ định vị trí insert rõ hơn. | Phải đảm bảo cursor ở đúng vị trí trong file trước khi "Insert at Cursor". |

### S2.3 — Bằng chứng

- `screenshots/product-A-2-input.png` — prompt đã nhập trong Cursor Composer
- `screenshots/product-A-3-output.png` — code được generate + nút Apply
- `screenshots/product-B-2-input.png` — prompt trong Copilot Chat sidebar
- `screenshots/product-B-3-output.png` — code trong sidebar + disclaimer + follow-up suggestions

### S2.4 — Nhận định: sản phẩm nào giảm friction tốt hơn?

Cursor giảm friction tốt hơn cho task _tạo code mới từ scratch_ — workflow 3 bước với Apply button là workflow mượt nhất hiện tại. GitHub Copilot giảm friction tốt hơn cho task _iteration và hỏi đáp liên tục_ — sidebar persistent, follow-up suggestions, slash commands đều hỗ trợ workflow chat-based. Nếu task là "code mới từ prompt", Cursor thắng; nếu task là "code đang có và cần refactor/debug liên tục", Copilot thắng.

---

## S3 — Output & Trust

### S3.1 — Chất lượng output

- **Cursor**:
  - Output có trả lời đúng câu hỏi chính: Có — hàm đúng, DP implementation chính xác
  - Output có bịa thông tin: Không — code chạy được, unit tests pass
  - Output có đầy đủ: Có (và hơn yêu cầu — 5 tests thay vì 3, thêm time/space complexity)

- **GitHub Copilot**:
  - Output có trả lời đúng câu hỏi chính: Có — hàm đúng, implementation chính xác
  - Output có bịa thông tin: Không — code chạy được, 3 unit tests pass
  - Output có đầy đủ: Đúng yêu cầu (không dư), docstring thiếu complexity analysis

### S3.2 — 6 Tín hiệu đáng tin

| Tín hiệu | Cursor | GitHub Copilot |
|---|---|---|
| 1. Dẫn nguồn (citation) | Không áp dụng (code gen) | Không áp dụng (code gen) |
| 2. Disclaimer khi không chắc | Không — implicit trust | Có — "Copilot uses AI. Check for mistakes." |
| 3. Fallback / dừng khi out-of-scope | Có (báo nếu prompt không rõ) | Có (suggest /explain nếu không hiểu) |
| 4. Consistency (2 lần cùng prompt) | Tương đương — cùng cấu trúc, khác biến tên nhỏ | Tương đương — ổn định |
| 5. User control (sửa, dừng, regenerate) | Apply/Reject; không có 1-click regenerate | Insert/Discard; có regenerate icon |
| 6. Explanation (vì sao AI nói thế) | Không tự giải thích trừ khi hỏi | Follow-up suggestions giải thích thêm ngay |

### S3.3 — Nhận định: sản phẩm nào tạo trust mạnh hơn?

Copilot tạo trust signal rõ hơn nhờ disclaimer nhất quán và follow-up suggestions — developer được nhắc nhở kiểm tra và được gợi ý cải tiến. Cursor tin tưởng developer tự verify, phù hợp với senior developer nhưng có thể nguy hiểm với người mới. Về chất lượng code thực tế, cả 2 đều pass tests — trust về mặt output là tương đương; nhưng trust về mặt UX thì Copilot minh bạch hơn.

---

## S4 — Business Signal

### S4.1 — Định vị tam giác

- **Cursor**: Mạnh-đắt — $20/tháng Pro, dùng model mạnh nhất (claude-3.5-sonnet/GPT-4), multi-file editing (Composer), codebase-aware search. Trade-off: phải fork IDE, phụ thuộc model thứ 3.
- **GitHub Copilot**: Cân bằng — $10/tháng Individual (free cho students/OSS), GPT-4o, tích hợp sâu vào GitHub/VS Code ecosystem. Trade-off: features ít hơn Cursor nhưng friction thấp hơn.

### S4.2 — Pricing pattern

| Yếu tố | Cursor | GitHub Copilot |
|---|---|---|
| Mô hình giá | Seat-based (Free / Pro / Business) | Seat-based (Free / Individual / Business / Enterprise) |
| Giá entry (free tier giới hạn gì) | Free: 50 slow requests/tháng, không có Composer | Free: sinh viên/OSS developers (verify required); 2000 completions/tháng cho all users (2024) |
| Giá trả phí (gói chính) | Pro: $20/tháng — unlimited requests, fast model | Individual: $10/tháng; Business: $19/user/tháng; Enterprise: $39/user/tháng |
| Paywall xuất hiện ở đâu | Khi hết slow request quota hoặc dùng Composer / fast model | Khi hết free completion quota hoặc cần Copilot Chat trên GitHub.com |

### S4.3 — Nhận định: chiến lược kinh doanh 2 sản phẩm khác nhau thế nào?

Cursor đang theo chiến lược "land & expand" — thu hút individual dev trước với Free tier, chuyển lên Pro khi thấy giá trị, sau đó scale lên Business cho team. GitHub Copilot theo chiến lược "distribution moat" — miễn phí cho sinh viên (xây thói quen sớm), bundle vào GitHub/Microsoft 365 để tăng adoption doanh nghiệp. Cursor cạnh tranh bằng product superiority; Copilot cạnh tranh bằng ecosystem lock-in.

---

## S5 — Product Judgment

### S5.1 — Verdict (BẮT BUỘC)

- **Cursor**: **Promising** — Tăng trưởng nhanh (báo cáo $100M+ ARR 2024), UX vượt trội cho AI-first coding, nhưng rủi ro "rented land" (phụ thuộc VS Code codebase + model thứ 3) và chưa có moat bền vững khi big tech copy tính năng.
- **GitHub Copilot**: **Strong** — Distribution moat cực mạnh (GitHub = 100M+ developers, Microsoft backing), tích hợp sâu vào workflow không thể thay thế nhanh, 1.8M+ paid subscribers, pricing reasonable. Rủi ro: autocomplete feature có thể bị commoditized.

### S5.2 — User base + tăng trưởng

- **Cursor**: ~$100M+ ARR được báo cáo vào cuối 2024 (Bloomberg, Dec 2024); valuation $2.5B (funding round 2024); số user paid chính xác không công bố công khai. Tăng trưởng: ARR tăng từ gần 0 lên $100M trong vòng ~18 tháng — tốc độ hiếm thấy. Nguồn: Bloomberg Dec 2024, TechCrunch funding articles.
- **GitHub Copilot**: 1.8M+ paid subscribers (Jan 2024, GitHub Universe announcement); ~30% doanh nghiệp Fortune 500 đang dùng (Microsoft Q1 FY2024 earnings); GitHub có 100M+ developers là potential user base. Nguồn: GitHub blog Jan 2024, Microsoft earnings call.

### S5.3 — Doanh thu / pricing power

- **Cursor**: $100M+ ARR (2024, ước tính); không có số chính thức (startup tư nhân). Pricing: Pro $20/tháng — cao hơn Copilot nhưng justified bởi capabilities. Chiến lược: freemium → Pro → Business.
- **GitHub Copilot**: Revenue được gộp trong GitHub/Microsoft — ước tính ~$200M+ ARR dựa trên 1.8M paid × $10 average (thực tế higher với Business/Enterprise tier). Microsoft không công bố riêng. Chiến lược: ecosystem bundle, student free để lock-in.

### S5.4 — Moat phân tích

| Moat | Cursor | GitHub Copilot |
|---|---|---|
| Data (proprietary flywheel) | Yếu — dùng data từ OpenAI/Anthropic, không có exclusive data | Mạnh — GitHub có lượng code public lớn nhất thế giới; dùng để train Codex/model |
| Network effects | Yếu — developer dùng độc lập, không tạo giá trị cho người khác | Trung bình — PR review Copilot có network effect khi cả team dùng |
| Switching cost | Trung bình — phải đổi IDE + re-learn Composer workflow | Mạnh — tích hợp vào GitHub PR/Issues/Actions; workflow team; enterprise SSO |
| Brand | Trung bình — "Cursor = AI coding" đang xây dựng nhanh | Mạnh — "Copilot" = AI assistant trong tâm trí developer (established) |
| Distribution | Yếu — phải download Cursor IDE riêng | Rất mạnh — GitHub 100M users, VS Code marketplace, Microsoft enterprise sales |

### S5.5 — Data flywheel + feedback loop

- **Cursor**: User code trong Cursor → Cursor có thể học pattern nào hiệu quả → improve suggestions theo codebase context. Nhưng model chính (Claude/GPT-4) được train bởi Anthropic/OpenAI, không phải Cursor. Loop không compounding mạnh vì Cursor không own model.
- **GitHub Copilot**: Developer code với Copilot → accept/reject suggestions → GitHub biết suggestion nào được chấp nhận → improve model. Loop có compounding: nhiều developer → nhiều signal → better suggestions → nhiều developer hơn. Đây là data flywheel thực sự vì GitHub own training pipeline (Codex → GPT-based).

### S5.6 — Niche Down + AI Feature Map (BẮT BUỘC)

- **Cursor**:
  - Niche cụ thể: Developer muốn AI-first workflow — coi AI như pair programmer, không chỉ là autocomplete. Target: indie developer, startup team, senior dev muốn productivity cao nhất.
  - AI Feature Map:
    - User Value: **Cao** — giảm đáng kể thời gian viết boilerplate, refactor, debug (tiết kiệm 30-50% thời gian theo user testimonials)
    - User Alignment: **Cao** — developer chọn dùng Cursor chủ động, không bị imposed
    - Business Value: **Cao** — $20/tháng Pro, tăng trưởng nhanh → strong unit economics

- **GitHub Copilot**:
  - Niche cụ thể: Developer đang dùng GitHub ecosystem — cần AI không friction, tích hợp vào workflow hiện có. Target: enterprise developer, team dùng GitHub cho CI/CD, sinh viên CS.
  - AI Feature Map:
    - User Value: **Cao** — autocomplete liên tục tiết kiệm nhiều keystrokes; Copilot Chat giúp explain/fix nhanh
    - User Alignment: **Cao** — Microsoft/GitHub push adoption nhưng developer genuinely find it useful
    - Business Value: **Rất cao** — lock-in vào GitHub ecosystem, enterprise pricing tier, Microsoft cross-sell

### S5.7 — Spark → Loop → System (BẮT BUỘC)

- **Cursor**: Đang ở giai đoạn **Loop** — đã có Spark (WOW moment khi dùng Composer lần đầu), đang build Loop (developer quay lại mỗi ngày, ARR tăng nhanh). Chưa đến System vì chưa có moat bền vững (phụ thuộc model thứ 3, chưa có network effect rõ). Dự báo 12 tháng: sẽ đẩy mạnh team collaboration features (Cursor Teams) để build switching cost → move toward System. Rủi ro: VS Code (Microsoft) có thể copy tính năng Composer trực tiếp.

- **GitHub Copilot**: Đang ở giai đoạn **System** — đã có Spark (2021 launch), đã có Loop (1.8M+ paid, enterprise adoption), đang build System (tích hợp sâu vào GitHub PR review, Actions, GHAS). Distribution moat + data flywheel đang compound. Dự báo 12 tháng: mở rộng sang agentic coding (GitHub Copilot Workspace — multi-file, multi-step task automation), cạnh tranh trực tiếp với Cursor ở tier cao hơn.

### S5.8 — Liên hệ Lab 1 (BẮT BUỘC)

**Từ Lab 1 của Nguyễn Bình Thành (case Chegg):**

- **Cursor có rủi ro disruption-style tương tự Chegg không?**
  Có — Cursor đang xây sản phẩm trên "rented land" (dùng VS Code codebase fork + model của Anthropic/OpenAI). Nếu Microsoft/VS Code ra Composer-equivalent trực tiếp trong VS Code, Cursor mất distribution advantage ngay — giống Chegg bị ChatGPT copy core value. Switching cost hiện tại = phải đổi IDE, nhưng nếu VS Code native AI bắt kịp, switching cost biến mất.

- **Copilot có rủi ro disruption tương tự không?**
  Ít hơn Cursor — Copilot có distribution moat (GitHub), data moat (code training data), và switching cost thực (team workflow, enterprise SSO). Rủi ro: nếu Cursor hoặc một startup khác build agent AI coding mạnh hơn nhiều, Copilot có thể bị "feature commoditized" ở autocomplete tier giống Chegg bị ChatGPT ở homework answer tier.

- **Bài học từ Lab 1 áp dụng cho 2 sản phẩm này:**
  (1) Cursor cần tạo data flywheel riêng (không phụ thuộc model thứ 3) trước khi big tech copy — giống như Chegg đáng lẽ phải xây learning profile data moat trước ChatGPT. (2) Sản phẩm AI wrapper (không own model, không own data) sẽ bị disrupt nhanh khi better alternative xuất hiện — Cursor đang ở vị trí này nếu không build moat kỹ thuật. (3) Distribution moat (như Copilot có với GitHub) mạnh hơn brand moat (như Chegg có) khi đối mặt với big tech disruption — Chegg đã chứng minh brand không đủ, Copilot đang chứng minh distribution bền hơn.

---

## Bảng kiểm trước khi build slide

- [x] S1 → S4 đã điền đầy đủ
- [x] S5.1 Verdict: Cursor = Promising, Copilot = Strong (nhất quán với phân tích)
- [x] S5.6 Niche + AI Feature Map: đã hoàn thành
- [x] S5.7 Spark→Loop→System: đã hoàn thành
- [x] S5.8 Liên hệ Lab 1 Chegg case: đã hoàn thành
- [x] S5.2–S5.5: đã có số liệu hoặc ghi rõ "không có nguồn công khai"
- [x] Mỗi nhận định có thể chỉ về log/screenshot
- [x] Verdict S5.1 nhất quán với moat S5.4 và giai đoạn S5.7
- [x] Học viên xác nhận outline này

---

## Ghi chú export

Slide deck cần export thành `analysis-report.pdf`. Nếu dùng Google Slides, lưu link công khai vào `analysis-report-link.md`.
