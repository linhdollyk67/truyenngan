### Rule 1 — Story must have a clear emotional journey
Mỗi truyện phải có: Beginning → Attraction / emotional hook → Development → Conflict → Escalation → Emotional climax → Resolution

### Rule 2 — Romance is the main plot
Subplot chỉ được tồn tại nếu hỗ trợ romance, character development, conflict hoặc emotional payoff. KHÔNG tạo subplot chỉ để làm truyện dài hơn.

### Rule 3 — Every chapter must change something
Mỗi chapter phải có ít nhất một trong: plot progression, relationship progression, character revelation, conflict escalation, emotional change. Nếu không, viết lại hoặc xóa.

### Rule 4 — Avoid repetitive scenes
Không lặp cùng một kiểu cãi nhau, misunderstanding, confession, hoặc emotional reaction.

### Rule 5 — Show, don't only tell
Ưu tiên action, body language, dialogue, thought, sensory detail thay vì liên tục giải thích cảm xúc.

### Rule 6 — Characters must behave consistently
Hành động phải phù hợp personality, history, motivation, current emotional state. (Chi tiết Want vs Need, xem `system/RULES/character_rules.md`)

### Rule 7 — Chapter-by-Chapter Generation and User Approval
AI CHỈ ĐƯỢC PHÉP viết truyện từng chương một. 
- Sau khi viết xong một chương, AI phải dừng lại và chờ người dùng xem xét, chỉnh sửa và APPROVE.
- Chỉ khi người dùng nói "Approve" hoặc yêu cầu viết chương tiếp theo, AI mới được phép viết tiếp.
- Sau MỖI chương (dù có chỉnh sửa hay không), AI PHẢI cập nhật đủ 4 file: `MEMORY/story_bible.md`, `MEMORY/timeline.md`, `MEMORY/relationship_memory.md`, `MEMORY/unresolved_threads.md` để đảm bảo toàn bộ các chương sau đó được đồng bộ (sync) hoàn toàn. Xem chi tiết vai trò từng file ở `system/WORKFLOW/main_workflow.md` Phase 6.

### Rule 8 — STATUS.md phải phản ánh đúng tiến độ thật
Sau mỗi Phase trong `system/WORKFLOW/main_workflow.md`, AI phải cập nhật `STATUS.md` của truyện:
- `PHASE`: phải ghi đúng tên 1 trong 9 Phase theo sơ đồ ở `README.md` (không dùng số/tên khác).
- `OPEN ISSUES`: phải liệt kê cụ thể nếu có tồn đọng thật — ví dụ số thread đang ở trạng thái OPEN trong `MEMORY/unresolved_threads.md`, hoặc file MEMORY nào chưa được cập nhật cho chương mới nhất. Không được ghi "None" hay một câu nhắc chung chung nếu thực sự có vấn đề tồn đọng.\n