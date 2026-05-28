# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp (0.0), câu trả lời có xu hướng rất chính xác, ngắn gọn và ít sáng tạo, nội dung ổn định hơn mỗi lần gọi. Khi temperature tăng lên 0.5 và 1.0, câu trả lời trở nên phong phú hơn, có thêm chi tiết và biểu đạt đa dạng hơn. Ở 1.5, mô hình dễ xuất hiện các câu sáng tạo hơn nhưng cũng kém dự đoán hơn và đôi khi có thể thêm thông tin không cần thiết.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature vào khoảng 0.2–0.5 để ưu tiên tính nhất quán và chính xác. Với chatbot hỗ trợ khách hàng, câu trả lời ổn định và ít bị sáng tạo quá mức quan trọng hơn, giúp giảm nguy cơ sai lệch thông tin.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Với tổng số token 10.000 × 3 × 350 = 10.500.000 token mỗi ngày, chi phí GPT-4o là khoảng 10.500 × 0.01 = 105 USD, còn GPT-4o-mini là khoảng 10.500 × 0.0006 = 6.3 USD. Như vậy GPT-4o đắt hơn khoảng 16,7 lần so với GPT-4o-mini.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi ứng dụng cần câu trả lời chính xác, lý luận sâu, tổng hợp dữ liệu phức tạp hoặc tạo nội dung chất lượng cao, ví dụ như tư vấn kỹ thuật, phân tích pháp lý, hoặc viết nội dung chuyên sâu. GPT-4o-mini phù hợp với các ứng dụng chat đơn giản, hỗ trợ khách hàng cơ bản, tìm kiếm thông tin nhanh hoặc xử lý khối lượng lớn khi chi phí là yếu tố quan trọng.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi người dùng tương tác trực tiếp qua chat hoặc voice assistant và cần phản hồi nhanh, vì nó tạo cảm giác phản hồi tức thì và giảm thời gian chờ. Non-streaming phù hợp hơn với các tác vụ offline, xử lý batch hoặc khi cần thu thập toàn bộ kết quả trước khi hiển thị, ví dụ như báo cáo tự động, phân tích dữ liệu, hoặc khi tốc độ hiển thị từng token không phải là ưu tiên.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
