# 1 · Tìm giải pháp đã có

## Mục tiêu

Tìm các pattern/giải pháp đã có cho bài toán review theo rubric, rồi chọn hướng làm thực tế cho Quick Win: **AI pre-review Pilot Plan + Exit Criteria cho coach**. Mục tiêu không phải chứng minh phải tự build, mà cân nhắc Build / Buy / Boost / Partner trước khi chốt.

## Dạng bài / pattern vấn đề

Pattern của bài toán:

```text
Human-in-the-loop rubric pre-review
```

Nói đời thường: AI đọc bài nộp + rubric, tạo bản nhận xét nháp có bằng chứng, sau đó coach duyệt. Đây không phải auto-grading hoàn toàn.

Pattern con:

- Rubric-based grading/review.
- AI-assisted grouping / pre-check.
- LLM-as-judge / grader nhưng có human review.
- Structured feedback generation.
- Workflow tool cho coach/instructor.

## Câu hỏi tìm kiếm

- Các LMS/grading tool hiện xử lý rubric review như thế nào?
- Có công cụ nào dùng AI để hỗ trợ grading nhưng vẫn giữ instructor trong vòng duyệt?
- Rubric tool có điểm mạnh/yếu gì khi áp vào artifact mở như Pilot Plan?
- LLM grader có thể dùng như thế nào mà không biến thành auto-grade rủi ro?
- Với pilot nhỏ, nên build mới, mua tool, boost workflow hiện có, hay partner với coach để vận hành thủ công + AI?

## Giải pháp đã có / Nguồn tham khảo

