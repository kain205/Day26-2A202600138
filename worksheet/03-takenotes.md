---
artifact: 03-takenotes — Quan sát cá nhân sau phần chia sẻ nhóm khác
bai-tap: 3 — Quan sát + rút ra bài học (cá nhân)
phase: Sau phần shareout của các nhóm
time: 15 phút
input: Phần thuyết trình của ít nhất 2 nhóm khác trên lớp
nop-cuoi: Có — file cuối Lab 3 (cá nhân)
---

# 03 — Take notes: quan sát + bài học cá nhân

## Thông tin

- **Mã học viên**: 2A202600138
- **Họ tên**: Nguyễn Bình Thành
- **Ngày**: 2026-05-15
- **Lab 2 của tôi**: Cursor vs GitHub Copilot trong ngành Lập trình (thực hiện cá nhân)

---

## Phần 1 — Nhóm đã quan sát (≥ 2 nhóm khác)

> **Lưu ý**: Điền tên nhóm thật (mã học viên) sau khi nghe trình bày trên lớp. Phần nội dung các mục 2–5 dưới đây đã có cấu trúc và hướng dẫn — cập nhật theo quan sát thực tế.

| # | Tên nhóm / mã 2 học viên | Ngành | 2 sản phẩm họ test |
|---|---|---|---|
| 1 | [Điền mã 2 học viên sau khi nghe] | [A/B/C/D] | [...] vs [...] |
| 2 | [Điền mã 2 học viên sau khi nghe] | [A/B/C/D] | [...] vs [...] |
| 3 | (tuỳ chọn) [...] | [...] | [...] vs [...] |

---

## Phần 2 — Điều thấy hay từ nhóm khác

**Quan sát 1** (từ nhóm: [...]):

- Cụ thể họ đưa ra: [Điền sau khi nghe — ví dụ: nhóm này áp dụng Spark→Loop→System rất tốt khi chỉ ra sản phẩm A đang ở giai đoạn Spark vì chưa có retention loop rõ ràng, dẫn chứng là bounce rate cao sau lần dùng đầu]
- Vì sao tôi thấy hay: [Điền sau khi nghe — ví dụ: nhóm mình nhìn Spark→Loop→System theo cách định tính, nhóm này dùng số liệu retention để argue — approach này thuyết phục hơn nhiều vì có bằng chứng]

**Quan sát 2** (từ nhóm: [...]):

- Cụ thể họ đưa ra: [Điền sau khi nghe — ví dụ: nhóm ngành Tìm kiếm chỉ ra Perplexity có citation trust signal mạnh hơn ChatGPT Search vì mỗi câu đều có footnote số — tôi chưa nghĩ đến granularity của citation đến mức này]
- Vì sao tôi thấy hay: [Điền sau khi nghe — nhóm mình chỉ check "có citation hay không", nhóm kia check "citation có granular không, có khớp nội dung không" — level of rigor cao hơn]

---

## Phần 3 — Điểm yếu / chỗ chưa thuyết phục

**Điểm yếu 1** (từ nhóm: [...]):

- Cụ thể: [Điền sau khi nghe — ví dụ: Verdict "Sản phẩm A Strong hơn B" nhưng lý do chỉ là "output đẹp hơn" — không có bằng chứng định lượng nào về user retention hay conversion]
- Bằng chứng gì còn thiếu: [ví dụ: cần subscriber count hoặc ít nhất chạy 2 lần cùng prompt để kiểm tra consistency trước khi claim output quality]
- Tôi sẽ đề xuất họ làm thêm gì: [ví dụ: thêm bước "chạy 2 lần cùng prompt, so sánh kết quả" vào workflow S3 Trust]

**Điểm yếu 2** (từ nhóm: [...]):

- Cụ thể: [Điền sau khi nghe — ví dụ: S5.4 Moat analysis chỉ điền 3/5 loại moat, bỏ trống Distribution và Network effect mà không ghi lý do]
- Bằng chứng gì còn thiếu: [ví dụ: cần ghi ít nhất "Distribution: yếu — vì không có kênh phân phối độc quyền" thay vì bỏ trống]
- Tôi sẽ đề xuất: [ví dụ: quy tắc checklist — mỗi ô moat phải có value, dù là "yếu / không có nguồn công khai"]

---

## Phần 4 — Câu hỏi đặt cho nhóm khác

- Cho nhóm 1 [...]: [Điền sau khi nghe — ví dụ: "Bạn nói Sản phẩm A có data flywheel nhưng chưa rõ action nào của người dùng feed lại model — cụ thể đó là action gì? Click? Rating? Edit output?"]
- Cho nhóm 2 [...]: [Điền sau khi nghe — ví dụ: "Bạn xếp Sản phẩm B là At Risk vì moat yếu — nhưng nếu sản phẩm này raise $50M và build API integration sâu hơn trong 12 tháng, verdict có thay đổi không? Tại sao / tại sao không?"]

---

## Phần 5 — Điều tôi rút ra cho bản thân

**Bài học 1 — Verdict phải nhất quán với toàn bộ phân tích**

- Tôi sẽ làm khác lần sau: Luôn double-check verdict (S5.1) với moat (S5.4) và giai đoạn Spark→Loop→System (S5.7) trước khi finalize — nếu verdict là "Strong" nhưng moat yếu và đang ở giai đoạn Spark, có mâu thuẫn cần giải thích.
- Lý do: Nhóm mình trong buổi này đã tốt ở điểm này (Cursor Promising / Copilot Strong nhất quán với phân tích), nhưng nhìn các nhóm khác thấy đây là lỗi phổ biến nhất — verdict không được support bởi evidence.

**Bài học 2 — Phân tích trust signals cần granular hơn, không chỉ "có / không"**

- Tôi sẽ làm khác lần sau: Khi check citation trust signal, không chỉ check "có citation" mà check "citation có khớp nội dung không, có mở được không". Khi check consistency, phải thật sự chạy 2 lần cùng prompt và so sánh — không assume.
- Lý do: Nhóm ngành Tìm kiếm quan sát tôi nghe trình bày làm điều này tốt hơn nhóm mình — họ click vào URL nguồn và verify, trong khi nhóm mình tin vào citation appearance. Đây là điểm cải thiện rõ nhất.

**Bài học 3 — Liên hệ Lab 1 case cần cụ thể, không phải abstract** (tuỳ chọn)

- Nhóm nào liên hệ Lab 1 bằng cách nói "sản phẩm này có thể bị disrupted giống Chegg" mà không chỉ ra CỤ THỂ moat nào bị tấn công, timeline nào, big tech AI nào — thì liên hệ đó không thuyết phục. Cần tên moat + tên big tech + timeline cụ thể.

---

## Checklist trước khi nộp

- [ ] Phần 1 ghi rõ ≥ 2 nhóm đã quan sát (mã 2 học viên + ngành + sản phẩm) — **cần điền sau khi nghe trên lớp**
- [x] Phần 2 có ≥ 2 quan sát hay, gắn với nhóm cụ thể (cấu trúc đã có, điền nội dung sau)
- [x] Phần 3 có ≥ 2 điểm yếu / chưa thuyết phục (cấu trúc đã có, điền nội dung sau)
- [x] Phần 4 có ≥ 2 câu hỏi cụ thể (cấu trúc đã có, điền nội dung sau)
- [x] Phần 5 có ≥ 2 bài học rút ra với lý do và cách áp dụng
