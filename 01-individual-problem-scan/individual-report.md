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
| 1 | Reproduce baseline paper thiếu code/config (VD: MoE-SAM) | Actor cụ thể (bản thân); workflow vẽ được 6 bước rõ; bottleneck rõ (thiếu config/eval/preprocessing); có số liệu ngành xác nhận pain thật + research cho thấy tool hiện tại chưa giải xong đúng ở khâu exact localization | Chưa chắc multi-agent có vượt được baseline single-prompt LLM không — phải chạy thử trên ReproRepo mới biết; nếu không vượt thì kiến trúc nhiều agent là thừa |
| 2 | Tổng hợp + validate note họp chia task | Lặp lại đều 4 lần/tuần, impact lớn (12-16h/tuần), dễ đo trước/sau vì có baseline thời gian rõ | AI transcribe/tóm tắt tiếng Việt độ chính xác thế nào — chưa test thử thực tế |
| 3 | (chưa chọn — cần scan thêm 3+ problem nữa để đủ tối thiểu 5 dòng theo yêu cầu Phase 1) | | |

### 2.2. Problem Cards chi tiết (lặp lại cho cả 3 cards)

---

#### Problem Card #1 — Reproduce baseline paper thiếu code/config/data

```text
Problem 1 câu:
Mỗi khi cần reproduce một baseline, researcher mất ~2 ngày và nhiều lần bị kẹt hẳn vì paper (kể cả top-tier) không publish đủ config, cách evaluate, cách preprocessing — và chỉ phát hiện thiếu gì khi đã code được nửa đường (case thật: MoE-SAM, MICCAI 2025).

Actor:
AI Researcher / Software Engineer cần reproduce baseline để so sánh với phương pháp mới trong project.

Thời điểm / bối cảnh:
Đầu mỗi project, lặp lại mỗi lần thêm một baseline mới để benchmark.

Current workflow 3-7 bước:
1. Đọc paper, tìm code publish (nếu có)
2. Setup môi trường
3. Tìm và chuẩn bị data
4. Phát hiện thiếu config / eval protocol / preprocessing giữa lúc code  <-- bottleneck
5. Tự đoán, hỏi tác giả, hoặc lục nguồn khác
6. Chạy lại, verify số có khớp paper không

Bottleneck:
Bước 4-5. Thiếu gì chỉ lộ ra khi đã đầu tư thời gian, nên không kịp đổi hướng; và khi thiếu thì phải đoán mò, không biết đoán đúng hay sai cho tới lúc chạy ra số.

Impact:
~16h/baseline; 1 project 3-4 baseline → 6-8 ngày chỉ để setup, chưa tính lúc bị kẹt. Quy mô ngành: khảo sát Nature (1.576 researcher) — hơn 70% từng fail reproduce công trình người khác.

Success metric:
Exact-localization accuracy (top-3) trên benchmark ReproRepo (EMNLP 2026, 1.149 paper, nhãn lấy từ GitHub Issues do người thật raise): trong 3 mục tool chỉ ra, có mục nào trùng đúng blocker thật ở mức item (đúng file / đúng config field / đúng bước) hay không. Hiện trạng ban đầu: tự mò, không có số. Mục tiêu: vượt baseline single-prompt LLM (hỏi thẳng "paper này thiếu gì") trên cùng benchmark. Chọn metric này vì ReproRepo cho thấy agent hiện tại surface được blocker cho ~90% paper nhưng yếu đúng ở khâu exact localization, và benchmark đã release sẵn nên không phải tự dựng ground truth.

Non-AI alternative:
Tự tick ML Code Completeness Checklist (Papers with Code / NeurIPS, 5 mục). Rẻ, nhưng chỉ biết "có file hay không", không biết config có khớp số trong paper không, và không tìm được câu trả lời nằm trong GitHub issue đã đóng.

AI hypothesis:
Multi-agent "ReproScout", 3 agent thu thập + 1 agent tổng hợp:
  - Paper Agent  : parse paper (text + bảng + hình) → claim có cấu trúc {component, value}
  - Repo Agent   : parse repo/config/code → artifact đã implement {value, file:line}
  - Issue Agent  : đào GitHub Issues/PR của repo → blocker người khác đã báo + reply tác giả
  - Reconciler   : đối chiếu 3 nguồn → mỗi mục checklist gán: đủ / thiếu-lệch / không chắc,
                   kèm trích dẫn nguồn
Multi-agent là cần thiết vì 3 nguồn khác loại nhau (PDF đa phương thức, code, thread issue), mỗi nguồn cần cách tìm riêng và phải tự quyết query — một prompt đơn không ôm nổi.
Agent chỉ được phép ở tầng thu thập và chẩn đoán; orchestration cố định 4 stage, người giữ quyết định cuối. Không đẩy lên mức tự sinh lại code vì PaperBench cho thấy agent tốt nhất chỉ đạt 21.0% so với người 41.4% — chưa đủ tin để giao.
Boundary: không sinh code thay, không tự điền giá trị đoán; mục "không chắc" bắt buộc người xem trước khi kết luận.

Quick gut:
[ ] No AI / process fix
[ ] Rule
[ ] Workflow
[x] Agent
[ ] Chưa biết
```

