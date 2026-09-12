# 03 — Individual Reflection

> Viết bằng lời của bạn (Phase 7 trong `01-worksheet.md`). Có thể dùng AI gợi ý câu hỏi tự soi, không dùng AI viết thay. 8-12 câu, có chuyện cụ thể.

## Thông tin cá nhân

- Họ và tên: _[cần điền]_
- Mã học viên: _[cần điền]_
- Nhóm: _[cần điền]_
- Candidate problem nhóm chọn: _[cần điền sau Phase 3 — card cá nhân tôi mang đi pitch là "Reproduce baseline paper thiếu code/config/data"]_

---

## 1. Tôi đã tham gia vào phần nào?

Ghi việc cụ thể + kết quả cụ thể. Không ghi chung chung kiểu "tham gia thảo luận".

| Hoạt động | Tôi đã làm gì? (việc cụ thể) | Kết quả / ảnh hưởng tới nhóm |
|---|---|---|
| Scan cá nhân | Tự scan pain từ công việc research và điều phối nhóm, kèm số đo thật (2 ngày/baseline; 4 buổi họp/tuần × 3-4 giờ tổng hợp) | Có 3 Problem Card, trong đó card reproduce baseline có case cụ thể (MoE-SAM, MICCAI 2025) để mang đi pitch |
| Pitch Problem Card | _[điền sau khi pitch: bạn nói gì trong 2 phút, nhóm phản ứng ra sao]_ | |
| Challenge bài của bạn khác | _[điền: bạn hỏi bạn nào câu gì, câu hỏi đó làm nhóm sửa gì]_ | |
| Gom trùng / cluster | _[điền sau Phase 3]_ | |
| Chọn candidate problem | _[điền sau Phase 3]_ | |
| Validation / research | Tự đặt hướng research và loại bỏ nguồn không kiểm được: yêu cầu chỉ giữ nguồn có link, loại các candidate không phải trải nghiệm thật; đào tới các công trình liên quan (ReproRepo, PaperBench, Paper2Code, AutoP2C) | Tìm ra khoảng trống đo được: agent hiện tại phát hiện được blocker cho ~90% paper nhưng yếu ở exact localization — đây là chỗ bài toán còn giá trị |
| Workflow nhóm | _[điền sau Phase 5]_ | |
| Problem Statement | _[điền sau Phase 5]_ | |
| Rule / Workflow / Agent | Không chấp nhận mức AI đề xuất ban đầu (Workflow); tự lập luận lại và chọn Agent nhưng giới hạn phạm vi ở tầng thu thập, không cho sinh code | Có lý do dựa trên bằng chứng (PaperBench: agent 21.0% vs người 41.4%) thay vì chọn mức theo cảm tính |
| Decision | _[điền sau Phase 6]_ | |

**Dấu tay rõ nhất của tôi trong artifact cuối (1-2 câu):**

```text
Việc chốt lại success metric: tôi bỏ metric thời gian cảm tính ban đầu và thay bằng exact-localization accuracy trên benchmark ReproRepo — một con số có ground truth sẵn từ GitHub Issues người thật raise, nên nhóm đo được thật chứ không phải tự ước lượng. Đi kèm là ràng buộc phải so với baseline single-prompt LLM, để nếu kiến trúc nhiều agent không hơn thì thừa nhận là thừa.
```

---

