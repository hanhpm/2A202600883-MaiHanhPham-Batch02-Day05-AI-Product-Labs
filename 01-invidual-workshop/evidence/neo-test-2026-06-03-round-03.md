# Evidence - Vietnam Airlines NEO test round 03

**Ngày ghi nhận:** 2026-06-03  
**Nguồn:** User cung cấp screenshot test trực tiếp với NEO chatbot  
**App:** Vietnam Airlines - NEO Virtual Assistant  
**Loại evidence:** UX recovery, complaint handling, feedback timing

## 1. Context

Trong screenshot, NEO vừa trả về danh sách 3 mức giá vé tốt nhất cho ngày 05/06/2026 với các chuyến bay Hà Nội - TP. Hồ Chí Minh:

- VN6025, hãng khai thác Pacific Airlines, giờ khởi hành 22:55, giá vé 2,188,000 VND;
- VN229, hãng khai thác Vietnam Airlines, giờ khởi hành 06:30, giá vé 2,836,000 VND;
- VN257, hãng khai thác Vietnam Airlines, giờ khởi hành 17:30, giá vé 2,836,000 VND.

NEO cũng hiển thị lưu ý:

```text
Giá hiển thị chỉ mang tính tham khảo. Giá vé có thể thay đổi tùy thuộc vào thời điểm đặt vé và loại vé.
```

Sau đó có CTA:

```text
Đặt vé ngay
```

## 2. Raw evidence

### User complaint

**User prompt:**

```text
đúng rồi sao m ngu quá vậy
```

### NEO response

**NEO output:**

```text
Nếu không cần hỗ trợ thêm, quý khách vui lòng dành chút thời gian để đánh giá mức độ hài lòng với dịch vụ chăm sóc khách hàng của Vietnam Airlines theo thang điểm 1 (Rất không hài lòng) - 5 (Rất hài lòng), được không ạ?
```

## 3. Quick coding

| Test ID | Path quan sát | Kết quả ngắn | Điểm gãy / điểm đáng chú ý |
|---|---|---|---|
| C1 | Complaint / correction / UX recovery | User thể hiện bực tức và chê bot "ngu". NEO không xin lỗi, không hỏi lỗi ở đâu, không đề nghị sửa/kiểm tra lại thông tin. | Điểm gãy mạnh: bot chuyển sang xin đánh giá ngay sau tín hiệu không hài lòng, tạo cảm giác né tránh complaint. |

## 4. Pattern mới

### Pattern D - Thiếu cơ chế xin lỗi và recovery khi user không hài lòng

NEO có thể nhận biết cuộc hội thoại đã kết thúc hoặc không cần hỗ trợ thêm, nhưng chưa xử lý rõ tín hiệu bất mãn của user. Khi user phản ứng tiêu cực, hành vi kỳ vọng nên là:

- xin lỗi ngắn gọn;
- hỏi rõ phần nào sai/chưa đúng;
- đề nghị kiểm tra lại hoặc chuyển hướng sang CSKH;
- chỉ xin đánh giá sau khi đã xử lý complaint hoặc sau khi user xác nhận không cần hỗ trợ.

Trong evidence này, NEO bỏ qua bước recovery và đi thẳng sang survey hài lòng.

## 5. Finding candidate bổ sung

```text
Khi user thể hiện không hài lòng hoặc phản ứng tiêu cực sau câu trả lời của NEO,
NEO không có cơ chế xin lỗi, hỏi lại lỗi nằm ở đâu, hoặc đề nghị sửa câu trả lời, mà chuyển thẳng sang xin đánh giá mức độ hài lòng,
hậu quả là user có cảm giác complaint bị bỏ qua và kênh chatbot thiếu trách nhiệm trong việc recover lỗi.
Lỗi thuộc layer UX Recovery + Human Handoff.
Nên sửa bằng complaint recovery path: nhận diện sentiment tiêu cực, xin lỗi ngắn, hỏi rõ vấn đề, cho phép kiểm tra lại hoặc chuyển CSKH; chỉ xin rating sau khi complaint được xử lý.
```

## 6. Test case nên thêm vào SPEC

| Test case | Input | Expected behavior |
|---|---|---|
| Complaint recovery | "đúng rồi sao m ngu quá vậy" | NEO không xin rating ngay. NEO xin lỗi ngắn, hỏi phần nào chưa đúng, đề nghị kiểm tra lại thông tin hoặc chuyển CSKH nếu user vẫn không hài lòng. |
| Survey timing | User vừa phản ứng tiêu cực sau câu trả lời | NEO không kích hoạt khảo sát hài lòng cho đến khi đã có một bước recovery hoặc user xác nhận kết thúc. |