**Draft workflow Card #1** (ASCII / Mermaid / ảnh đính kèm):

```text
CURRENT STATE — ~16h/baseline, kéo dài vô hạn nếu kẹt (case MoE-SAM)

[1 Tìm+đọc code: 4h] → [2 Setup env: 4h] → [3 Chuẩn bị data: 8h]
→ [4 Phát hiện thiếu giữa lúc code: không xác định]  <-- bottleneck
→ [5 Đoán / hỏi tác giả] → [6 Chạy verify]

FUTURE STATE — thêm ~30' chẩn đoán TRƯỚC khi bỏ 16h

[1 Paste link paper + repo]
→ [2 Paper/Repo/Issue Agent chạy song song: ~10']
→ [3 Reconciler ra báo cáo có trích dẫn: ~5']
→ [4 Researcher review mục "không chắc": ~15']   <-- human boundary
→ [5 Bắt đầu setup, biết trước chỗ nào sẽ kẹt và chỗ nào đã có người giải trong issue]

Fallback: tool báo "đủ" nhưng vẫn kẹt → quay lại quy trình cũ. Tool giảm rủi ro kẹt bất ngờ, không hứa reproduce được 100%.
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
- Điểm yếu AI chỉ ra: (1) Mức "agent tự sinh lại toàn bộ code" là chỗ mọi tool hiện tại fail nặng nhất — PaperBench cho thấy agent tốt nhất chỉ đạt 21.0% so với người 41.4%. (2) Success metric ban đầu ("giảm thời gian phát hiện thiếu") là metric cảm tính, khó đo khách quan. (3) Đã có negative ablation study cho thấy orchestration multi-agent có thể không tạo thêm giá trị so với pipeline đơn giản.
- Tôi sửa gì: (1) Giới hạn phạm vi agent ở tầng *thu thập và chẩn đoán*, không cho sinh code hay tự điền giá trị đoán — người giữ quyết định cuối. (2) Đổi sang một metric khách quan duy nhất: exact-localization accuracy (top-3) trên benchmark ReproRepo đã release, có nhãn thật từ GitHub Issues, thay vì tự ước lượng thời gian. (3) Chấp nhận rằng phải so với baseline single-prompt LLM, nếu không vượt thì multi-agent là thừa.

### Self-check nộp phần 01
- [ ] Có 5+ problems + top 3 Cards đủ field
- [ ] Mỗi Card có workflow trước/sau + bottleneck + metric + fallback
- [ ] Đã chọn 1 card pitch + câu hỏi challenge
