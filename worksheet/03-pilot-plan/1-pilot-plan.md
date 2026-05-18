# 1 · AI Pilot Plan

## Mục tiêu

Viết pilot plan đủ rõ để Program Lead / Instructor quyết định có approve pilot hay không. Kế hoạch này dùng cho Quick Win đã chọn: **AI pre-review Pilot Plan + Exit Criteria cho coach**.

## Phạm vi pilot

Pilot nhỏ trong 2 tuần, chỉ dùng cho coach.

Trong phạm vi:

- AI đọc bài nộp Day28 của một batch nhỏ:
  - `worksheet/03-pilot-plan/1-pilot-plan.md`
  - `worksheet/03-pilot-plan/2-FINAL-pitch.md`
- AI dùng rubric 5 Gate, tập trung Gate 5:
  - scope
  - timeline
  - owner/team
  - budget
  - metrics
  - baseline
  - exit criteria
  - adoption plan
  - decision ask
- AI tạo báo cáo pre-review có cấu trúc cho coach.
- Coach đánh dấu từng AI flag:
  - dùng được
  - cần sửa
  - sai / loại bỏ
  - AI bỏ sót lỗi nghiêm trọng
- Nhóm đo thời gian review, tỷ lệ coach chấp nhận flag, tỷ lệ AI bỏ sót lỗi nghiêm trọng và mức hài lòng của coach.

## Ngoài phạm vi

- Không auto-grade.
- Không đưa điểm chính thức.
- Không gửi AI feedback trực tiếp cho học viên.
- Không review toàn bộ mọi worksheet Day28.
- Không build LMS/GitHub integration hoàn chỉnh trong pilot đầu.
- Không làm dashboard toàn khóa.
- Không dùng dữ liệu cá nhân nhạy cảm.

## Người dùng pilot

Người dùng trực tiếp:

- 1-2 Coach / TA review bài Day28.

Người dùng gián tiếp:

- Program Lead / Instructor xem kết quả pilot.
- Học viên nhận feedback đã được coach duyệt.

Mẫu pilot:

```text
5-10 bài Day28 Pilot Plan / Pitch của các nhóm học viên.
```

Ghi chú: con số 5-10 là scope pilot đề xuất, cần stakeholder xác nhận.

## Owner / Nhóm vận hành

- Product owner: Program Lead / Instructor.
- Người vận hành pilot: nhóm Thái - Linh.
- Người review chuyên môn: 1-2 Coach / TA.
- Người quyết định cuối: Program Lead / Instructor.

Vai trò nhóm:

- Thái: framing, rubric schema, pitch logic.
- Linh: pilot metrics, workflow, risk/exit criteria.

## Dữ liệu cần có

Dữ liệu tối thiểu:

- Day28 5 Gate rubric từ `templates/rubric-gate-sheet.md`.
- Bài nộp dùng trong pilot:
  - `worksheet/03-pilot-plan/1-pilot-plan.md`
  - `worksheet/03-pilot-plan/2-FINAL-pitch.md`
- Context files:
  - `worksheet/00-context.md`
  - `worksheet/01-frame/3-FINAL-problem-framing.md`
  - `worksheet/02-solution/2-FINAL-solution.md`
- Nhãn coach dùng khi review:
  - dùng được
  - cần sửa
  - sai / loại bỏ
  - AI bỏ sót lỗi nghiêm trọng
- Dữ liệu thời gian:
  - thời gian review thủ công
  - thời gian review có AI hỗ trợ

Dữ liệu không cần trong pilot:

- Điểm chính thức của học viên.
- Hồ sơ cá nhân/riêng tư của học viên.
- Toàn bộ lịch sử LMS.

## Ngân sách

| Hạng mục | Ước tính | Ghi chú |
|---|---:|---|
| Chi phí model/API | $5-15 | Ước tính cho 5-10 bài markdown dùng LLM reviewer. Chi phí thật phụ thuộc model/context length và cần đo trong pilot. |
| Công cụ | $0 | Dùng GitHub/LMS + markdown + LLM chat/API hiện có. Không build platform mới trong pilot. |
| Review của coach | 2-4 giờ coach | Coach đọc AI report, gắn nhãn flag, so với review thủ công. Đây là chi phí thật của pilot. |
| Vận hành / hỗ trợ | 1-2 giờ nhóm | Chuẩn bị input, chạy pre-review, thu nhãn, tổng hợp metrics. |

Ghi chú ngân sách:

```text
Các số trên là ước tính pilot, chưa phải chi phí vận hành đã kiểm chứng. Pilot Day28 cần đo lại thời gian review thật và lượng model usage thật.
```

## Lộ trình

