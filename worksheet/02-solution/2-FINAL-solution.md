# FINAL · Giải pháp + bản vẽ trực quan

## 1. Hướng giải pháp được chọn

```text
Boost + Light Build + Coach-in-the-loop
```

Nhóm chọn tạo một workflow AI pre-review nhỏ cho Day28 Pilot Plan/Pitch. AI không chấm điểm; AI đọc bài nộp + rubric 5 Gate, tạo báo cáo có cấu trúc cho coach. Coach duyệt, sửa, hoặc bỏ qua báo cáo trước khi feedback/câu hỏi phản biện được dùng.

## 2. Quyết định Build / Buy / Boost / Partner

Quyết định:

```text
Boost first, light build only where needed.
```

- **Boost** workflow hiện có: học viên vẫn nộp markdown qua GitHub/LMS, coach vẫn là người review cuối.
- **Light Build** một prompt/schema reviewer để tạo báo cáo thống nhất.
- **Partner** với 1-2 coach để calibrate rubric và validate flags.
- **Không Buy trước** vì các grading tools có sẵn mạnh về rubric workflow nhưng chưa khớp ngay với Day28 markdown + AI Pilot Plan rubric.

## 3. Vì sao chọn hướng này

- Bám sát Quick Win: chỉ review Pilot Plan + Pitch, không build full grading engine.
- Giữ human-in-the-loop nên giảm rủi ro auto-grade sai.
- Có thể pilot bằng dữ liệu sẵn có: worksheet markdown + rubric 5 Gate.
- Dễ đo trong 1-2 tuần: thời gian review, tỷ lệ coach chấp nhận flag, tỷ lệ AI bỏ sót lỗi nghiêm trọng.
- Có thể mở rộng sau: nếu hiệu quả, tích hợp vào GitHub comments/LMS hoặc dashboard.

Nguồn tham khảo:

