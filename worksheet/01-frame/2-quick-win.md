# 2 · Chọn Quick Win

## Mục tiêu

Chọn một lát cắt nhỏ của Track 06 để pilot trước, thay vì cố build full Assessment & Rubric Engine. Quick Win phải có tác động đủ rõ, làm được bằng dữ liệu sẵn có, đo được trong 1-2 tuần, và rủi ro thấp vì vẫn có coach duyệt.

## Các use case ứng viên

Từ `1-intake-breakdown.md`, nhóm rút gọn còn 6 candidate đáng chấm:

1. AI pre-review Day28 Problem Framing.
2. AI pre-review Solution + Visual.
3. AI pre-review Pilot Plan + Exit Criteria.
4. AI pre-review 5-slide Pitch.
5. Feedback draft generator cho coach.
6. Student self-check trước khi nộp.

Không đưa `rubric consistency dashboard` và `analytics dashboard` vào scoring chính vì hai use case đó cần nhiều dữ liệu sau nhiều vòng review, không phù hợp làm pilot đầu.

## Tiêu chí chấm điểm

| Tiêu chí | Mô tả | Điểm |
|---|---|---|
| Impact | Pain có lớn và thường xuyên không? Có giúp coach/instructor ra quyết định tốt hơn không? | /5 |
| Feasibility | Có thể làm pilot nhỏ bằng worksheet/rubric hiện có không? Có cần platform lớn không? | /5 |
| Evidence nhanh | Có đo được trong 1-2 tuần không? Có baseline dễ lấy không? | /5 |
| Risk | Điểm cao = rủi ro thấp. Sai thì coach có bắt được không? Có ảnh hưởng trực tiếp tới điểm/niềm tin học viên không? | /5 |

Công thức tính điểm có trọng số:

```text
Tổng = Impact×0.30 + Feasibility×0.25 + Evidence×0.25 + Risk×0.20
```

Nguồn chấm: `templates/quick-win-scoring.md` và `templates/rubric-gate-sheet.md` trong repo Day28.

## Bảng chấm Quick Win

| Use case | Impact | Feasibility | Evidence | Risk | Tổng | Ghi chú |
|---|---:|---:|---:|---:|---:|---|
| AI pre-review Day28 Problem Framing | 4 | 5 | 5 | 4 | 4.50 | Dễ pilot vì rubric Gate 1-3 rõ: breakdown, quick win, problem framing. Nhưng chỉ cover phase đầu, chưa chạm pilot plan cuối. |
| AI pre-review Solution + Visual | 4 | 4 | 4 | 4 | 4.00 | Có Gate 4 rõ, visual bắt buộc nên dễ flag. Nhưng solution quality cần nhiều judgment hơn problem framing. |
| AI pre-review Pilot Plan + Exit Criteria | 5 | 5 | 5 | 4 | 4.80 | Pain lớn, rubric rõ, dễ đo: thiếu metric, baseline, owner, budget, exit criteria. Coach vẫn duyệt nên rủi ro thấp. |
| AI pre-review 5-slide Pitch | 4 | 4 | 4 | 3 | 3.85 | Tác động cao trước present, nhưng pitch có yếu tố diễn đạt/thuyết phục khó chấm tự động hơn worksheet. |
| Feedback draft generator cho coach | 4 | 3 | 4 | 3 | 3.55 | Hữu ích, nhưng nếu AI viết feedback không chuẩn tone hoặc quá tự tin sẽ tạo thêm việc cho coach. |
| Student self-check trước khi nộp | 5 | 4 | 4 | 2 | 3.90 | Impact cao với học viên, nhưng rủi ro học viên hiểu feedback AI như đáp án/chấm điểm chính thức. Nên làm sau coach-facing pilot. |

## Giải thích điểm chi tiết

### 1. AI pre-review Day28 Problem Framing — 4.50

| Tiêu chí | Điểm | Lý do |
|---|---:|---|
| Impact | 4 | Problem Framing sai thì các phase sau dễ lệch, nên tác động cao. Tuy nhiên nó chỉ xử lý phần đầu của bài, chưa hỗ trợ quyết định pilot cuối. |
| Feasibility | 5 | Rubric Gate 1-3 rất rõ: breakdown, quick win, problem framing. Có thể dùng markdown worksheet hiện có để pilot ngay. |
| Evidence nhanh | 5 | Coach có thể nhanh chóng đánh dấu AI flag đúng/sai trên 5-10 bài. Các lỗi như thiếu user, thiếu baseline, pain chung chung khá dễ quan sát. |
| Risk | 4 | Rủi ro thấp vì coach duyệt trước. Nhưng vẫn có khả năng AI hiểu sai một problem framing tốt nhưng viết khác format. |

