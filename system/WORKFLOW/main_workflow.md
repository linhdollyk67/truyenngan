# QUY TRÌNH TẠO TRUYỆN (MAIN WORKFLOW)

Đây là quy trình bắt buộc AI phải tuân theo thứ tự từ trên xuống dưới. Các kỹ năng (skills) cần dùng nằm trong thư mục `system/SKILLS/`. Số Phase dưới đây khớp 1:1 với sơ đồ 9-phase ở `README.md` — không dùng số khác để tránh lệch với `STATUS.md` (xem `system/RULES/core_rules.md` Rule 8).

## Phase 1: Phân Tích & Concept (Command: `/analyze-idea`)
Đọc `INPUT/story_idea.md` -> Sử dụng kỹ năng `idea_analyzer` -> Tạo Concept -> Ghi ra `OUTPUT/outline/01_story_concept.md`.

## Phase 2: Thiết Kế Nhân Vật (Command: `/create-characters`)
Sử dụng kỹ năng `character_designer` -> Tạo hồ sơ nhân vật -> Cập nhật vào `MEMORY/character_memory.md`.

## Phase 3: Kiến Trúc Câu Chuyện (Command: `/create-outline`)
Sử dụng kỹ năng `story_architect`, `romance_architect` và `conflict_designer` (thiết kế xung đột internal/external đủ mạnh nhưng hợp lý cho toàn truyện) -> Tạo outline tổng thể -> Ghi ra `OUTPUT/outline/story_outline.md`.

## Phase 4: Dàn Ý Từng Chương (Command: `/create-chapters`)
Sử dụng kỹ năng `chapter_planner` -> Tạo dàn ý chi tiết cho từng chương -> Ghi ra `OUTPUT/outline/chapter_outline.md`.
*(Lưu ý: KHÔNG viết bản nháp ở bước này).*

## Phase 5: Thiết Lập Story Bible (Command: `/write-chapter 1` — phần khởi tạo)
Trước khi viết chương đầu tiên, khởi tạo `MEMORY/story_bible.md` (Premise, Characters, Settings, Established Facts) dựa trên `story_outline.md` và `character_memory.md`. Đây là "nguồn sự thật duy nhất" mà mọi chương sau phải tuân theo.

## Phase 6: Viết Nháp Từng Chương (Command: `/write-chapter [số]`)
Sử dụng kỹ năng `scene_writer`, `emotion_writer` và `dialogue_writer` để viết bản nháp chương hiện tại -> Ghi ra `OUTPUT/drafts/chapter_[số].md`.

**QUY TẮC BẮT BUỘC Ở PHASE NÀY (RULE 7 — xem thêm `system/RULES/core_rules.md`):**
- **Viết TỪNG CHƯƠNG MỘT**: Không bao giờ tự động viết sang chương tiếp theo nếu chưa có lệnh của người dùng.
- **Gate cập nhật MEMORY (bắt buộc — phải báo cáo đã làm, không chỉ là lời nhắc):** Trước khi trình bản nháp cho user, AI phải xác nhận đã cập nhật đủ 4 mục sau và liệt kê rõ nội dung đã cập nhật của từng mục:
  + [ ] `MEMORY/story_bible.md`: chốt sự kiện, chi tiết, trạng thái nhân vật của chương vừa viết.
  + [ ] `MEMORY/timeline.md`: cập nhật mốc thời gian tuyệt đối (ngày/giờ, khoảng cách với chương trước, thời gian hồi phục/chờ đợi nếu có).
  + [ ] `MEMORY/relationship_memory.md`: cập nhật giai đoạn/mức độ tình cảm hiện tại giữa hai nhân vật chính.
  + [ ] `MEMORY/unresolved_threads.md`: thêm mọi thread MỚI được cài (kèm chương cài, dự kiến chương trả) và đánh dấu RESOLVED cho thread vừa được giải quyết.
- **Gate review nhẹ (bắt buộc, trước khi trình user):** AI phải tự chạy nhanh `plot_hole_checker` và `continuity_checker` (rút gọn, không cần report đầy đủ) trên chính chương vừa viết. Nếu phát hiện lỗi CRITICAL, phải tự sửa trước khi trình user; lỗi MAJOR/MINOR thì nêu rõ cho user quyết định cùng lúc trình bản nháp.
- **Phê duyệt**: Sau đó AI phải **DỪNG LẠI CHỜ NGƯỜI DÙNG APPROVE**. Chỉ khi user Approve (hoặc yêu cầu viết chương tiếp) mới được viết chương kế tiếp.
- **Đồng bộ (Sync)**: Nếu người dùng yêu cầu chỉnh sửa chi tiết nào trong chương, AI phải sửa chương đó, sau đó đối chiếu lại toàn bộ cốt truyện/outline để đồng bộ chi tiết thay đổi đó vào các chương sau, đồng thời cập nhật lại cả 4 file MEMORY ở trên.

## Phase 7: Đánh Giá & Kiểm Tra (Command: `/review`)
Sử dụng các kỹ năng kiểm tra (Plot Hole Checker, Continuity Checker, Romance Checker, Pacing Checker) -> Tạo báo cáo đánh giá đầy đủ vào `OUTPUT/reviews/review_report.md`. Cả 4 checker báo cáo theo cùng một format: Issue / Severity (CRITICAL/MAJOR/MINOR) / Evidence / Suggested fix (xem `system/SKILLS/plot_hole_checker.md`).
Bắt buộc bao gồm: (a) đối chiếu draft với chính `chapter_outline.md` của chương đó (Reveal, Ending hook, Important dialogue có thực sự xuất hiện trong draft không), (b) đối chiếu với `MEMORY/unresolved_threads.md` để xác nhận không có thread nào bị bỏ quên.
*(Đây là review đầy đủ, bắt buộc chạy ít nhất một lần trước khi Finalize — không thay thế cho gate review nhẹ per-chapter ở Phase 6.)*

## Phase 8: Viết Lại / Chỉnh Sửa (Command: `/rewrite`)
Xác định nguyên nhân gốc từ báo cáo đánh giá -> Sửa lại chương bị ảnh hưởng -> Kiểm tra lại tính nhất quán (continuity) -> Quay lại Phase 7 để đánh giá lại cho đến khi PASS.

## Phase 9: Hoàn Thiện Truyện (Command: `/finalize`)
Sử dụng kỹ năng `final_editor` — đây là lượt kiểm tra tổng hợp cuối cùng trên toàn bộ bản thảo đã ghép (bổ sung thêm, không thay thế Phase 7). Ghi kết quả vào `OUTPUT/reviews/final_review.md`.
Điều kiện PASS bắt buộc: `MEMORY/unresolved_threads.md` không còn thread nào ở trạng thái OPEN (mọi nút thắt đã cài đều phải được trả lời).
Nếu FAIL -> quay lại Phase 8 để sửa, sau đó chạy lại `final_editor` cho đến khi PASS.
Khi PASS toàn bộ -> Ghép tất cả các chương vào một file duy nhất tại `OUTPUT/final/final_story.md`.