## 2. Bảng dùng AI (mỗi dòng 1 phase có dùng AI — 2 cột cuối bắt buộc)

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai / hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| Scan | Tự nêu 2 pain thật của mình trước (reproduce baseline, tổng hợp note họp), sau đó nhờ AI tìm thêm pain point ở domain khác có số liệu kiểm được | Tìm được nguồn có số thật thay vì ý chung chung: khảo sát Nature 1.576 researcher, thống kê thời gian review code, số liệu documentation burden ngành y tế | Đề xuất candidate ở domain y tế và customer support — số liệu đẹp nhưng tôi không hề trải nghiệm, đưa vào scan cá nhân là giả | Loại bỏ 2 candidate đó khỏi bảng scan, chỉ giữ pain tôi thật sự trải qua và có số của chính mình |
| Problem Card | Dựng khung card và nhờ AI phản biện các field | Chỉ ra success metric ban đầu của tôi ("giảm thời gian phát hiện thiếu") là cảm tính, không ai đo khách quan được | Bản đầu AI đề xuất kiến trúc quá nhiều tầng, nhiều loại metric — phức tạp hơn mức cần cho một card | Yêu cầu cắt bớt, chốt lại đúng 1 metric khách quan duy nhất và 1 kiến trúc gọn |
| Workflow | Nhờ AI vẽ lại current state / future state theo số liệu tôi cung cấp | Bóc tách được rõ đâu là bottleneck và đặt human boundary đúng chỗ | Future state bản đầu ghi "giảm 16h xuống 30 phút", gộp nhầm thời gian chẩn đoán với thời gian setup | Sửa lại: 30 phút là bước chẩn đoán thêm vào *trước*, không phải thay thế 16h setup |
| Research | Nhờ AI tìm giải pháp đã có cho bài toán reproduce baseline và khoảng trống còn lại | Tìm ra đúng các công trình liên quan: ReproRepo (nhãn từ GitHub Issues), PaperBench (agent 21.0% vs người 41.4%), Paper2Code, AutoP2C | Vòng đầu đưa ra ý chung chung không có link kiểm được, phải yêu cầu lại mới ra nguồn cụ thể | Ép điều kiện: chỉ nhận nguồn có link kiểm được, và ghi rõ số nào là tại thời điểm công bố chứ không phải mới nhất |
| Problem Statement | _[chưa tới — điền sau Phase 5 cùng nhóm]_ | | | |
| Rule / Workflow / Agent | Nhờ AI so sánh các mức và phản biện lựa chọn | Số liệu PaperBench cho tôi cơ sở rõ để loại mức "AI tự sinh lại code" thay vì loại theo cảm tính | AI ban đầu chốt mức Workflow, chưa tính tới việc thông tin nằm rải ở 3 nguồn khác loại nên phần thu thập buộc phải tự quyết query | Tôi tự quyết lại: chọn Agent nhưng giới hạn ở tầng thu thập/chẩn đoán, orchestration cố định, người giữ quyết định cuối |
| Decision | _[chưa tới — điền sau Phase 6 cùng nhóm]_ | | | |

> Nếu phase nào không dùng AI, ghi `Không dùng` và vì sao tự làm.

---

## 3. Reflection câu hỏi mở

Chọn 3-4 câu trong 6 câu dưới để viết thành đoạn 8-12 câu (không trả lời bullet 1 dòng):
- Tôi học được gì khi nghe top 3 problems của các bạn khác?
- Nhóm có lúc nào bị solution-first, đòi làm Agent cho ngầu không?
- Tôi có thay đổi ý kiến sau khi bị challenge không, vì sao đổi?
- Tôi đóng góp gì thật sự vào artifact cuối, phần nào có dấu tay của tôi?
- Điều khó nhất khi viết Problem Statement là gì, metric hay boundary?
- Nếu làm lại, tôi sẽ challenge nhóm mạnh hơn ở điểm nào?

**Reflection:**

> Phần này worksheet quy định phải tự viết, không để AI viết thay. Dưới đây chỉ là các mốc có thật trong quá trình làm để gợi nhớ — hãy viết lại thành đoạn 8-12 câu bằng lời của mình rồi xoá phần gợi nhớ này.
>
> - Lúc AI đề xuất pain point ngành y tế và customer support: số liệu rất đẹp nhưng mình không hề trải nghiệm, và mình đã chủ động loại — vì sao mình thấy đưa vào là sai?
> - Lúc mình hỏi "nhưng làm sao biết thật sự nó thiếu cái gì": đây là câu hỏi mình phải hỏi hai lần mới ra được cơ chế cụ thể. Điều đó nói lên gì về việc nhận câu trả lời đầu tiên của AI?
> - Lúc phát hiện ReproRepo đã làm sẵn phần ground truth mà mình định tự dựng — cảm giác lúc đó thế nào, và nó đổi cách mình nghĩ về "đóng góp mới" ra sao?
> - Lúc mình yêu cầu bỏ bớt độ phức tạp và chốt 1 metric duy nhất: vì sao mình thấy bản nhiều metric là quá tham?
> - Lúc mình đổi quyết định từ Workflow sang Agent: mình đổi vì bằng chứng nào, hay vì muốn làm multi-agent cho hay? Trả lời thật câu này.
> - Điều khó nhất khi viết Problem Statement với mình là metric hay boundary?

```text



```

---

## 4. Tự kiểm cuối bài (check trước khi nộp repo)

- [ ] [12đ] Cá nhân có 5+ problems + top 3 Problem Cards
- [ ] [12đ] Tôi đã pitch rõ + challenge nhóm đúng trọng tâm (ghi ở bảng mục 1)
- [ ] Nhóm có nhật ký hội tụ từ candidates về 1 bài
- [ ] [15đ] Nhóm có workflow trước/sau
- [ ] [20đ] Nhóm có PS v0/v1 với metric + boundary rõ
- [ ] [15đ] Nhóm có so sánh No AI / Rule / Workflow / Agent
- [ ] [10đ] Nhóm có Go / Not Yet / No-Go + lý do rõ
- [ ] [10đ] Reflection này có vai trò thật + AI giúp/sai ở đâu + điều học được + nếu làm lại đổi gì
- [ ] [6đ] Tôi tự giải thích được mạch problem → workflow → metric → boundary → độ phù hợp AI