### 2. AI pre-review Solution + Visual — 4.00

| Tiêu chí | Điểm | Lý do |
|---|---:|---|
| Impact | 4 | Gate 4 rất quan trọng vì README nói visual là bắt buộc; thiếu visual có thể làm bài trượt. |
| Feasibility | 4 | Có thể kiểm xem có flow/mockup/source không, nhưng đánh giá chất lượng solution cần nhiều judgment hơn. |
| Evidence nhanh | 4 | Có thể đo nhanh bằng tỷ lệ flag coach chấp nhận. Tuy nhiên solution quality thường cần đọc kỹ nguồn và logic Build/Buy/Boost. |
| Risk | 4 | Coach-in-the-loop giảm rủi ro. Risk còn lại là AI có thể quá checklist, chỉ thấy "có visual" mà không đánh giá visual có hữu ích không. |

### 3. AI pre-review Pilot Plan + Exit Criteria — 4.80

| Tiêu chí | Điểm | Lý do |
|---|---:|---|
| Impact | 5 | Đây là phần quyết định stakeholder có approve pilot hay không. Thiếu metric, budget, owner hoặc exit criteria làm plan không đủ để quyết. |
| Feasibility | 5 | Gate 5 có checklist rõ: scope, timeline, người, budget, metric, exit criteria, ask. Dữ liệu nằm sẵn trong worksheet markdown. |
| Evidence nhanh | 5 | Có thể pilot trong 1-2 tuần với 5-10 bài, đo review time, coach acceptance rate và critical miss rate. |
| Risk | 4 | Rủi ro thấp vì AI chỉ pre-review cho coach. Không cho 5 vì nếu AI miss exit criteria hoặc hallucinate evidence thì có thể làm coach mất trust. |

### 4. AI pre-review 5-slide Pitch — 3.85

| Tiêu chí | Điểm | Lý do |
|---|---:|---|
| Impact | 4 | Pitch là thứ stakeholder nhìn trực tiếp, nên feedback nhanh trước pitch có giá trị. |
| Feasibility | 4 | Có thể check slide có problem, quick win, solution, pilot plan, ask. Nhưng pitch quality còn phụ thuộc storytelling và delivery. |
| Evidence nhanh | 4 | Có thể đo bằng coach acceptance rate và chất lượng câu hỏi phản biện. |
| Risk | 3 | AI dễ nhận xét style/tone quá nhiều hoặc đánh giá presentation không công bằng nếu chỉ đọc markdown. |

### 5. Feedback draft generator cho coach — 3.55

| Tiêu chí | Điểm | Lý do |
|---|---:|---|
| Impact | 4 | Nếu tốt, nó giảm thời gian viết feedback lặp lại cho coach. |
| Feasibility | 3 | Viết feedback đúng tone, đúng mức độ và không quá dài khó hơn flag lỗi rubric. |
| Evidence nhanh | 4 | Coach có thể đánh dấu draft dùng được hay không khá nhanh. |
| Risk | 3 | Nếu AI viết quá tự tin hoặc sai tone, coach phải sửa nhiều hơn, làm phản tác dụng. |

### 6. Student self-check trước khi nộp — 3.90

| Tiêu chí | Điểm | Lý do |
|---|---:|---|
| Impact | 5 | Học viên được check trước khi nộp có thể cải thiện bài nhanh, giảm lỗi cơ bản. |
| Feasibility | 4 | Dễ làm bằng prompt/rubric, nhưng cần thiết kế guardrails tốt. |
| Evidence nhanh | 4 | Có thể đo số lỗi giảm sau self-check hoặc số lần học viên sửa bài. |
| Risk | 2 | Rủi ro cao vì học viên có thể coi AI feedback là đáp án, game rubric, hoặc hiểu nhầm là điểm chính thức. Vì vậy không chọn pilot đầu. |

## Quick Win được chọn

```text
AI pre-review Pilot Plan + Exit Criteria cho worksheet/03-pilot-plan/1-pilot-plan.md
và worksheet/03-pilot-plan/2-FINAL-pitch.md.
```

Lý do chọn:

- Đây là phần gần quyết định business nhất: stakeholder cần biết có approve pilot hay không.
- Rubric rõ theo Gate 5: scope, timeline, người, budget, metric, exit criteria, lời xin.
- Các lỗi thường rất cụ thể và dễ flag:
  - không có baseline
  - metric mơ hồ
  - thiếu budget
  - không có owner
  - exit criteria không rõ
  - slide cuối không có ask
