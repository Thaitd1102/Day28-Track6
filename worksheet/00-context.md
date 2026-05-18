# 00 · Context

## Nhóm

```text
Nhóm 2 học viên AI20k:
- 2A202600328 — Trương Đức Thái
- 2A202600278 — Phan Hoài Linh
```

## Track được giao

```text
Track 06 — Assessment & Rubric Engine
```

## Yêu cầu lớn

```text
AI20k muốn có một hệ thống AI hỗ trợ coach/instructor review artifact lớn của học viên theo rubric.

Các artifact có thể gồm:
- Problem Framing
- Solution + visual
- AI Pilot Plan
- 5-slide pitch

Mục tiêu không phải thay coach chấm bài, mà tạo bản pre-review để coach duyệt nhanh hơn,
phát hiện lỗi thiếu rubric sớm hơn, và giúp feedback nhất quán hơn giữa nhiều nhóm học viên.
```

## Các bên liên quan

```text
Primary stakeholder:
- Program Lead / Instructor: muốn đảm bảo chất lượng bài nộp và giảm tải review.

Secondary stakeholders:
- Coach / TA: người trực tiếp đọc bài, sửa feedback, quyết định feedback cuối.
- Học viên / nhóm học viên: người nhận feedback để cải thiện bài.
- Ops team: người cần theo dõi tiến độ nộp bài, trạng thái review, và chất lượng feedback.
```

## Người dùng chính

```text
Primary user:
- Coach / TA review bài nộp.

User moment chính:
- Sau khi nhóm học viên nộp worksheet/pitch, trước khi coach gửi feedback chính thức.

Không chọn học viên làm primary user ở pilot đầu vì rủi ro feedback AI bị hiểu là điểm/chấm chính thức.
Trong pilot, AI chỉ hỗ trợ coach, không trả feedback trực tiếp cho học viên nếu chưa có human review.
```

## Bối cảnh vận hành

```text
AI20k có khoảng 500 học viên, học theo ngày/lab, thường nộp artifact qua GitHub/LMS/Discord.
Mỗi ngày có nhiều nhóm nộp bài, coach/instructor cần review nhanh nhưng vẫn bám rubric.

Pain hiện tại giả định:
- Coach mất nhiều thời gian đọc bài dài.
- Feedback có thể không nhất quán giữa coach.
- Một số bài thiếu mục quan trọng nhưng chỉ phát hiện muộn.
- Học viên cần feedback sớm để sửa trước buổi peer review hoặc pitch.

Pilot nên bắt đầu với một artifact rõ rubric nhất: Day28 AI Pilot Plan / 5-slide pitch theo 5 Gate.
```

## Ràng buộc

```text
- Không thay thế quyết định của coach/instructor.
- AI output phải là draft feedback, không phải điểm chính thức.
- Cần có human-in-the-loop trước khi feedback đến học viên.
- Không dùng dữ liệu cá nhân nhạy cảm của học viên nếu chưa được phép.
- Nếu AI không có căn cứ từ bài nộp hoặc rubric, phải ghi là assumption, không nói như fact.
- Pilot phải nhỏ: không build full grading platform.
- Cần có exit criteria rõ ràng nếu AI feedback sai, thiếu, hoặc gây thêm việc cho coach.
```

## Giả định ban đầu

```text
Giả định để bắt đầu framing:
- Artifact Day28 có rubric/gate rõ nên phù hợp để pilot rubric engine.
- Coach hiện phải đọc thủ công từng bài trước khi feedback.
- Một bản AI pre-review tốt có thể giảm thời gian review mà không giảm chất lượng.
- LLM có thể phát hiện lỗi cấu trúc: thiếu baseline, thiếu exit criteria, thiếu visual, thiếu metric.
- Những nhận định mang tính chuyên môn vẫn cần coach duyệt.

Các số như thời gian review hiện tại, số bài/ngày, coach acceptance rate cần validate ở phase sau.
```

## Cách dùng file này với AI

```text
Mỗi lần dùng AI để hỗ trợ làm bài, paste file context này trước.

Yêu cầu AI:
- Không tự chọn scope quá rộng.
- Luôn phản biện Quick Win theo 4 trục: Impact, Feasibility, Evidence, Risk.
- Nếu đưa ra số liệu không có nguồn, phải đánh dấu là giả định.
- Ưu tiên pilot nhỏ, đo được, có human-in-the-loop.
- Giữ vai trò AI là người phản biện và tạo draft, không phải người quyết định thay nhóm.
```
