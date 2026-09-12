# 01 — Individual Problem Scan

> Điền theo Phase 1 + Phase 2 trong `01-worksheet.md`. Tự scan trước, dùng AI sau để phản biện. Không copy ví dụ Weekly Report.

## Thông tin cá nhân

- Họ và tên:
- Mã học viên:
- Vai trò / bối cảnh (VD: sinh viên năm X, intern PM, ...):
- Công việc hằng tuần (3-5 gạch đầu dòng để soi problem):

---

## Phase 1 — Scan 5+ problems (tối thiểu 5, khuyến khích 8-10)

**Cách điền:** mỗi dòng = việc gì + ai chịu + đo bằng gì. Cột `Dấu hiệu thật` bắt buộc có số: mất bao lâu (bấm giờ mấy lần), mấy lần/tuần, bao nhiêu người gặp, log/ticket/quote nào.

| # | Lăng kính (Lặp lại / Tốn thời gian / AI có thể tốt hơn / Pain từ người khác) | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật (số + bằng chứng) |
|---|---|---|---|---|
| 1 | Tốn thời gian / AI có thể tốt hơn | Reproduce baseline paper (VD: MoE-SAM, MICCAI 2025) — paper chỉ publish kết quả, không publish đủ code/config/cách evaluate/preprocessing, kể cả paper top-tier | Bản thân (AI Researcher/SWE) khi cần benchmark baseline cho project | ~2 ngày/baseline (1 ngày tìm code + setup môi trường, 1 ngày lấy/chuẩn bị data); lặp lại nhiều lần nếu có nhiều baseline; case cụ thể: bị stuck hẳn ở MoE-SAM vì thiếu config, cách evaluate, cách preprocessing |
| 2 | Lặp lại / Tốn thời gian | Tổng hợp + validate lại thông tin sau họp để chia task cho phase tiếp theo — note tiếng Việt bị thiếu hoặc chồng chéo vì cuộc họp kéo dài/thông tin dồn nhanh | Bản thân (điều phối nhóm) + thành viên nhận task sai/thiếu do note không chính xác | 4 lần/tuần (tùy tiến độ dự án), mỗi lần mất 3-4 giờ để tổng hợp + validate ≈ 12-16 giờ/tuần |
| 3 | | | | |
| 4 | | | | |
| 5 | | | | |
| 6 | | | | |
| 7 | | | | |
| 8 | | | | |
| 9 | | | | |
| 10 | | | | |

> Gợi ý tự soi: tuần trước mất nhiều thời gian nhất vào việc gì? Việc gì hay trì hoãn? Người khác hay hỏi lại câu gì? Workflow nào ai cũng biết là chậm?

**AI đã dùng ở Phase 1 (nếu có):**
- Prompt đã hỏi: Sau khi tự nêu 2 pain thật (reproduce baseline, note họp), hỏi AI research thêm pain point có số liệu/nguồn kiểm được ở domain khác (software, y tế, customer support) để so sánh đa dạng lăng kính; sau đó hỏi sâu: baseline-reproduction đã có giải pháp gì, còn thiếu gì.
- Ý dùng được: Xác định đúng paper mình bị stuck (MoE-SAM, MICCAI 2025) đúng là chưa có code công khai; số liệu ngành xác nhận pain thật (khảo sát Nature trên 1.576 researcher: 70%+ từng fail khi reproduce công trình người khác); các tool hiện có (ReproScreener, PaperRepro, MCDM reproducibility framework) đều chưa giải xong — PaperRepro chỉ 44.6% accuracy, chưa ai đóng gói tool nhẹ cho 1 researcher tự check nhanh 1 paper cụ thể.
- Ý bỏ vì không phải pain thật: Candidate về EHR/clinical documentation và customer support ticket triage — có số liệu mạnh nhưng không phải trải nghiệm thật của bản thân, nên không đưa vào bảng scan cá nhân.

**Self-check Phase 1:**
- [ ] Đủ 5+ dòng, mỗi dòng có actor + số đo cụ thể
- [ ] Dùng ít nhất 3/4 lăng kính
- [ ] Không có dòng chung chung kiểu "mất nhiều thời gian"

---

## Phase 2 — Top 3 Problem Cards

### 2.1. Chọn top 3

Giữ bài nào: actor cụ thể, workflow vẽ được 3-7 bước, bottleneck ở 1 bước, impact đo được. Loại bài quá rộng.

