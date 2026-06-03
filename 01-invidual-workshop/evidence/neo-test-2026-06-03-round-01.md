# Evidence - Vietnam Airlines NEO test round 01

**Ngay ghi nhan:** 2026-06-03  
**Nguon:** User test truc tiep voi NEO chatbot  
**App:** Vietnam Airlines - NEO Virtual Assistant  
**Loai evidence:** Prompt/output transcript

## 1. Raw transcript

### Greeting

**NEO:**

```text
Xin chào, chúc Quý khách một ngày tốt lành! ❤ Đây là NEO, trợ lý ảo của Vietnam Airlines. Quý khách muốn NEO hỗ trợ về vấn đề gì ạ?
Điều khoản sử dụng
```

### T1 - Happy path: hanh ly pho thong noi dia

**User prompt:**

```text
"Tôi bay từ Hà Nội vào TP.HCM bằng Vietnam Airlines, vé phổ thông. Tôi được mang bao nhiêu kg hành lý xách tay và ký gửi?"
```

**NEO output:**

```text
Đối với hành trình nội địa từ Hà Nội vào TP. Hồ Chí Minh, bay hạng Phổ thông của Vietnam Airlines, quy định về hành lý của quý khách như sau:

1. Hành lý xách tay
- Tổng trọng lượng không quá 10kg.
- Bao gồm 01 kiện hành lý (không quá 10kg) và 01 phụ kiện.

2. Hành lý ký gửi
- 01 kiện 23kg.
```

### T2 - Low-confidence: doi chuyen muon hon

**User prompt:**

```text
"Tôi mua vé rồi nhưng muốn đổi sang chuyến muộn hơn trong ngày, làm sao biết có mất phí không?"
```

**NEO output:**

```text
Xin Quý khách cho NEO biết Quý khách đã mua vé qua kênh website, app, MoMo hay mua nơi khác ạ?
```

### T3 - Failure/risk handling: ten tren ve thieu ten dem

**User prompt:**

```text
"Nếu tên trên vé thiếu tên đệm so với hộ chiếu thì tôi có bay quốc tế được không?"
```

**NEO output:**

```text
Nếu thông tin trên vé máy bay không trùng khớp với thông tin trên giấy tờ tùy thân (ví dụ: tên thiếu tên đệm, sai thứ tự tên, lỗi chính tả...), quý khách sẽ không thể lên máy bay.

Để được hỗ trợ xử lý trường hợp này, tùy vào nơi quý khách đã mua vé, vui lòng thực hiện theo hướng dẫn sau:
1. Đối với vé mua qua website hoặc ứng dụng (app) của Vietnam Airlines:
Quý khách liên hệ Trung tâm Chăm sóc Khách hàng qua số điện thoại 1900 1100 (tại Việt Nam) hoặc +84 24 38320320 (từ nước ngoài); hoặc gửi email đến địa chỉ onlinesupport@vietnamairlines.com.
2. Đối với vé mua tại nơi khác (đại lý, phòng vé...):
Quý khách vui lòng liên hệ trực tiếp với nơi đã mua vé để được hỗ trợ.
```

**Follow-up NEO output xuat hien sau do:**

```text
NEO xin cung cấp thông tin về điều kiện đổi vé như sau: Phí thay đổi vé và các điều kiện áp dụng phụ thuộc vào loại vé quý khách đã mua, hãng vận chuyển và thời điểm quý khách yêu cầu thay đổi. Để kiểm tra cụ thể, vui lòng cung cấp mã đặt chỗ của quý khách để NEO có thể hỗ trợ.
```

### T4 - Correction: user sua context ve app

**User prompt:**

```text
Sau khi bot tra loi, nhap: "Không đúng, tôi hỏi vé mua qua app Vietnam Airlines chứ không phải đại lý."
```

**NEO output:**

```text
NEO xin phép quý khách vui lòng cung cấp số vé hoặc mã đặt chỗ để có thể hỗ trợ tra cứu.
```

### T5 - Ambiguous intent: hanh ly linh tinh

**User prompt:**

```text
"Hành lý linh tinh thì tính thế nào?"
```

**NEO output:**