- Gradescope có pattern AI-assisted grading nhưng vẫn để instructor kiểm soát rubric/action: [Gradescope AI-Assisted Grading](https://guides.gradescope.com/hc/en-us/articles/24838908062093-AI-Assisted-Grading-and-Answer-Groups).
- Gradescope/Canvas/Moodle đều dùng rubric để chuẩn hóa grading workflow: [Gradescope rubrics](https://guides.gradescope.com/hc/en-us/articles/22249389005709-Grading-submissions-with-rubrics), [Canvas SpeedGrader rubrics](https://community.instructure.com/en/kb/articles/661173-how-do-i-use-a-rubric-to-grade-submissions-in-speedgrader), [Moodle Rubrics](https://docs.moodle.org/404/en/Rubrics).
- OpenAI Graders gợi ý pattern đánh giá có cấu trúc theo criterion, nhưng trong pilot này output chỉ là pre-review, không phải điểm chính thức: [OpenAI Graders](https://platform.openai.com/docs/guides/graders/).

## 4. Luồng người dùng

```text
Nhóm học viên hoàn thành Day28 Pilot Plan + 5-slide Pitch
        |
        v
Nộp worksheet/03-pilot-plan/*.md lên GitHub/LMS
        |
        v
AI pre-review đọc:
  - 00-context.md
  - 1-pilot-plan.md
  - 2-FINAL-pitch.md
  - rubric 5 Gate
        |
        v
AI tạo báo cáo pre-review có cấu trúc
        |
        v
Coach đọc báo cáo AI
        |
        +--> Chấp nhận flag hữu ích
        +--> Sửa flag còn yếu
        +--> Bỏ flag sai
        |
        v
Coach gửi feedback cuối / dùng làm câu hỏi phản biện khi pitch
```

## 5. Luồng hệ thống / AI

```text
Đầu vào
  |
  |-- Bài nộp markdown
  |-- Context của track
  |-- Rubric 5 Gate
  |-- Schema output
  v
Tiền xử lý
  |
  |-- Tách các phần: scope, metric, budget, timeline, exit criteria, ask
  |-- Đánh dấu phần thiếu hoặc yếu
  v
LLM Review
  |
  |-- Kiểm từng tiêu chí rubric
  |-- Bắt buộc có câu trích bằng chứng hoặc "không tìm thấy"
  |-- Gán mức độ: nghiêm trọng / lớn / nhẹ
  |-- Tạo câu hỏi gợi ý cho coach
  v
Báo cáo có cấu trúc
  |
  |-- Tóm tắt
  |-- Bảng theo từng Gate
  |-- Các lỗi nghiêm trọng
  |-- Checklist hành động cho coach
  v
Human Review
  |
  |-- Coach chấp nhận / sửa / từ chối
  |-- Ghi lại metric feedback
```

## 6. Dữ liệu đầu vào

- `worksheet/00-context.md`: context của track, user chính, constraints.
- `worksheet/03-pilot-plan/1-pilot-plan.md`: pilot scope, timeline, budget, metrics, exit criteria.
- `worksheet/03-pilot-plan/2-FINAL-pitch.md`: 5-slide pitch và lời xin quyết định.
- Day28 5 Gate rubric:
  - Breakdown
  - Quick Win
  - Problem Framing
  - Solution + Visual
  - Pilot Plan
- Context bổ sung nếu cần:
  - `worksheet/01-frame/3-FINAL-problem-framing.md`
  - `worksheet/02-solution/2-FINAL-solution.md`
- Nhãn coach dùng sau khi review:
  - được dùng
  - cần sửa
  - loại bỏ
  - AI bỏ sót lỗi nghiêm trọng

## 7. Con người duyệt cuối / review chuyên môn

- Output của AI không bao giờ là feedback cuối.
- Coach/TA phải duyệt trước khi feedback đến học viên.
- Coach có quyền override mọi flag.
- Coach đánh dấu AI flag là dùng được / cần sửa / sai.
- Instructor/Program Lead xem metric pilot trước khi scale.

Quyền quyết định:

```text
AI gợi ý.
Coach quyết định feedback.
Program Lead quyết định tiếp tục / mở rộng / dừng.
```

## 8. Ví dụ output

```markdown
# Báo cáo AI pre-review — Pilot Plan

## Tóm tắt
Nhận định chung: Cần coach review trước khi pitch.
Số lỗi critical tìm thấy: 2

## Gate 5 — Pilot Plan

| Tiêu chí | Trạng thái | Bằng chứng | Mức độ | Câu hỏi gợi ý cho coach |
|---|---|---|---|---|
| Scope | Đạt | "Pilot covers 10 teams in Week 1..." | Nhẹ | Out-of-scope đã đủ rõ chưa? |
| Metric | Yếu | "Improve feedback quality" | Nghiêm trọng | Metric nào đo được việc quality cải thiện? |
| Baseline | Thiếu | Không tìm thấy | Nghiêm trọng | Review time/error rate hiện tại là bao nhiêu? |
| Budget | Yếu | "$50 API budget" | Lớn | Budget này đã tính thời gian coach review chưa? |
| Exit criteria | Thiếu | Không tìm thấy | Nghiêm trọng | Điều kiện nào khiến nhóm dừng pilot? |
| Decision ask | Đạt | "Approve 2-week pilot..." | Nhẹ | Ai là người approve cụ thể? |

## Checklist hành động cho coach
- Yêu cầu nhóm thêm baseline.
- Yêu cầu ít nhất 2 exit criteria.
- Làm rõ metric và success threshold.
```

## 9. Lỗi có thể xảy ra

- AI nói một phần bị thiếu dù thật ra nó nằm dưới heading khác.
- AI chấp nhận metric mơ hồ như "improve quality" như thể đó là metric đo được.
- AI tạo feedback quá dài, làm coach đọc lâu hơn review thủ công.
- AI quá tập trung vào checklist và bỏ sót logic business yếu.
- AI bịa bằng chứng không có trong bài nộp.
- Coach không đồng ý với AI nhưng báo cáo không hỗ trợ override dễ dàng.

## 10. Cách giảm rủi ro

- Bắt mọi flag phải có câu trích dẫn bằng chứng hoặc ghi `Không tìm thấy`.
- Giữ output ngắn: tóm tắt + bảng theo Gate + các lỗi nghiêm trọng.
- Dùng mức độ để coach nhìn thấy lỗi nghiêm trọng trước.
- Có nhãn hành động cho coach: dùng / sửa / bỏ.
- Calibrate trên 5-10 bài nộp trước khi scale.
- Dừng pilot nếu tỷ lệ AI bỏ sót lỗi nghiêm trọng quá cao hoặc tỷ lệ coach chấp nhận flag quá thấp.
- Không đưa AI report trực tiếp cho học viên trong pilot.

## 11. Các hướng KHÔNG chọn và lý do

### Không chọn build full platform

Nhóm không chọn build một Assessment & Rubric Engine hoàn chỉnh vì scope quá rộng: cần user management, ingest bài nộp, dashboard, history, calibration giữa coach, student-facing UI và permission. Với 70 phút lab và một pilot đầu, làm full platform sẽ vi phạm nguyên tắc Quick Win.

### Không chọn buy ngay

Các công cụ như Gradescope, Canvas SpeedGrader và Moodle Rubrics có workflow rubric rất tốt, nhưng chúng không giải quyết trực tiếp bài toán nhỏ của nhóm: đọc markdown Day28 Pilot Plan/Pitch và flag thiếu baseline, metric, budget, exit criteria. Buy có thể phù hợp ở giai đoạn scale, sau khi pilot chứng minh giá trị.

### Không chọn student-facing self-check

Student-facing self-check có impact cao, nhưng rủi ro cao hơn: học viên có thể hiểu AI feedback là đáp án mẫu, hoặc tối ưu bài để qua checklist thay vì cải thiện reasoning. Vì vậy pilot đầu chỉ coach-facing.

### Không chọn auto-grading

Auto-grading dễ gây mất trust nếu sai. Bài Pilot Plan là artifact mở, cần judgment của coach. Vì vậy AI chỉ pre-review và nêu evidence, còn coach quyết định feedback cuối.

### Không chọn dashboard analytics ở pilot đầu

Dashboard lỗi phổ biến hữu ích cho Program Lead, nhưng cần nhiều dữ liệu review qua nhiều nhóm/ngày. Pilot đầu cần chứng minh AI flag có hữu ích cho coach trước đã.

## Bản vẽ trực quan / Mockup

Bản vẽ trực quan cho Gate 4:

```text
┌────────────────────┐
│ Bài nộp học viên    │
│ Pilot Plan + Pitch  │
└─────────┬──────────┘
          │
          v
┌────────────────────┐
│ AI pre-review      │
│ Rubric 5 Gate      │
│ Bắt buộc evidence  │
└─────────┬──────────┘
          │
          v
┌────────────────────┐
│ Report có cấu trúc │
│ - Mục bị thiếu     │
│ - Metric yếu       │
│ - Rủi ro exit      │
│ - Câu hỏi coach    │
└─────────┬──────────┘
          │
          v
┌────────────────────┐
│ Coach review       │
│ Dùng/Sửa/Bỏ        │
└─────────┬──────────┘
          │
          v
┌────────────────────┐
│ Feedback cuối      │
│ Đã được người duyệt│
└────────────────────┘
```

Mức demo cho lab này: markdown mockup + ví dụ input/output ở trên. App chạy được là điểm cộng, không bắt buộc để qua Gate 4.