| Rank | Problem (copy từ bảng scan) | Vì sao chọn (2-3 ý) | Điều còn chưa chắc |
|---|---|---|---|
| 1 | Reproduce baseline paper thiếu code/config (VD: MoE-SAM) | Actor cụ thể (bản thân); workflow vẽ được 6 bước rõ; bottleneck rõ (thiếu config/eval/preprocessing); có số liệu ngành xác nhận pain thật + research cho thấy tool hiện tại chưa giải xong (accuracy thấp, chưa đóng gói sản phẩm) | Success metric "phát hiện đúng % mục thiếu" cần thử trên vài paper thật mới chốt số chính xác được |
| 2 | Tổng hợp + validate note họp chia task | Lặp lại đều 4 lần/tuần, impact lớn (12-16h/tuần), dễ đo trước/sau vì có baseline thời gian rõ | AI transcribe/tóm tắt tiếng Việt độ chính xác thế nào — chưa test thử thực tế |
| 3 | (chưa chọn — cần scan thêm 3+ problem nữa để đủ tối thiểu 5 dòng theo yêu cầu Phase 1) | | |

### 2.2. Problem Cards chi tiết (lặp lại cho cả 3 cards)

---

#### Problem Card #1 — Reproduce baseline paper thiếu code/config/data

```text
Problem 1 câu:
Mỗi khi cần reproduce 1 baseline cho project, researcher mất trung bình 2 ngày (tìm code + setup env, chuẩn bị data) và nhiều lần bị kẹt hoàn toàn vì paper — kể cả paper top-tier — không publish đủ config, cách evaluate, cách preprocessing (case cụ thể: MoE-SAM, MICCAI 2025).

Actor:
Bản thân — AI Researcher / Software Engineer, cần reproduce baseline để so sánh với model/phương pháp mới trong project nghiên cứu.

Thời điểm / bối cảnh:
Đầu mỗi project nghiên cứu, khi cần benchmark với một hoặc nhiều baseline khác nhau; lặp lại mỗi lần đổi baseline.

Current workflow 3-7 bước:
1. Đọc paper, tìm code publish (nếu có)
2. Setup môi trường theo hướng dẫn (thường thiếu/không đầy đủ)
3. Tìm và chuẩn bị data theo mô tả trong paper
4. Phát hiện thiếu config / cách evaluate / cách preprocessing giữa lúc code  <-- bottleneck
5. Tự đoán, hỏi tác giả, hoặc tìm nguồn khác để bù phần thiếu
6. Chạy lại và verify số ra có khớp paper report không

Bottleneck:
Bước 4-5 — paper chỉ publish kết quả, không publish đủ code/config/data; researcher chỉ phát hiện thiếu gì giữa lúc code, không biết trước, nên bị kẹt bất ngờ và phải tự đoán, không chắc đoán đúng cho tới khi chạy ra số.

Impact:
~2 ngày/baseline (16h): 1 ngày tìm code + setup env, 1 ngày chuẩn bị data — chưa tính thời gian bị kẹt thêm khi thiếu info (case MoE-SAM là ví dụ bị kẹt hẳn). Nếu 1 project cần so sánh 3-4 baseline, tổng có thể lên 6-8+ ngày chỉ để setup. Số liệu ngành xác nhận quy mô: khảo sát Nature trên 1.576 researcher cho thấy hơn 70% từng thất bại khi cố reproduce công trình người khác.

Success metric:
Giảm thời gian "biết paper/repo thiếu gì" từ mò mẫm thủ công (không xác định, có thể phát hiện dần trong nhiều giờ/ngày code) xuống dưới 30 phút để có checklist rõ: thiếu mục nào, lệch mục nào so với paper, mục nào chưa từng được document ở đâu (cần hỏi tác giả). Đo bằng: % mục thiếu thật được checklist phát hiện đúng, so với việc tự phát hiện dần khi code.

Non-AI alternative:
Dùng thủ công ML Code Completeness Checklist (NeurIPS/Papers with Code, 5 mục: dependencies, training code, evaluation code, pretrained model, README+results) để tự tick — không cần AI, nhưng chỉ check được "có file hay không" (structural), không check được "config có khớp số trong paper không" (semantic).

AI hypothesis:
Rule quét repo tự động theo checklist mở rộng (5 mục gốc + preprocessing + config-per-experiment) để báo thiếu file gì; Workflow trích xuất bảng hyperparameter/kết quả từ paper rồi diff với giá trị trong config/code để báo lệch gì hoặc thiếu tài liệu ở cả 2 nơi. Không cần Agent tự sinh code hay tự đoán số thay người.

Quick gut:
[ ] No AI / process fix
[ ] Rule
[x] Workflow
[ ] Agent
[ ] Chưa biết
```

**Draft workflow Card #1** (ASCII / Mermaid / ảnh đính kèm):

