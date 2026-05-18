# 1 · Tách yêu cầu đầu vào

## Mục tiêu

Tách Track 06 — Assessment & Rubric Engine thành các use case nhỏ, độc lập, có thể pilot được. File này chưa chọn giải pháp cuối; mục tiêu là hiểu đúng Big Ask và tạo danh sách candidate để bước `2-quick-win.md` chấm điểm.

## Yêu cầu gốc

AI20k muốn có một công cụ AI hỗ trợ review artifact lớn của học viên theo rubric, ví dụ: Problem Framing, Solution, Pilot Plan, 5-slide pitch. Công cụ cần giúp coach/instructor đánh giá nhanh hơn, nhất quán hơn, và phát hiện lỗi rubric trước khi feedback được gửi cho học viên.

## Diễn giải lại bằng lời nhóm

Nhóm hiểu bài toán như sau: không nên build một hệ thống auto-grading hoàn chỉnh ngay. Lát cắt hợp lý hơn là tạo một **AI pre-review assistant** cho coach: AI đọc bài nộp + rubric, chỉ ra phần thiếu, phần yếu, câu hỏi phản biện, và draft feedback. Coach vẫn là người duyệt cuối.

Điểm cần giữ rõ:

- AI không chấm điểm chính thức.
- AI không gửi feedback trực tiếp cho học viên trong pilot đầu.
- AI phải bám rubric/gate, không phán chung chung.
- Output phải giúp coach tiết kiệm thời gian thật, không tạo thêm việc.

## Tách thành các hướng công cụ

| # | Use case | User chính | Workflow moment | Pain | Output mong muốn |
|---|---|---|---|---|---|
| 1 | AI pre-review Day28 Problem Framing theo 5 Gate | Coach / TA | Sau khi nhóm nộp `3-FINAL-problem-framing.md`, trước khi coach đọc sâu | Coach phải đọc nhiều bài để tìm lỗi cơ bản như thiếu user, thiếu baseline, pain chung chung | Checklist pass/fail theo Gate 1-3, flag missing evidence, câu hỏi coach nên hỏi |
| 2 | AI pre-review Solution + Visual | Coach / TA | Khi nhóm nộp `2-FINAL-solution.md` | Nhiều bài nói solution bằng chữ nhưng thiếu visual hoặc Build/Buy/Boost không có lý do | Rubric feedback cho solution, kiểm có visual, kiểm data + human review |
| 3 | AI pre-review Pilot Plan + Exit Criteria | Coach / TA | Trước pitch hoặc trước khi final submit | Pilot plan dễ thiếu metric, baseline, exit criteria, owner, budget | Bảng lỗi thiếu mục, risk flags, đề xuất câu hỏi phản biện |
| 4 | AI pre-review 5-slide Pitch | Coach / Instructor | Ngay trước buổi pitch 5 phút | Pitch đẹp nhưng thiếu ask rõ ràng, thiếu số, thiếu logic dừng pilot | Slide-by-slide critique, missing ask, weak metric, weak risk answer |
| 5 | Rubric consistency checker giữa nhiều coach | Program Lead / Instructor | Sau khi nhiều coach feedback cho các nhóm | Feedback giữa coach có thể lệch chuẩn, nhóm này bị soi kỹ hơn nhóm khác | Report so sánh pattern feedback, phát hiện rubric drift |
| 6 | Student self-check trước khi nộp | Học viên / nhóm học viên | Trước khi submit worksheet | Học viên không biết bài thiếu mục nào cho đến khi coach phản hồi | Self-check report theo rubric, nhưng không phải điểm chính thức |
| 7 | Feedback draft generator cho coach | Coach / TA | Sau khi AI đã flag lỗi rubric | Coach mất thời gian viết lại feedback lặp đi lặp lại cho lỗi phổ biến | Draft feedback ngắn gọn, có tone phù hợp, coach edit rồi gửi |
| 8 | Analytics dashboard về lỗi phổ biến | Program Lead / Ops | Cuối ngày / cuối tuần sau nhiều bài nộp | Instructor không biết cả lớp đang vướng ở gate nào để recap | Dashboard: top missing items, common misconceptions, suggested recap topics |

## Các use case không chọn ngay

- **Full auto-grading engine**: quá rủi ro vì dễ bị hiểu là điểm chính thức; cần ground truth và calibration lớn.
- **Student-facing self-check làm default**: hữu ích nhưng có rủi ro học viên copy feedback AI mà không hiểu; nên làm sau khi coach-facing flow ổn.
- **Rubric consistency dashboard toàn khóa**: có giá trị cho program lead nhưng cần nhiều dữ liệu và nhiều coach feedback trước.
- **Review mọi artifact mọi ngày**: scope quá rộng; pilot đầu nên chọn một artifact/rubric rõ nhất.

## Câu hỏi cần hỏi stakeholder

- Artifact nào đang làm coach mất thời gian nhất: Problem Framing, Solution, Pilot Plan hay Pitch?
- Hiện coach mất trung bình bao nhiêu phút để review một bài?
- Một ngày có bao nhiêu bài / nhóm cần review?
- Lỗi nghiêm trọng nhất coach muốn AI flag là gì?
- Coach có muốn AI đưa điểm số không, hay chỉ nên đưa pass/fail + feedback?
- Feedback AI có được gửi cho học viên không, hay bắt buộc coach duyệt trước?
- Ngưỡng sai nào là không chấp nhận được? Ví dụ AI miss lỗi exit criteria bao nhiêu lần thì dừng pilot?
- Dữ liệu bài nộp nằm ở đâu: GitHub, LMS, Google Docs, Discord hay form?

## Ghi chú từ AI / nghiên cứu

- Pattern phù hợp không phải "auto-grading" ngay, mà là **human-in-the-loop rubric pre-review**.
- Use case có khả năng Quick Win cao nhất là pre-review một artifact có rubric rõ, ví dụ Day28 Pilot Plan hoặc 5-slide Pitch theo 5 Gate.
- Output nên là structured feedback: Gate, evidence from submission, issue, severity, suggested coach question.
- Cần phân biệt rõ:
  - AI finds issues.
  - Coach decides final feedback.
  - Student receives human-approved feedback.
- Metrics ban đầu nên đo bằng pilot nhỏ:
  - review time saved
  - coach acceptance rate
  - critical misses
  - feedback consistency
