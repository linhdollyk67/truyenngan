# Thể loại: Ngôn Tình Trung Quốc (Chinese Romance Web Novels)
Mặc định toàn bộ các câu chuyện được tạo ra từ framework này đều thuộc thể loại **Ngôn Tình**. 

**Yêu cầu bắt buộc về thể loại:**
- **Bối cảnh & Văn hóa:** Sử dụng bối cảnh, văn hóa, và cách diễn đạt đặc trưng của truyện ngôn tình Trung Quốc (hoặc bối cảnh tương đương).
- **Cách xưng hô & Tên gọi:** Ưu tiên sử dụng tên nhân vật kiểu Trung Quốc (nếu user không chỉ định tên cụ thể). Cách xưng hô phải phù hợp với thiết lập quan hệ (ví dụ: tổng tài, thư ký, thiếu gia, ảnh đế, v.v.).
- **Trọng tâm:** Luôn phải là mối quan hệ tình cảm giữa hai nhân vật chính. Các yếu tố khác (công việc, gia đình, thương trường, showbiz) chỉ làm nền để phát triển hoặc tạo rào cản cho mối quan hệ này.

*Lưu ý quy trình: Đây là default toàn cục. `idea_analyzer` (Phase 1) bắt buộc phải xác nhận với user rằng đang áp dụng default này trước khi sang Phase 2, để user có cơ hội đổi bối cảnh nếu muốn (xem `system/SKILLS/idea_analyzer.md`).*

## Kho Trope & Quy ước thường gặp (tham khảo khi thiết kế, không bắt buộc dùng hết)
- **Bạch nguyệt quang / Chu sa nốt ruồi**: người yêu cũ/tình đầu được lý tưởng hoá còn vướng bận so với hiện tại.
- **Thanh mai trúc mã**: bạn thời thơ ấu phát triển thành tình yêu.
- **Hợp đồng hôn nhân / Giả kết hôn**: hai người kết hôn vì lý do thực dụng (tiền, danh dự, thừa kế), tình cảm nảy sinh sau.
- **Ngộ nhận thân phận**: một bên giấu thân phận thật (tổng tài giấu mặt, người thừa kế ẩn danh...).
- **Tổng tài ngã nước / bá đạo tổng tài**: nam/nữ chính quyền lực, lạnh lùng bên ngoài, chiếm hữu/áp đặt trong tình cảm (giới hạn bắt buộc xem tại `system/RULES/romance_rules.md`).
- **Gia tộc đối đầu / Hôn nhân sắp đặt vì lợi ích gia tộc**: xung đột gia đình/kinh doanh làm rào cản tình cảm.
- **Xa cách nhiều năm rồi tái ngộ**: khoảng trống thời gian cần lấp bằng flashback được kiểm soát chặt continuity (xem `system/RULES/continuity_rules.md`).
- **Tráo đổi thân phận (con nuôi/con ruột, tiểu thư giả/thật)**: motif thân phận đặc trưng của ngôn tình gia tộc.

*Mọi trope khi dùng vẫn phải tuân thủ toàn bộ `system/RULES/*` — đặc biệt `plot_rules.md` (nhân-quả, không lạm dụng hiểu lầm) và `romance_rules.md` (mức độ áp đặt cho phép).*\n