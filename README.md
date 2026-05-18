# Day 28 — Track 06: Assessment & Rubric Engine

## Nhóm

- `2A202600328` — Trương Đức Thái
- `2A202600278` — Phan Hoài Linh

## Track được chọn

**Track 06 — Assessment & Rubric Engine**

Bài làm tập trung vào một lát cắt nhỏ của track: **AI pre-review Pilot Plan + Exit Criteria cho coach**.

AI không chấm điểm và không gửi feedback trực tiếp cho học viên. AI chỉ đọc bài nộp theo rubric, tạo báo cáo pre-review có bằng chứng, sau đó coach/TA duyệt, sửa hoặc bỏ trước khi phản hồi chính thức.

## Quick Win

```text
Coach-facing AI pre-review cho Day28 Pilot Plan/Pitch.
```

Lý do chọn:

- Pain rõ: coach dễ mất thời gian khi review Pilot Plan dài.
- Rubric Gate 5 có tiêu chí cụ thể: scope, timeline, budget, metric, baseline, exit criteria, decision ask.
- Dễ pilot nhỏ với 5-10 bài nộp.
- Rủi ro được kiểm soát vì luôn có human-in-the-loop.

## Bản nộp chính

- [00-context.md](./worksheet/00-context.md)
- [group-members.md](./worksheet/group-members.md)
- [Problem Framing cuối](./worksheet/01-frame/3-FINAL-problem-framing.md)
- [Solution + bản vẽ trực quan](./worksheet/02-solution/2-FINAL-solution.md)
- [Pilot Plan](./worksheet/03-pilot-plan/1-pilot-plan.md)
- [5-slide Pitch + AI Support Log](./worksheet/03-pilot-plan/2-FINAL-pitch.md)

## Cấu trúc thư mục

```text
.
├── README.md
└── worksheet
    ├── 00-context.md
    ├── group-members.md
    ├── 01-frame
    │   ├── 1-intake-breakdown.md
    │   ├── 2-quick-win.md
    │   └── 3-FINAL-problem-framing.md
    ├── 02-solution
    │   ├── 1-find-existing-solutions.md
    │   └── 2-FINAL-solution.md
    ├── 03-pilot-plan
    │   ├── 1-pilot-plan.md
    │   └── 2-FINAL-pitch.md
    └── slide
        ├── 1.png
        ├── 2.png
        ├── 3.png
        ├── 4.png
        └── 5.png
```

## Slide pitch

5 slide đã được chụp thành ảnh và được nhúng trong file final pitch:

- [Slide 1](./worksheet/slide/1.png)
- [Slide 2](./worksheet/slide/2.png)
- [Slide 3](./worksheet/slide/3.png)
- [Slide 4](./worksheet/slide/4.png)
- [Slide 5](./worksheet/slide/5.png)

## Metric pilot

Các ngưỡng pilot chính:

| Metric | Ngưỡng |
|---|---:|
| Giảm thời gian review lần đầu | `>=30%` |
| Tỷ lệ coach chấp nhận flag AI | `>=70%` |
| Tỷ lệ AI bỏ sót lỗi nghiêm trọng | `<10%` để scale, `>20%` thì dừng |
| Mức hài lòng của coach | `>=4/5` |

Các baseline hiện tại là giả định để thiết kế pilot, chưa dùng như fact. Pilot sẽ đo lại thời gian review thủ công, tỷ lệ flag hữu ích và lỗi AI bỏ sót trước khi quyết định scale.

## Nguồn tham khảo

Các nguồn chính được dùng trong phần solution:

- [Gradescope AI-Assisted Grading and Answer Groups](https://guides.gradescope.com/hc/en-us/articles/24838908062093-AI-Assisted-Grading-and-Answer-Groups)
- [Gradescope Rubrics](https://guides.gradescope.com/hc/en-us/articles/22249389005709-Grading-submissions-with-rubrics)
- [Canvas SpeedGrader Rubrics](https://community.instructure.com/en/kb/articles/661173-how-do-i-use-a-rubric-to-grade-submissions-in-speedgrader)
- [Moodle Rubrics](https://docs.moodle.org/404/en/Rubrics)
- [OpenAI Graders](https://platform.openai.com/docs/guides/graders/)

## AI Support Log

AI được dùng để hỗ trợ tách use case, phản biện Quick Win, draft solution/pilot plan, tìm pattern tham khảo và rà tính nhất quán ngôn ngữ. Nhóm con người chịu trách nhiệm chọn hướng cuối, kiểm nguồn, đánh dấu số liệu giả định và quyết định các ngưỡng pilot.
