---
artifact: 2 — Bảng so sánh 2 sản phẩm theo 5 mục
bai-tap: 2 — Phân tích 2 sản phẩm AI (nhóm 2 học viên)
phase: Chuyển giao Phase 2 → Phase 3 (5 phút)
time: 5 phút
input: 1-research-notes.md + screenshots/
nop-cuoi: Không — file trung gian
---

# 2 — Bảng so sánh Cursor vs GitHub Copilot theo 5 mục slide deck

## Phần A — Bảng so sánh 5 mục

| Mục | Cursor (Sản phẩm A) | GitHub Copilot (Sản phẩm B) |
|---|---|---|
| **S1 — Product Moment**<br><sup>Entry point + ý định người dùng + surface chính</sup> | IDE-first (VS Code fork). Entry qua Composer (Ctrl+I) hoặc inline Cmd+K. Surface: editor canvas + floating Composer. Ý định: viết/sửa/tạo code mới. | Sidebar chat trong VS Code/GitHub. Entry qua Copilot Chat sidebar. Surface: chat sidebar + inline autocomplete. Ý định: hỏi đáp + autocomplete liên tục. |
| **S2 — Workflow Evidence**<br><sup>Trước/trong/sau AI. Friction chính.</sup> | Trước: mở file Python trống. Trong: Ctrl+I → paste prompt → Apply (1 click insert). Sau: chạy tests ngay trong terminal. Friction: phải dùng Composer riêng cho task tạo mới, khác với autocomplete. | Trước: mở file Python trống. Trong: mở sidebar → paste prompt → copy/Insert at Cursor. Sau: kiểm tra code. Friction: sidebar nhỏ gây scroll nhiều; insert code cần thêm 1 bước so với Cursor. |
| **S3 — Output & Trust**<br><sup>Chất lượng + citation + disclaimer + control</sup> | Code đúng, có docstring đầy đủ kèm Time/Space complexity. Không có disclaimer. Không cite source. 5 unit tests (hơn yêu cầu). | Code đúng, docstring tốt nhưng thiếu complexity analysis. Có disclaimer "Check for mistakes." Có follow-up suggestions. 3 unit tests (đúng yêu cầu). |
| **S4 — Business Signal**<br><sup>Pricing + giới hạn + Cost-Capability-Speed</sup> | Pro $20/tháng. Free tier giới hạn 50 slow requests/tháng. Định vị: mạnh-toàn diện. Model: claude-3.5-sonnet / GPT-4. Rào cản: phải dùng Cursor IDE (không phải extension). | Individual $10/tháng. Free cho students/open source. Business $19/tháng. Định vị: rẻ-tích hợp sâu vào GitHub ecosystem. Model: GPT-4o. Tích hợp trực tiếp với GitHub PR review. |
| **S5 — Product Judgment**<br><sup>Verdict 1 dòng</sup> | **Promising** — Tăng trưởng cực nhanh ($100M+ ARR), UX vượt trội cho code generation, nhưng còn phụ thuộc model bên thứ 3 và phải fork VS Code nên có rủi ro "rented land". | **Strong** — Distribution moat cực mạnh (GitHub ecosystem + Microsoft), 1.8M+ paid users, tích hợp sâu vào workflow developer hiện có, nhưng tính năng autocomplete có thể bị commoditized. |

---

## Phần B — Đối chiếu 3 friction areas

- **Physical load** (số click / tab / copy-paste):
  Cursor: Composer → prompt → Apply = 3 bước, rất ít click. Copilot: mở sidebar → prompt → Insert at Cursor = 4 bước, thêm 1 click để insert.

- **Cognitive burden** (prompt engineering / context):
  Cursor: không cần biết nhiều — Composer hiểu ngữ cảnh file đang mở. Copilot: có slash commands (/explain, /fix, /test) giúp rõ ý định hơn, nhưng cần nhớ commands.

- **User workarounds**:
  Cursor: để apply code vào đúng vị trí trong file lớn, đôi khi phải chỉ định line number rõ hơn. Copilot: code insert ở cursor position — nếu cursor không đúng chỗ, phải move trước khi insert.

---

## Phần C — Đối chiếu 6 trust signals

| Tín hiệu đáng tin | Cursor | GitHub Copilot |
|---|---|---|
| 1. Dẫn nguồn (citation) | Không (code gen không cần cite) | Không (code gen không cần cite) |
| 2. Disclaimer khi không chắc | Không — tin tưởng developer verify | Có — "Copilot uses AI. Check for mistakes." |
| 3. Fallback / dừng khi out-of-scope | Có — sẽ báo nếu task không phải code | Có — redirect sang /explain hoặc từ chối |
| 4. Consistency (chạy 2 lần) | Tương đối nhất quán (cùng model, cùng context) | Tương đối nhất quán (GPT-4o ổn định) |
| 5. User control (sửa, dừng, regenerate) | Có Apply/Reject; không có regenerate một click | Có Insert/Discard; có regenerate icon |
| 6. Explanation (vì sao AI nói thế) | Không tự giải thích trừ khi hỏi | Có follow-up suggestions giải thích thêm |

---

## Phần D — Định vị trên Cost-Capability-Speed

- **Cursor nghiêng về**: Mạnh-đắt (nhưng $20/tháng không phải quá cao) — model mạnh nhất, nhiều tính năng nhất (multi-file edit, Composer, codebase search), nhưng phải trả phí và phải dùng Cursor IDE
- **GitHub Copilot nghiêng về**: Cân bằng / Rẻ-tích hợp — $10/tháng (hoặc miễn phí cho students), tích hợp vào VS Code không cần chuyển IDE, ít friction hơn cho team dùng GitHub

---

## Phần E — Verdict sơ bộ

- **Cursor — verdict sơ bộ**: Promising
  - Lý do: Tăng trưởng nhanh + UX vượt trội cho code generation + differentiation thực sự (Composer multi-file), nhưng có rủi ro platform (phụ thuộc VS Code fork + model bên thứ 3)

- **GitHub Copilot — verdict sơ bộ**: Strong
  - Lý do: Distribution moat cực mạnh (GitHub = 100M developers), Microsoft backing, tích hợp sâu vào workflow không thể dễ dàng thay thế, pricing reasonable + free for students
