# FINAL · Đóng khung vấn đề

## 1. Yêu cầu gốc

AI20k muốn xây một **Assessment & Rubric Engine** để hỗ trợ review các artifact lớn của học viên như Problem Framing, Solution, AI Pilot Plan và 5-slide Pitch. Mục tiêu ban đầu là giúp instructor/coach đánh giá nhanh hơn, nhất quán hơn và phát hiện thiếu sót theo rubric.

## 2. Vấn đề sau khi đóng khung lại

Thay vì build một hệ thống auto-grading đầy đủ, nhóm đóng khung lại thành một pilot nhỏ hơn:

```text
Coach cần một AI pre-review assistant cho phần Pilot Plan + Exit Criteria,
để phát hiện nhanh các lỗi rubric quan trọng trước khi coach gửi feedback chính thức.
```

AI không chấm điểm và không thay coach. AI chỉ tạo một bản pre-review có cấu trúc: mục nào đạt/chưa đạt, bằng chứng nằm ở đâu trong bài, lỗi nào nghiêm trọng, và câu hỏi coach nên hỏi lại nhóm học viên.

## 3. Người dùng mục tiêu

Primary user:

```text
Coach / TA review bài Day28 của các nhóm học viên.
```

Secondary users:

- Instructor / Program Lead: cần biết nhóm nào có pilot plan đủ chặt để pitch.
- Học viên: nhận feedback tốt hơn, nhưng chỉ sau khi coach duyệt.
- Ops: theo dõi nhóm nào đã được review và nhóm nào còn thiếu mục quan trọng.

Người không chọn làm primary user ở pilot đầu:

```text
Học viên tự dùng AI để self-check.
```

Lý do: nếu đưa trực tiếp cho học viên ngay, AI feedback có thể bị hiểu là đáp án hoặc điểm chính thức. Pilot đầu nên coach-facing để kiểm soát rủi ro.

## 4. Thời điểm trong quy trình

Workflow hiện tại:

```text
Nhóm học viên hoàn thành Pilot Plan / 5-slide Pitch
→ nộp worksheet lên GitHub/LMS
→ coach mở từng file và đọc thủ công
→ coach kiểm có đủ scope, metric, budget, owner, exit criteria, ask không
→ coach viết feedback hoặc chuẩn bị câu hỏi phản biện
→ nhóm học viên sửa / pitch
```

Workflow mong muốn trong pilot:

```text
Nhóm học viên nộp Pilot Plan / Pitch
→ AI đọc bài + rubric 5 Gate
→ AI tạo pre-review report cho coach
→ coach kiểm, sửa, approve hoặc bỏ qua flag của AI
→ coach gửi feedback chính thức / dùng làm câu hỏi phản biện
```

Moment quan trọng nhất:

```text
Sau khi học viên nộp bài, trước khi coach feedback hoặc trước buổi pitch.
```

## 5. Nỗi đau / baseline

Pain chính:

- Pilot Plan thường là phần quyết định business nhất nhưng cũng dễ thiếu mục nhất.
- Một bài có thể nhìn thuyết phục nhưng vẫn thiếu baseline, metric, budget hoặc exit criteria.
- Coach phải đọc thủ công nhiều file và tự dò từng mục theo rubric.
- Nếu coach bỏ sót lỗi lớn, nhóm có thể pitch một pilot plan không đủ để stakeholder quyết định.

Baseline hiện chưa có số đo thật từ chương trình, nên nhóm ghi rõ các số dưới đây là giả định cần validate:

```text
Giả định cần validate:
- Coach mất khoảng 10-15 phút để review một Pilot Plan / Pitch.
- Một ngày lab có thể có nhiều nhóm cần review trong thời gian ngắn.
- AI pre-review tốt có thể giảm 30-40% thời gian đọc lần đầu.
- Coach nên dùng được ít nhất 70% flags AI đưa ra thì pilot mới đáng tiếp tục.
```

Các baseline cần đo trong pilot:

| Baseline cần đo | Cách đo |
|---|---|
| Thời gian coach review 1 bài không có AI | Coach self-time hoặc log timestamp |
| Thời gian coach review 1 bài có AI pre-review | Coach self-time hoặc log timestamp |
| Tỷ lệ AI flag được coach chấp nhận | Coach đánh dấu use / edit / reject |
| Tỷ lệ AI bỏ sót lỗi nghiêm trọng | Coach ghi lỗi nghiêm trọng mà AI không phát hiện |
| Coach satisfaction | 1-5 rating sau mỗi batch review |

## 6. Vì sao cần làm bây giờ

Day28 có rubric 5 Gate rõ ràng và artifact đầu ra tương đối chuẩn hóa, nên phù hợp để pilot rubric pre-review hơn các bài mơ hồ hơn. Đây là thời điểm tốt vì:

- Học viên vừa làm AI Pilot Plan, cần feedback nhanh để sửa trước pitch/peer review.
- Gate 5 yêu cầu rõ các mục có thể kiểm được: scope, timeline, người, budget, metric, exit criteria, ask.
- Chương trình có nhiều nhóm học viên, nên nếu pilot thành công có thể scale sang các ngày khác.
- Day26 và Day27 đã có tư duy product/economics, nên Day28 có thể dùng AI để kiểm các lỗi plan mang tính PM khá rõ.

