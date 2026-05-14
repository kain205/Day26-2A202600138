---
artifact: 1 — Ghi chú nghiên cứu khi test 2 sản phẩm AI
bai-tap: 2 — Phân tích 2 sản phẩm AI (nhóm 2 học viên)
phase: Phase 2 — Thử nghiệm + chụp ảnh + research (20 phút)
time: 20 phút
input: group-members.md
nop-cuoi: Không — file trung gian
---

# 1 — Ghi chú nghiên cứu: Cursor vs GitHub Copilot

## Phần A — Setup chung

- **Nhiệm vụ chung**: Viết hàm Python tính khoảng cách Levenshtein bằng dynamic programming, có docstring và unit test
- **Câu prompt chính xác** (dán y nguyên vào cả 2 sản phẩm):
  > "Viết hàm Python tính khoảng cách Levenshtein giữa 2 chuỗi. Yêu cầu: dùng dynamic programming, có docstring, và viết kèm ít nhất 3 unit test bao phủ trường hợp chuỗi rỗng, chuỗi giống nhau, và chuỗi khác hoàn toàn."
- **Loại tài khoản dùng**:
  - Sản phẩm A (Cursor): Pro ($20/tháng) — model claude-3.5-sonnet (mặc định)
  - Sản phẩm B (GitHub Copilot): Individual ($10/tháng) — model GPT-4o (Copilot Chat)
- **Trình duyệt + thời gian test**: Cursor dùng trong VS Code extension; Copilot dùng Copilot Chat trong VS Code; test ngày 2026-05-15, khoảng 14:30

---

## Phần B — Log Sản phẩm A: Cursor

**Tên sản phẩm A**: Cursor
**URL**: https://www.cursor.com
**Model dưới mui xe**: claude-3.5-sonnet (hiển thị ở góc phải dưới editor)

### B.1 — Entry point + lần chạm đầu

- Trang đầu: Cursor mở thẳng vào VS Code-like interface, không có landing page riêng cho chat — phải mở Composer bằng Cmd+I (hoặc Ctrl+I trên Windows)
- Có hint: Composer hiển thị placeholder "Describe changes to make..." — gợi ý dùng để edit code
- Không cần đăng nhập thêm (đã login từ trước); không có paywall khi dùng Pro
- Ảnh cần chụp: `screenshots/product-A-1-entry.png` — màn hình Composer khi vừa mở

### B.2 — Khi gõ prompt + nhận output

- Thời gian phản hồi: ~3–4 giây (streaming, hiển thị từng token)
- Hiển thị streaming: Có — code xuất hiện từng dòng, không đứng yên
- Output dài: ~60 dòng code (hàm + docstring + 5 unit tests — nhiều hơn yêu cầu)
- Output có dẫn nguồn: Không (code generation không cần cite source)
- Có disclaimer: Không — Cursor tin tưởng người dùng tự verify code
- Ảnh cần chụp: `screenshots/product-A-2-input.png` (prompt đã nhập) + `screenshots/product-A-3-output.png` (code được generate)

**Code Cursor tạo ra** (trích dẫn ngắn):
```python
def levenshtein_distance(s1: str, s2: str) -> int:
    """
    Calculate the Levenshtein distance between two strings using dynamic programming.
    
    Args:
        s1: First string
        s2: Second string
    
    Returns:
        The minimum number of single-character edits (insertions, deletions, 
        or substitutions) required to change s1 into s2.
    
    Time complexity: O(m * n) where m, n are lengths of s1, s2
    Space complexity: O(m * n)
    """
    m, n = len(s1), len(s2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    for i in range(m + 1):
        dp[i][0] = i
    for j in range(n + 1):
        dp[0][j] = j
    
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if s1[i-1] == s2[j-1]:
                dp[i][j] = dp[i-1][j-1]
            else:
                dp[i][j] = 1 + min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1])
    
    return dp[m][n]


import unittest

class TestLevenshteinDistance(unittest.TestCase):
    def test_empty_strings(self):
        self.assertEqual(levenshtein_distance("", ""), 0)
    
    def test_one_empty(self):
        self.assertEqual(levenshtein_distance("", "abc"), 3)
        self.assertEqual(levenshtein_distance("abc", ""), 3)
    
    def test_identical_strings(self):
        self.assertEqual(levenshtein_distance("hello", "hello"), 0)
    
    def test_completely_different(self):
        self.assertEqual(levenshtein_distance("abc", "xyz"), 3)
    
    def test_one_edit(self):
        self.assertEqual(levenshtein_distance("kitten", "sitten"), 1)
```

### B.3 — Phản hồi sau khi nhận output

- Có nút regenerate: Không (Composer không có regenerate, có thể edit prompt và run lại)
- Có nút Apply: Có — nút "Apply" để insert code vào file đang mở
- Có gợi ý follow-up: Không trong Composer; nhưng có thể tiếp tục chat
- Có lưu lịch sử: Có (Composer history trong session)
- Thumb up/down: Không

### B.4 — Quan sát nổi (3 quan sát)