- Có thể pilot nhỏ bằng dữ liệu có sẵn: lấy một số bài Day28 của nhóm học viên, cho AI pre-review, rồi coach đánh dấu feedback nào dùng được.
- Rủi ro được kiểm soát vì AI chỉ tạo pre-review cho coach, không gửi trực tiếp cho học viên.

Luồng ra quyết định:

```text
Breakdown tạo 8 use case
→ bỏ dashboard/rubric drift vì cần nhiều dữ liệu lịch sử
→ chấm 6 candidate bằng 4 tiêu chí có trọng số
→ Pilot Plan + Exit Criteria đạt điểm cao nhất 4.80
→ chọn làm Quick Win vì vừa high impact, vừa đo nhanh, vừa coach-facing nên rủi ro kiểm soát được
```

## Vì sao không làm full tool

Full Assessment & Rubric Engine sẽ gồm nhiều module: ingest bài nộp, hiểu nhiều loại artifact, chấm rubric, tạo feedback, dashboard, calibration giữa coach, self-check cho học viên. Scope đó quá rộng cho pilot đầu và dễ trượt Gate 1 vì đang pitch cả platform.

Nhóm chỉ chọn một lát cắt:

```text
Input: 1 bài Pilot Plan / 5-slide pitch
Rubric: 5 Gate của Day28
Output: AI pre-review report cho coach
Human decision: coach duyệt/sửa trước khi feedback đi ra
```

## Ai ủng hộ pilot

Giả định stakeholder ủng hộ:

- **Coach / TA**: muốn đọc nhanh hơn và không bỏ sót lỗi rubric cơ bản.
- **Instructor / Program Lead**: muốn đảm bảo nhóm nào cũng có pilot plan đủ để quyết, đặc biệt là metric và exit criteria.
- **Ops**: có lợi nếu trạng thái review rõ hơn và ít phải nhắc nhóm sửa thiếu mục.

Giả định cần validate:

- Coach có thực sự mất nhiều thời gian nhất ở phần Pilot Plan không?
- Coach có tin AI pre-review nếu nó luôn trích evidence từ bài nộp không?
- Program Lead có chấp nhận pilot chỉ coach-facing, chưa student-facing không?

## Cái nhóm KHÔNG chọn

- Không chọn **Student self-check** ở pilot đầu vì rủi ro học viên dùng AI feedback như đáp án mẫu, hoặc cố "game rubric" thay vì hiểu vấn đề.
- Không chọn **Feedback draft generator** làm Quick Win chính vì writing tone là phần sau; trước hết AI phải flag đúng lỗi rubric đã.
- Không chọn **Rubric consistency dashboard** vì cần nhiều feedback từ nhiều coach; chưa có dữ liệu đủ trong pilot nhỏ.
- Không chọn **full auto-grading** vì đây là quyết định nhạy cảm, cần ground truth/calibration, và có thể làm mất trust nếu sai.

## Rủi ro của lựa chọn

| Rủi ro | Mức độ | Cách giảm rủi ro |
|---|---|---|
| AI flag sai hoặc bỏ sót lỗi quan trọng trong pilot plan | Cao | Coach duyệt bắt buộc; đo critical miss rate; dừng nếu miss lỗi nghiêm trọng quá ngưỡng |
| AI feedback chung chung, không dựa vào bài nộp | Trung bình | Bắt output có evidence quote / section reference từ worksheet |
| Coach thấy AI tạo thêm việc thay vì tiết kiệm thời gian | Cao | Đo review time và coach acceptance rate; nếu acceptance thấp thì chỉnh prompt/format |
| Nhóm thiếu dữ liệu baseline thực tế | Trung bình | Ghi rõ số ban đầu là giả định; validate bằng 5-10 bài pilot đầu |
| Rubric bị hiểu cứng nhắc, bỏ qua judgment của coach | Trung bình | Output là pre-review, không phải điểm; coach override mọi đề xuất |

Baseline cần validate ở phase Pilot Plan:

```text
Giả định ban đầu, chưa dùng như fact:
- Coach mất khoảng 10-15 phút để review một Pilot Plan/pitch.
- AI pre-review có thể giảm 30-40% thời gian đọc lần đầu nếu format tốt.
- Ngưỡng chấp nhận: coach dùng được ít nhất 70% flags AI đưa ra.
```
