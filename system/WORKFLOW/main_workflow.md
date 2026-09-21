# QUY TRÌNH TẠO TRUYỆN (MAIN WORKFLOW)

Đây là quy trình bắt buộc AI phải tuân theo thứ tự từ trên xuống dưới. Các kỹ năng (skills) cần dùng nằm trong thư mục `system/SKILLS/`.

## Bước 1: Từ Ý tưởng đến Concept (Command: `/analyze-idea`)
Đọc `INPUT/story_idea.md` -> Sử dụng kỹ năng `idea_analyzer` -> Tạo Concept -> Ghi ra `OUTPUT/outline/01_story_concept.md`.

## Bước 2: Thiết kế nhân vật (Command: `/create-characters`)
Sử dụng kỹ năng `character_designer` -> Tạo hồ sơ nhân vật -> Cập nhật vào `MEMORY/character_memory.md`.

## Bước 3: Cấu trúc câu chuyện (Command: `/create-outline`)
Sử dụng kỹ năng `story_architect` và `romance_architect` -> Tạo outline tổng thể -> Ghi ra `OUTPUT/outline/story_outline.md`.

## Bước 4: Lên dàn ý từng chương (Command: `/create-chapters`)
Sử dụng kỹ năng `chapter_planner` -> Tạo dàn ý chi tiết cho từng chương -> Ghi ra `OUTPUT/outline/chapter_outline.md`. 
*(Lưu ý: KHÔNG viết bản nháp ở bước này).*

## Bước 5: Viết bản nháp chương (Command: `/write-chapter [số]`)
Khởi tạo và chốt canon vào `MEMORY/story_bible.md`. 
Sử dụng kỹ năng `scene_writer` và `emotion_writer` để viết draft.

**QUY TẮC BẮT BUỘC Ở BƯỚC NÀY (RULE 7):**
- **Viết TỪNG CHƯƠNG MỘT**: Không bao giờ tự động viết sang chương tiếp theo nếu chưa có lệnh của người dùng.
- **Phê duyệt**: Sau mỗi chương, AI phải xuất bản nháp, check continuity, và **DỪNG LẠI CHỜ NGƯỜI DÙNG APPROVE**.
- **Cập nhật MEMORY đầy đủ (bắt buộc cả 4 file, không chỉ story_bible.md):**
  + `MEMORY/story_bible.md`: chốt sự kiện, chi tiết, trạng thái nhân vật của chương vừa viết.
  + `MEMORY/timeline.md`: cập nhật mốc thời gian tuyệt đối (ngày/giờ, khoảng cách thời gian với chương trước, thời gian hồi phục/chờ đợi nếu có).
  + `MEMORY/relationship_memory.md`: cập nhật giai đoạn/mức độ tình cảm hiện tại giữa hai nhân vật chính sau chương này.
  + `MEMORY/unresolved_threads.md`: thêm mọi nút thắt/bí mật/manh mối MỚI được cài trong chương (kèm chương cài, dự kiến chương trả), và đánh dấu RESOLVED cho thread nào vừa được giải quyết.
- **Đồng bộ (Sync)**: Nếu người dùng yêu cầu chỉnh sửa chi tiết nào trong chương, AI phải sửa chương đó, sau đó đối chiếu lại toàn bộ cốt truyện/outline để đồng bộ chi tiết thay đổi đó vào các chương sau, đồng thời cập nhật lại cả 4 file MEMORY ở trên.

## Bước 6: Đánh giá (Command: `/review`)
Sử dụng các kỹ năng kiểm tra (Plot Hole Checker, Continuity Checker, Romance Checker, Pacing Checker) -> Tạo báo cáo đánh giá vào `OUTPUT/reviews/review_report.md`. Phân loại lỗi thành CRITICAL, MAJOR, MINOR.
Bắt buộc bao gồm: (a) đối chiếu draft với chính `chapter_outline.md` của chương đó (Reveal, Ending hook, Important dialogue có thực sự xuất hiện trong draft không), (b) đối chiếu với `MEMORY/unresolved_threads.md` để xác nhận không có thread nào bị bỏ quên.

## Bước 7: Viết lại / Chỉnh sửa (Command: `/rewrite`)
Xác định nguyên nhân gốc từ báo cáo đánh giá -> Sửa lại chương bị ảnh hưởng -> Kiểm tra lại tính nhất quán (continuity).

## Bước 8: Hoàn thiện (Command: `/finalize`)
Sử dụng kỹ năng `final_editor`. Điều kiện PASS bắt buộc: `MEMORY/unresolved_threads.md` không còn thread nào ở trạng thái OPEN (mọi nút thắt đã cài đều phải được trả lời). Khi toàn bộ các chương đã vượt qua kiểm tra và được người dùng duyệt -> Ghép tất cả các chương vào một file duy nhất tại `OUTPUT/final/final_story.md`.