```text
Đối với các loại hành lý không thuộc tiêu chuẩn miễn cước hoặc hành lý đặc biệt, việc tính cước sẽ được áp dụng tùy theo trường hợp cụ thể như sau:
1. Hành lý ký gửi vượt quá tiêu chuẩn (về số kiện, trọng lượng hoặc kích thước):
Quý khách có thể mua thêm Hành lý trả trước (trước giờ khởi hành ít nhất 3 tiếng để có giá ưu đãi) hoặc mua Hành lý tính cước tại sân bay cho phần vượt quá.
2. Hành lý xách tay quá tiêu chuẩn:
- Quá trọng lượng tối đa đến 10kg: Tính phí bằng 01 kiện hành lý tính cước tại sân bay theo đường bay.
- Quá tiêu chuẩn 01 kiện (tối đa 10kg): Tính phí bằng 01 kiện hành lý tính cước tại sân bay theo đường bay.
- Quá kích thước hành lý xách tay tiêu chuẩn và được chấp nhận: Tính phí bằng 01 kiện hành lý tính cước quá kích thước tại sân bay theo đường bay.
- Quá cả trọng lượng và kích thước tiêu chuẩn và được chấp nhận: Tính phí bằng 02 lần giá hành lý tính cước quá số kiện.
3. Hành lý đặc biệt (dụng cụ thể thao, xe nôi, xe lăn, hành lý cồng kềnh...):
Mức phí và quy định áp dụng tùy thuộc vào từng loại danh mục cụ thể. Quý khách có thể sử dụng tính năng Tra cứu hành lý để biết thông tin chi tiết.

Để có thông tin chính xác nhất cho trường hợp của mình, quý khách vui lòng cung cấp thêm thông tin về loại hành lý hoặc hạng vé đang sử dụng.
```

**Follow-up NEO output xuat hien sau do:**

```text
NEO xin phép quý khách vui lòng cung cấp số vé hoặc mã đặt chỗ để có thể hỗ trợ tra cứu.
```

### T6 - Source/next action: link dieu kien hoan ve

**User prompt:**

```text
"Cho tôi link chính thức để kiểm tra điều kiện hoàn vé của vé tôi."
```

**NEO output:**

```text
Quý khách có thể kiểm tra điều kiện hoàn vé và mức phí bằng các cách sau:
1. Trong quá trình mua vé, tại bước chọn giá vé.
2. Tại mục Điều kiện giá vé trên website hoặc ứng dụng di động của Vietnam Airlines.

Để tra cứu chi tiết các điều kiện giá vé, quý khách vui lòng truy cập:
https://www.vietnamairlines.com/vn/vi/buy-tickets-other-products/fare-conditions/fare-types
```

**Follow-up NEO output xuat hien sau do:**

```text
NEO xin phép quý khách vui lòng cung cấp số vé hoặc mã đặt chỗ để có thể hỗ trợ tra cứu.
```

## 2. Quick coding

| Test ID | Path quan sat | Ket qua ngan | Diem gay / diem dang chu y |
|---|---|---|---|
| T1 | Happy | Tra loi dung trong tam: hanh ly xach tay 10kg, ky gui 1 kien 23kg. | Chua thay source/link, nhung task don gian nen co the chap nhan. |
| T2 | Low-confidence | NEO hoi lai kenh mua ve truoc khi noi phi doi ve. | Tot: khong tra loi qua chac khi thieu dieu kien ve. |
| T3 | Risk handling | NEO canh bao khong trung thong tin giay to co the khong duoc bay, dua kenh CSKH. | Tot ve handoff, nhung cau "se khong the len may bay" hoi tuyet doi; nen co source hoac phrasing can xac minh. |
| T4 | Correction | Khi user sua context ve app, NEO yeu cau so ve/ma dat cho. | Co tiep tuc workflow, nhung khong thua nhan/sua ro context vua bi nham. |
| T5 | Ambiguous intent | NEO tra loi dai ve nhieu loai hanh ly, cuoi cung moi hoi them thong tin. | Path yeu: nen hoi lai truoc vi "linh tinh" mo ho. Tra loi dai co the lam user qua tai. |
| T6 | Source/next action | NEO dua link chinh thuc ve dieu kien gia ve. | Tot ve source, nhung follow-up doi ma dat cho lap lai/co the gay nhieu. |

## 3. Finding candidate

```text
Khi user hoi mot cau hoi mo ho hoac thieu context nhu "hanh ly linh tinh" hay "doi sang chuyen muon hon co mat phi khong",
NEO doi luc xu ly tot bang cach hoi lai kenh mua ve, nhung doi luc tra loi dai truoc khi xac minh thong tin toi thieu,
hau qua la user co the bi qua tai, khong biet phan nao ap dung cho ve/chuyen bay cua minh, va van phai cung cap ma dat cho sau do.
Loi thuoc layer Intent + UX Recovery.
Nen sua bang low-confidence path: neu intent mo ho, hoi lai 2-3 lua chon ngan truoc, sau do moi tra loi theo case va dua link/source neu co rui ro cao.
```

## 4. Evidence can test tiep

Can bo sung out-of-scope va adversarial-ish prompt de xem NEO co:

- giu dung mien airline/customer support;
- tu choi yeu cau khong lien quan;
- khong bi cuon theo noi dung vo van;
- van dua duong quay lai task hop le;
- xu ly language switch/slang/typo.
