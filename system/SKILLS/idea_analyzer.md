# Kỹ năng: Idea Analyzer
Nhiệm vụ: Phân tích `INPUT/story_idea.md`.
- Trích xuất yêu cầu (requirements).
- Xác định thông vị còn thiếu.
- Phân biệt giữa requirements (user yêu cầu) vs assumptions (AI giả định).
- Xác định premise, genre, tone, romantic dynamic, conflict.
- **Xác nhận Genre Default:** Nếu `story_idea.md` không tự chỉ định bối cảnh/văn hóa riêng, AI phải nêu rõ cho user biết truyện sẽ mặc định theo `system/CONFIG/genre_config.md` (Ngôn tình Trung Quốc: bối cảnh, tên nhân vật kiểu Trung Quốc, cách xưng hô...) và hỏi user có muốn giữ mặc định này hay đổi sang bối cảnh khác trước khi sang Phase 2.
- Đánh giá độ phức tạp của cốt truyện:
  + Nếu cốt truyện PHỨC TẠP: Dừng lại và gợi ý cho người dùng rằng cốt truyện này cần mở rộng hơn 10 chương. Nếu người dùng đồng ý, hãy hỏi họ về số chương mong muốn. Nếu người dùng không đồng ý, AI bắt buộc phải gói gọn câu chuyện trong tối đa 10 chương.
  + Nếu cốt truyện ĐƠN GIẢN: Bắt buộc phải gói gọn trong 3-10 chương.
- Flag cho user nếu có thông tin quan trọng bị thiếu làm ảnh hưởng toàn bộ câu chuyện.\n