## 7. Ràng buộc

- Không auto-grade và không đưa điểm chính thức.
- Human-in-the-loop bắt buộc: coach duyệt trước khi feedback đến học viên.
- AI phải bám vào rubric và bài nộp; nếu không thấy bằng chứng thì ghi "not found", không tự suy diễn.
- Không dùng dữ liệu cá nhân nhạy cảm của học viên.
- Pilot chỉ tập trung vào Day28 Pilot Plan / Pitch, không review mọi artifact.
- Nếu dùng số chưa đo được, phải ghi rõ là giả định.
- Output phải ngắn và actionable, nếu quá dài sẽ làm coach tốn thêm thời gian.

## 8. Phạm vi Quick Win

Quick Win được chọn:

```text
AI pre-review Pilot Plan + Exit Criteria cho Day28.
```

Trace từ các bước trước:

- `1-intake-breakdown.md` tách Track 06 thành 8 use case.
- `2-quick-win.md` chấm 6 candidate bằng 4 tiêu chí: Impact, Feasibility, Evidence nhanh, Risk.
- Use case thắng là **AI pre-review Pilot Plan + Exit Criteria** với tổng điểm 4.80.
- Nhóm xác nhận không chọn full tool, student self-check hay dashboard vì các hướng đó rộng hơn, rủi ro hơn, hoặc cần nhiều dữ liệu hơn.

In scope:

- Đọc `worksheet/03-pilot-plan/1-pilot-plan.md`.
- Đọc `worksheet/03-pilot-plan/2-FINAL-pitch.md`.
- Kiểm các mục:
  - scope
  - out of scope
  - owner/team
  - data required
  - budget
  - timeline
  - metrics
  - baseline
  - success threshold
  - exit criteria
  - adoption plan
  - decision request / ask
- Tạo report cho coach:
  - pass / weak / missing theo từng mục
  - evidence từ bài nộp
  - severity
  - suggested coach question

Out of scope:

- Chấm điểm chính thức.
- Feedback trực tiếp cho học viên khi chưa có coach duyệt.
- Review toàn bộ mọi worksheet của Day28.
- Dashboard toàn khóa.
- Auto-merge / auto-submit / thay đổi file học viên.

## 9. Câu hỏi còn mở

- Coach hiện mất bao lâu để review một Pilot Plan/Pitch?
- Số bài cần review trong một buổi Day28 là bao nhiêu?
- Lỗi bị bỏ sót nào là nghiêm trọng nhất: thiếu exit criteria, thiếu metric, thiếu baseline, hay thiếu lời xin quyết định?
- Coach muốn output ở dạng checklist, table, hay comment trực tiếp trên markdown?
- Có cần AI trích dẫn line/section cụ thể trong file nộp không?
- Ngưỡng dừng pilot là gì nếu AI miss lỗi nghiêm trọng?
- Dữ liệu bài nộp lấy từ đâu trong pilot: GitHub repo, LMS export, hay copy markdown?
- Ai là người quyết định go/no-go sau pilot: instructor, program lead, hay coach lead?

## 10. Kế hoạch kiểm chứng

Pilot validation nhỏ:

```text
Sample: 5-10 bài Pilot Plan/Pitch từ các nhóm học viên.
Người review: 1-2 coach/TA.
So sánh: review thủ công vs review có AI pre-review.
```

Các bước:

1. Chọn 5-10 bài Day28 đã nộp.
2. Coach review một vài bài theo cách thủ công để lấy baseline thời gian.
3. AI tạo pre-review report cho các bài còn lại.
4. Coach đọc AI report, đánh dấu từng flag:
   - useful
   - needs edit
   - wrong / reject
   - critical miss
5. Tính các chỉ số:
   - review time saved
   - coach acceptance rate
   - critical miss rate
   - coach satisfaction
6. Quyết định continue / revise / stop.

Success criteria đề xuất, cần stakeholder xác nhận:

```text
- Giảm ít nhất 30% thời gian review lần đầu.
- Coach dùng được ít nhất 70% flags của AI.
- Tỷ lệ AI bỏ sót lỗi nghiêm trọng dưới 10% với các lỗi như thiếu exit criteria hoặc metric.
- Coach satisfaction trung bình ≥ 4/5.
```

Exit criteria đề xuất:

```text
- Dừng nếu AI miss lỗi nghiêm trọng trong >20% bài pilot.
- Dừng nếu coach acceptance rate <50%.
- Dừng nếu coach báo AI report làm review lâu hơn thay vì nhanh hơn.
```

## Tuyên bố vấn đề cuối

Coach/TA của AI20k cần review nhiều Pilot Plan và 5-slide Pitch trong thời gian ngắn, nhưng các bài này dễ thiếu những mục quyết định như baseline, metric, budget, owner và exit criteria. Nếu review hoàn toàn thủ công, coach có thể mất nhiều thời gian và vẫn bỏ sót lỗi rubric quan trọng. Nhóm sẽ pilot một AI pre-review assistant cho Day28 Pilot Plan/Pitch: AI đọc bài nộp theo rubric 5 Gate, tạo structured report cho coach, và coach duyệt trước khi feedback chính thức. Thành công của pilot được đo bằng thời gian review giảm, tỷ lệ flag được coach chấp nhận, critical miss rate và mức hài lòng của coach.