```text
CURRENT STATE — ~16 giờ (2 ngày)/baseline, có thể kéo dài vô hạn nếu kẹt (case MoE-SAM)

[1 Tìm + đọc code: ~4h] → [2 Setup env: ~4h] → [3 Tìm/chuẩn bị data: ~8h]
→ [4 Phát hiện thiếu config/eval/preprocessing giữa lúc code: thời gian không xác định]  <-- bottleneck
→ [5 Tự đoán / hỏi tác giả / tìm nguồn khác]
→ [6 Chạy lại verify]

FUTURE STATE — setup giữ ~16h, nhưng biết rõ rủi ro thiếu gì từ đầu (~27 phút check trước)

[1 Paste link paper + repo vào tool: 2'] → [2 Rule quét file structural: 2'] → [3 Workflow diff config vs bảng paper: 10']
→ [4 Researcher review checklist kết quả: 15']  <-- human boundary
→ [5 Bắt đầu setup, biết trước phần nào chắc thiếu để chủ động hỏi tác giả/research thêm ngay từ đầu]

Fallback: Nếu tool báo "đủ" nhưng vẫn bị stuck khi code thật → quay lại quy trình cũ (tự đọc, tự hỏi tác giả). Tool chỉ giảm rủi ro bị kẹt bất ngờ, không đảm bảo reproduce được 100%.
```

File đính kèm (nếu vẽ riêng): `01-individual-problem-scan-workflow-card-1.png`

---

#### Problem Card #2 — [Tên problem]

```text
Problem 1 câu:

Actor:

Thời điểm / bối cảnh:

Current workflow 3-7 bước:
1.
2.
3.
4.
5.

Bottleneck:

Impact:

Success metric:

Non-AI alternative:

AI hypothesis:

Quick gut:
[ ] No AI / process fix
[ ] Rule
[ ] Workflow
[ ] Agent
[ ] Chưa biết
```

**Draft workflow Card #2:**

```text
CURRENT STATE — ___ phút

[1 ...] → [2 ...] → [3 ...]  <-- bottleneck

FUTURE STATE — ___ phút

[1 ...] → [2 ...] → [3 ... review]  <-- human boundary

Fallback: ...
```

File đính kèm: `01-individual-problem-scan-workflow-card-2.png`

---

#### Problem Card #3 — [Tên problem]

```text
Problem 1 câu:

Actor:

Thời điểm / bối cảnh:

Current workflow 3-7 bước:
1.
2.
3.
4.
5.

Bottleneck:

Impact:

Success metric:

Non-AI alternative:

AI hypothesis:

Quick gut:
[ ] No AI / process fix
[ ] Rule
[ ] Workflow
[ ] Agent
[ ] Chưa biết
```

**Draft workflow Card #3:**

```text
CURRENT STATE — ___ phút

[1 ...] → [2 ...] → [3 ...]  <-- bottleneck

FUTURE STATE — ___ phút

[1 ...] → [2 ...] → [3 ... review]  <-- human boundary

Fallback: ...
```

File đính kèm: `01-individual-problem-scan-workflow-card-3.png`

---

### 2.3. Card muốn pitch nhất (chuẩn bị 2 phút)

**Card tôi muốn pitch nhất:**

```text
Card #1 — Reproduce baseline paper thiếu code/config/data (case MoE-SAM, MICCAI 2025)
```

**Vì sao (2-3 câu: workflow gì, số đo gì, impact gì):**

```text
Mỗi lần reproduce 1 baseline mất ~2 ngày, và có thể bị kẹt vô hạn khi paper (kể cả top-tier) không publish đủ config/cách evaluate/preprocessing — đúng như tôi gặp với MoE-SAM. Số liệu ngành xác nhận đây là pain có thật và có quy mô lớn (70%+ researcher từng fail reproduce công trình người khác — khảo sát Nature, 1.576 người), trong khi các tool hiện có (ReproScreener, PaperRepro...) vẫn chưa giải xong (PaperRepro chỉ 44.6% accuracy).
```

**Câu hỏi tôi muốn nhóm challenge (1-2 câu hỏi đúng chỗ yếu):**

```text
1. Success metric "% mục thiếu phát hiện đúng" liệu có đo được thật trong phạm vi lab, hay chỉ là ước lượng chưa kiểm chứng?
2. Nếu checklist báo "đủ" nhưng vẫn sai khi reproduce thật (case sai vì lý do không nằm trong 6-7 mục rule check), ai/khi nào phát hiện, và điều đó có phá vỡ giá trị của tool không?
```

**AI phản biện Card (nếu có):**
- Điểm yếu AI chỉ ra: Layer Agent (tự bù phần thiếu tài liệu ở cả paper và repo) là chỗ mọi tool hiện tại đang fail/hallucinate nhiều nhất — nếu tham lam đẩy giải pháp lên mức Agent tự động hoàn toàn sẽ rủi ro cao mà lợi ích không rõ hơn Workflow.
- Tôi sửa gì: Giữ Quick gut ở mức Workflow (Rule cho phần structural + pipeline diff cố định cho phần semantic), chỉ dừng ở việc flag "thiếu/lệch/chưa document", không để AI tự đoán số hay tự sinh code thay.

### Self-check nộp phần 01
- [ ] Có 5+ problems + top 3 Cards đủ field
- [ ] Mỗi Card có workflow trước/sau + bottleneck + metric + fallback
- [ ] Đã chọn 1 card pitch + câu hỏi challenge