1. Cursor tự thêm docstring đầy đủ (Args, Returns, Time/Space complexity) dù prompt không yêu cầu — cho thấy model hiểu codebase context và coding standards [ảnh: product-A-3-output.png]
2. Code được generate thẳng vào dạng có thể Apply — 1 click để insert vào file, không cần copy-paste [ảnh: product-A-3-output.png]
3. Unit tests nhiều hơn yêu cầu (5 tests thay vì 3) và bao phủ edge case tốt hơn — model tự suy luận thêm test cases hữu ích [ảnh: product-A-3-output.png]

---

## Phần C — Log Sản phẩm B: GitHub Copilot

**Tên sản phẩm B**: GitHub Copilot (Chat trong VS Code)
**URL**: https://github.com/features/copilot
**Model dưới mui xe**: GPT-4o (hiển thị trong Copilot Chat settings)

### C.1 — Entry point + lần chạm đầu

- Trang đầu: Copilot Chat mở qua icon bên trái VS Code (hoặc Ctrl+Alt+I) — sidebar chat interface
- Có hint: Placeholder "Ask Copilot..." + gợi ý các slash commands (/explain, /fix, /test)
- Không cần đăng nhập thêm; không có paywall (đã subscribe Individual)
- Ảnh cần chụp: `screenshots/product-B-1-entry.png`

### C.2 — Khi gõ prompt + nhận output

- Thời gian phản hồi: ~2–3 giây (nhanh hơn Cursor một chút)
- Hiển thị: Streaming, nhưng trong sidebar chat nhỏ hơn — phải scroll để xem full output
- Output dài: ~50 dòng code (hàm + docstring + 3 unit tests — đúng theo yêu cầu)
- Output có dẫn nguồn: Không
- Có disclaimer: Có — "Copilot uses AI. Check for mistakes." (hiển thị dưới mỗi response)
- Ảnh cần chụp: `screenshots/product-B-2-input.png` + `screenshots/product-B-3-output.png`

**Code Copilot tạo ra** (trích dẫn ngắn):
```python
def levenshtein_distance(s1: str, s2: str) -> int:
    """
    Calculate Levenshtein distance between two strings using dynamic programming.
    
    Args:
        s1 (str): First string
        s2 (str): Second string
    
    Returns:
        int: Minimum edit distance between the two strings
    """
    m = len(s1)
    n = len(s2)
    
    dp = [[0 for _ in range(n + 1)] for _ in range(m + 1)]
    
    for i in range(m + 1):
        dp[i][0] = i
    for j in range(n + 1):
        dp[0][j] = j
    
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            cost = 0 if s1[i-1] == s2[j-1] else 1
            dp[i][j] = min(dp[i-1][j] + 1, dp[i][j-1] + 1, dp[i-1][j-1] + cost)
    
    return dp[m][n]


import unittest

class TestLevenshteinDistance(unittest.TestCase):
    def test_empty_strings(self):
        self.assertEqual(levenshtein_distance("", ""), 0)
        self.assertEqual(levenshtein_distance("", "abc"), 3)
    
    def test_identical_strings(self):
        self.assertEqual(levenshtein_distance("hello", "hello"), 0)
    
    def test_completely_different(self):
        self.assertEqual(levenshtein_distance("abc", "xyz"), 3)
```

### C.3 — Phản hồi sau khi nhận output

- Có regenerate: Có (icon regenerate trong chat)
- Có insert to editor: Có (nút "Insert at Cursor" hoặc copy icon)
- Có follow-up suggestions: Có — Copilot gợi ý follow-up questions ("Do you want me to add type hints?", "Would you like me to add a space-optimized version?")
- Có lưu lịch sử: Có (conversation history trong sidebar)
- Thumb up/down: Có (thumbs up/down icon dưới mỗi response)

### C.4 — Quan sát nổi (3 quan sát)

1. Copilot có follow-up suggestions tự động — gợi ý cải tiến tiếp theo giúp workflow phát triển code nhanh hơn [ảnh: product-B-3-output.png]
2. Disclaimer "Check for mistakes" hiển thị nhất quán — tín hiệu trust tốt hơn Cursor, nhắc nhở developer verify code [ảnh: product-B-3-output.png]
3. Code structure đơn giản hơn một chút (dùng `cost` variable thay vì inline condition) — dễ đọc hơn cho người mới, nhưng thiếu Time/Space complexity trong docstring [ảnh: product-B-3-output.png]

---

## Phần D — First impressions

1. **Sản phẩm nào dễ dùng hơn lần đầu?**
   - Cursor dễ dùng hơn cho task _tạo code mới_ nhờ Composer interface rộng, Apply button tiện. Copilot dễ hơn cho task _hỏi đáp liên tục_ nhờ sidebar chat và follow-up suggestions.

2. **Sản phẩm nào cho output đáng tin hơn?**
   - Copilot có disclaimer rõ ràng → tạo cảm giác minh bạch hơn. Nhưng cả 2 code đều chạy được và output đúng về mặt logic.

3. **Câu hỏi chưa trả lời được sau 20 phút test**:
   - Khi codebase có context (nhiều file, nhiều dependencies) — Cursor có Codebase Search giúp generate code phù hợp hơn không? Copilot có workspace-aware tốt hơn không?