| Tuần | Mốc việc | Output |
|---|---|---|
| Tuần 1 | Setup + calibration | Chốt rubric schema, output template, 2 báo cáo AI mẫu được coach review |
| Tuần 2 | Chạy batch pilot | 5-10 bài được AI pre-review và coach kiểm tra |
| Tuần 3 | Tổng hợp metrics | Tổng hợp thời gian review, tỷ lệ chấp nhận, tỷ lệ AI bỏ sót lỗi nghiêm trọng, mức hài lòng |
| Tuần 4 | Quyết định | Khuyến nghị tiếp tục / sửa / dừng + phạm vi bước tiếp theo |

## Metric

| Metric | Baseline | Mục tiêu | Cách đo |
|---|---:|---:|---|
| Thời gian review mỗi bài | Ước tính 10-15 phút thủ công; kiểm chứng ở Tuần 1 | Giảm ≥30% thời gian đọc lần đầu | Coach tự bấm giờ hoặc log timestamp |
| Tỷ lệ coach chấp nhận flag | Chưa có baseline | ≥70% AI flags được đánh dấu dùng được hoặc cần sửa | Coach gắn nhãn từng flag |
| Tỷ lệ AI bỏ sót lỗi nghiêm trọng | Chưa có baseline | <10% bài có lỗi nghiêm trọng bị AI bỏ sót | Coach ghi lại critical miss |
| Mức hài lòng của coach | Chưa có baseline | Trung bình ≥4/5 | Survey 1 câu sau batch |
| Độ nhất quán feedback | Baseline định tính | Coach thấy ít lệch rubric hơn / checklist rõ hơn | Coach debrief |

Giải thích cách tính:

| Metric | Công thức tính | Ý nghĩa | Ngưỡng hợp lý |
|---|---|---|---|
| Giảm thời gian review | `(Thời gian thủ công - Thời gian có AI) / Thời gian thủ công × 100%` | Đo AI có thật sự giúp coach đọc lần đầu nhanh hơn không. Ví dụ thủ công 12 phút, có AI 8 phút thì giảm 33%. | **≥30%** là ngưỡng đủ đáng thử tiếp: tiết kiệm rõ ràng nhưng không quá ảo tưởng ở pilot đầu. Nếu chỉ giảm 5-10%, lợi ích chưa bù công vận hành. |
| Tỷ lệ coach chấp nhận flag | `(Số flag được coach đánh dấu "dùng được" hoặc "cần sửa") / Tổng số flag AI đưa ra × 100%` | Đo chất lượng flag của AI. "Cần sửa" vẫn được tính vì AI vẫn giúp coach phát hiện vấn đề, dù wording chưa chuẩn. | **≥70%** là ngưỡng hợp lý cho pilot: nghĩa là khoảng 7/10 flag có giá trị. Dưới mức này coach sẽ phải lọc quá nhiều noise. |
| Tỷ lệ AI bỏ sót lỗi nghiêm trọng | `(Số bài có lỗi nghiêm trọng mà AI không flag) / Tổng số bài có lỗi nghiêm trọng theo coach × 100%` | Đo rủi ro nguy hiểm nhất: AI bỏ sót lỗi khiến Pilot Plan không đủ để stakeholder quyết định. Lỗi nghiêm trọng gồm thiếu metric, thiếu baseline, thiếu exit criteria, thiếu owner/budget hoặc thiếu decision ask. | **<10%** là ngưỡng để scale; **>20%** là ngưỡng dừng. Vì đây là coach-facing nên có thể chấp nhận pilot nhỏ có vài lỗi, nhưng nếu cứ 5 bài lỗi nghiêm trọng thì AI miss 1 bài, trust sẽ giảm mạnh. |
| Mức hài lòng của coach | `Điểm trung bình từ survey 1-5 sau batch pilot` | Đo cảm nhận thực tế của người dùng chính. Nếu coach thấy report phiền hoặc khó dùng thì metric thời gian cũng chưa đủ. | **≥4/5** là ngưỡng tiếp tục. **<3/5** là dừng hoặc redesign vì coach không thấy đủ giá trị. |
| Tỷ lệ report quá dài | `(Số report bị coach đánh dấu "quá dài/khó đọc") / Tổng số report × 100%` | Đo rủi ro AI tạo thêm việc cho coach. | **≤20%**. Nếu hơn 1/5 report bị chê dài, cần rút format trước khi scale. |

Quyết định ngưỡng:

