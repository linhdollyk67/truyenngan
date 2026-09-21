# Kỹ năng: Plot Hole Checker
Kiểm tra logic nguyên nhân - kết quả theo nguyên tắc tại `system/RULES/plot_rules.md` (nhân-quả, Chekhov's Gun, nhân vật không hành động dựa trên thông tin chưa biết).
Đọc `MEMORY/unresolved_threads.md`: nếu đang ở chương cuối/Phase Finalize mà vẫn còn thread OPEN, đây là CRITICAL ISSUE.
Output: PASS hoặc ISSUES FOUND (kèm Issue, Severity, Evidence, Suggested fix).\n