| # | Giải pháp / Pattern | Nguồn | Điểm dùng được | Giới hạn | Liên quan gì tới bài nhóm |
|---|---|---|---|---|---|
| 1 | Gradescope AI-assisted grading / answer groups | [Gradescope guide: AI-Assisted Grading and Answer Groups](https://guides.gradescope.com/hc/en-us/articles/24838908062093-AI-Assisted-Grading-and-Answer-Groups) | AI hỗ trợ gom câu trả lời tương tự để instructor grade nhanh hơn; instructor vẫn chọn rubric item và kiểm soát grading. | Phù hợp nhất với fixed-template assignments; không trực tiếp xử lý artifact mở dạng markdown/pitch. | Chứng minh pattern "AI hỗ trợ, con người chấm" là thực tế và an toàn hơn auto-grade. |
| 2 | Gradescope rubric grading | [Gradescope guide: Grading submissions with rubrics](https://guides.gradescope.com/hc/en-us/articles/22249389005709-Grading-submissions-with-rubrics) | Rubric giúp chuẩn hóa feedback, có thể chỉnh khi grading, hỗ trợ nhất quán giữa submissions. | Rubric tool không tự hiểu chất lượng sâu của pilot plan nếu không có AI/pre-review. | Gợi ý output của nhóm nên bám rubric item, không feedback văn xuôi chung chung. |
| 3 | Canvas SpeedGrader + Rubrics | [Instructure guide: use rubric to grade in SpeedGrader](https://community.instructure.com/en/kb/articles/661173-how-do-i-use-a-rubric-to-grade-submissions-in-speedgrader) | Instructor grade submissions bằng rubric ngay trong workflow grading. | Là grading UI, không tự flag missing baseline/exit criteria bằng AI. | Cho thấy coach-facing workflow là hướng đúng: AI report nên xuất hiện trước hoặc trong review flow. |
| 4 | Moodle Rubrics / Advanced grading | [MoodleDocs: Rubrics](https://docs.moodle.org/404/en/Rubrics) | Rubric là grading method chính thức, có tiêu chí và mức đánh giá rõ ràng. | Không có AI pre-review mặc định; cần setup rubric kỹ. | Củng cố rằng rubric structure là nền để AI kiểm từng tiêu chí. |
| 5 | OpenAI Graders / model-based evaluation | [OpenAI docs: Graders](https://platform.openai.com/docs/guides/graders/) | Có pattern dùng grader để đánh giá model output theo tiêu chí có cấu trúc. | Dùng trực tiếp cho grading học viên sẽ rủi ro nếu không calibrate/human review. | Hữu ích cho thiết kế schema: từng criterion trả pass/weak/missing + explanation. |

## Các lựa chọn Build / Buy / Boost / Partner

| Lựa chọn | Mô tả | Điểm mạnh | Điểm yếu | Mức phù hợp |
|---|---|---|---|---|
| Build | Tự build một mini reviewer đọc markdown + rubric + tạo report | Khớp đúng Day28, kiểm format/bằng chứng theo 5 Gate, demo dễ | Cần prompt/schema tốt; dễ phình scope nếu biến thành platform | Phù hợp cao cho pilot nhỏ nếu chỉ build prototype |
| Buy | Dùng LMS/grading tool như Gradescope/Canvas/Moodle rubric workflow | Có sẵn workflow grading/rubric, ổn định hơn | Không khớp ngay với artifact markdown GitHub; AI pre-review cho Pilot Plan vẫn phải custom | Phù hợp trung bình; tốt cho scale sau, không nhanh nhất cho pilot hôm nay |
| Boost | Dùng workflow hiện có GitHub/LMS + LLM prompt/schema + coach approval | Nhanh, ít build, dễ pilot, giữ human-in-loop | Ban đầu còn thủ công; chưa có dashboard tự động | Phù hợp cao nhất cho Quick Win |
| Partner | Làm cùng 1-2 coach để calibrate rubric và validate flags | Giảm rủi ro sai rubric, có feedback thật | Phụ thuộc thời gian coach | Bắt buộc nên có, nhưng không thay thế solution |

## Dữ liệu cần có

Dữ liệu tối thiểu cho pilot:

- Rubric 5 Gate của Day28 từ `templates/rubric-gate-sheet.md`.
- Submission markdown:
  - `worksheet/03-pilot-plan/1-pilot-plan.md`
  - `worksheet/03-pilot-plan/2-FINAL-pitch.md`
- Context của track / nhóm:
  - `worksheet/00-context.md`
  - `worksheet/01-frame/3-FINAL-problem-framing.md`
  - `worksheet/02-solution/2-FINAL-solution.md`
- Có thêm thì tốt: 2-3 bài mẫu đã được coach đánh giá để calibrate.
- Nhãn coach dùng khi kiểm AI report:
  - dùng được
  - cần sửa
  - sai / bỏ
  - AI bỏ sót lỗi nghiêm trọng

## Phần con người cần review

- Coach/TA duyệt mọi AI flag trước khi feedback đến học viên.
- Coach xác nhận mức độ:
  - nghiêm trọng: thiếu metric/exit criteria/ask khiến stakeholder không quyết được
  - lớn: thiếu bằng chứng hoặc scope chưa rõ
  - nhẹ: wording/tone/format
- Coach đánh dấu AI flag có dùng được không để tạo feedback loop.
- Instructor/Program Lead quyết định go/no-go sau pilot, không phải AI.

## Rủi ro / Phản ví dụ

- **Open-ended artifact khó hơn fixed-template grading**: Gradescope AI-assisted grading mạnh ở fixed-template/answer grouping; Pilot Plan là artifact mở, nên AI dễ đánh giá chung chung nếu prompt không ép evidence.
- **Rubric không đồng nghĩa quality thật**: bài đủ mục vẫn có thể yếu logic. Coach cần judgment cuối.
- **AI có thể báo thiếu sai**: nếu không yêu cầu câu trích/section bằng chứng, AI có thể nói thiếu dù bài có viết.
- **Student-facing quá sớm gây gaming**: nếu học viên nhận rubric flags trực tiếp, họ có thể sửa cho đủ checklist nhưng không cải thiện reasoning.
- **Không có baseline = khó chứng minh impact**: phải đo thời gian review và tỷ lệ coach chấp nhận flag, không chỉ nói "AI giúp nhanh hơn".

## Danh sách ngắn hướng khả thi

Hướng chốt cho file FINAL:

```text
Chọn Boost + Light Build:
- Boost workflow hiện có: GitHub/LMS submission + coach review.
- Light Build: một AI pre-review template/schema tạo báo cáo có cấu trúc.
- Partner với 1-2 coach để calibrate rubric và kiểm chứng output.
```

Không chọn Buy ở pilot đầu vì các tool như Gradescope/Canvas/Moodle hữu ích cho grading workflow nhưng chưa giải quyết ngay bài toán Day28 markdown + pilot-plan rubric trong 70 phút. Có thể cân nhắc Buy/Integrate nếu pilot chứng minh giá trị.