- Ngưỡng **giảm ≥30% thời gian review** được chọn vì pilot này chỉ đáng tiếp tục nếu coach tiết kiệm thời gian thấy rõ. Với baseline giả định 10-15 phút/bài, mục tiêu là giảm còn khoảng 7-10 phút/bài.
- Ngưỡng **≥70% flag được coach chấp nhận** được chọn để đảm bảo AI report không quá nhiễu. 70% không yêu cầu hoàn hảo, nhưng đủ chứng minh AI có ích trong review lần đầu.
- Ngưỡng **<10% AI bỏ sót lỗi nghiêm trọng** là điều kiện scale. Vì lỗi nghiêm trọng ảnh hưởng quyết định pilot, mức này phải thấp hơn các metric khác.
- Ngưỡng dừng **>20% AI bỏ sót lỗi nghiêm trọng** được chọn vì nếu 1/5 bài có lỗi lớn bị AI bỏ qua, coach sẽ không còn tin report như một lớp pre-review.
- Ngưỡng **coach satisfaction ≥4/5** giữ pilot bám thực tế người dùng: nếu coach không thấy hữu ích, không nên scale dù số liệu kỹ thuật trông ổn.

Ghi chú metric:

```text
Các baseline hiện tại là giả định hoặc chưa có. Pilot tồn tại để đo lại chúng, không dùng chúng như fact.
```

## Tiêu chí dừng / tiếp tục

Dừng ngay nếu:

- AI report bị gửi cho học viên khi chưa có coach duyệt.
- AI bịa bằng chứng lặp lại khiến coach không thể tin report.

Dừng sau batch pilot nếu có một trong các điều kiện sau:

- Tỷ lệ AI bỏ sót lỗi nghiêm trọng >20%.
- Tỷ lệ coach chấp nhận flag <50%.
- Review có AI hỗ trợ lâu hơn review thủ công.
- Mức hài lòng của coach <3/5.
- Program Lead đánh giá rủi ro trust/chất lượng quá cao.

Sửa rồi chạy lại, chưa cần dừng, nếu:

- Output hữu ích nhưng quá dài.
- AI bắt được mục thiếu nhưng gán mức độ còn nhiễu.
- Coach muốn format report khác.

Tiếp tục/mở rộng nếu:

- Thời gian review giảm ≥30%.
- Tỷ lệ coach chấp nhận flag ≥70%.
- Tỷ lệ AI bỏ sót lỗi nghiêm trọng <10%.
- Mức hài lòng của coach ≥4/5.

## Kế hoạch áp dụng

Các bước áp dụng pilot:

1. Bắt đầu ở chế độ chỉ dành cho coach.
2. Giải thích rõ: AI là lớp pre-review, không phải người chấm.
3. Đưa coach format report một trang:
   - lỗi nghiêm trọng trước
   - câu trích bằng chứng / không tìm thấy
   - câu hỏi gợi ý cho coach
4. Yêu cầu coach gắn nhãn flag trong lúc review.
5. Chia sẻ tổng hợp pilot hằng tuần với Program Lead:
   - thời gian tiết kiệm
   - flag hữu ích
   - lỗi AI bỏ sót
   - ví dụ cụ thể

Nếu pilot thành công:

- Phase 2: dùng AI pre-review cho toàn bộ Day28 Pilot Plans.
- Phase 3: mở rộng sang artifact Day26/Day27.
- Sau đó: tích hợp vào GitHub comment hoặc luồng review LMS.

## Rủi ro

| Rủi ro | Mức độ | Cách giảm rủi ro |
|---|---|---|
| AI bỏ sót lỗi nghiêm trọng như thiếu exit criteria | Cao | Coach review bắt buộc; đo tỷ lệ AI bỏ sót lỗi nghiêm trọng; dừng nếu vượt ngưỡng |
| AI bịa bằng chứng | Cao | Mọi flag phải có trích dẫn/section reference hoặc ghi `Không tìm thấy` |
| Coach mất nhiều thời gian hơn để đọc AI report | Cao | Giữ report ngắn; đưa lỗi nghiêm trọng lên đầu; đo thời gian review |
| Học viên quá tin feedback AI | Trung bình | Không đưa AI report trực tiếp cho học viên trong pilot |
| Rubric bị biến thành checklist cứng | Trung bình | Coach có quyền override; thêm ghi chú về logic business yếu |
| Không có baseline | Trung bình | Tuần 1 đo thời gian review thủ công và kỳ vọng của coach |

## Đề xuất quyết định

Đề xuất:

```text
Approve pilot 2 tuần, chỉ dùng cho coach, để AI pre-review Day28 Pilot Plan/Pitch
với 5-10 bài nộp và 1-2 coach reviewer.
```

Nhóm cần:

- Quyền dùng 5-10 bài Day28 đã ẩn danh hoặc được phép dùng.
- 1-2 coach sẵn sàng gắn nhãn AI flags.
- Thống nhất rằng output AI không gửi cho học viên nếu chưa có coach duyệt.
- Cho phép thu thập dữ liệu thời gian và chất lượng review.

Quyết định sau pilot:

```text
Go: mở rộng cho toàn bộ bài Day28.
Revise: chỉnh prompt/schema/report format và chạy lại.
Stop: dừng nếu AI bỏ sót lỗi nghiêm trọng hoặc làm coach tốn thời gian hơn.
```
