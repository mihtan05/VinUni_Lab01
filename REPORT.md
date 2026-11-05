# Báo cáo thu hoạch Lab 01: Nền tảng LLM API

## 1. Những việc đã làm
- Tích hợp trực tiếp ba dịch vụ AI phổ biến (OpenAI, Google Gemini, Anthropic Claude), chuẩn hóa toàn bộ dữ liệu trả về theo cùng một cấu trúc gồm nội dung phản hồi, độ trễ và số lượng token tiêu thụ.
- Đo lường & so sánh xây dựng công cụ gửi cùng một câu hỏi đến nhiều mô hình để đối chiếu tốc độ và tự động tính toán chi phí thực tế theo lượng token sử dụng.
- Dựng chatbot có ngữ cảnh: Xây dựng ứng dụng trò chuyện trên dòng lệnh hỗ trợ hiển thị chữ theo thời gian thực (streaming) và tự động ghi nhớ các lượt hội thoại gần nhất
- Xử lý sự cố: Bổ sung cơ chế tự động thử lại khi hệ thống gặp lỗi mạng hoặc quá tải.

---

## 2. Bài học rút ra
- Gom các chuẩn API khác nhau về một định dạng chung ngay từ đầu giúp việc thay đổi hoặc thử nghiệm các mô hình mới trở nên linh hoạt và tiết kiệm thời gian chỉnh sửa logic.
- Tiếng Việt có dấu tiêu tốn nhiều token hơn tiếng Anh. Trong khi đó, các dòng mô hình nhẹ (Flash, Mini) rẻ hơn hàng chục lần so với dòng cao cấp mà tốc độ lại vượt trội, rất phù hợp cho phần lớn tác vụ cơ bản.
- Mô hình không tự nhớ nội dung trò chuyện, nhưng gửi lại toàn bộ lịch sử sẽ khiến chi phí token tăng rất nhanh. Việc giới hạn chỉ giữ lại vài lượt trao đổi gần nhất là giải pháp tối ưu để vừa duy trì ngữ cảnh, vừa kiểm soát chi phí. Đồng thời, kỹ thuật truyền chữ theo thời gian thực giúp người dùng không cảm thấy ứng dụng bị treo hay phải chờ đợi lâu.
- Code chạy đúng trong môi trường thử nghiệm chưa chắc đã chạy ổn định khi kết nối thật. Việc tài khoản hết hạn mức, bị giới hạn số lượt gọi hay máy chủ quá tải luôn có thể xảy ra, đòi hỏi ứng dụng phải luôn có cơ chế tự động thử lại và phương án sử dụng mô hình dự phòng.

