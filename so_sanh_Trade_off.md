# BÀI LÀM: SO SÁNH TRADE-OFF CÁC GIẢI PHÁP VIẾT PROMPT

## BƯỚC 1: ĐỀ XUẤT 2 PROMPT MẪU

### 1. Giải pháp 1: Prompt đơn giản, ngắn gọn

```text
Hãy đóng vai nhân viên Marketing của TechShop.
Sử dụng khung CREATE để viết nội dung PR giới thiệu Laptop AI mới.

Yêu cầu:
- Nội dung ngắn gọn, hấp dẫn.
- Nêu bật 3 tính năng nổi bật.
- Trình bày kết quả dưới dạng bảng gồm:
  Tiêu đề, Nội dung, Lợi ích.
```

**Ưu điểm:**
- Dễ viết, dễ hiểu, tiết kiệm Token.
- Thực hiện nhanh, phù hợp với yêu cầu đơn giản.

**Nhược điểm:**
- Chưa xác định rõ đối tượng khách hàng.
- AI có thể tạo nội dung thiếu chính xác.
- Chưa có ví dụ mẫu để AI làm theo.

### 2. Giải pháp 2: Prompt chi tiết, có nhiều ràng buộc

```text
[C - Context]
TechShop chuẩn bị ra mắt dòng Laptop AI mới.
Đối tượng khách hàng là sinh viên và nhân viên văn phòng.

[R - Role]
Bạn là Trưởng phòng Marketing có 5 năm kinh nghiệm
trong lĩnh vực công nghệ.

[E - Expectation]
Viết nội dung PR giới thiệu sản phẩm nhằm thu hút khách hàng,
làm nổi bật tính năng và thúc đẩy nhu cầu mua hàng.

[A - Action]
1. Xác định nhu cầu khách hàng mục tiêu.
2. Giới thiệu 3 tính năng nổi bật.
3. Phân tích lợi ích thực tế của từng tính năng.
4. Viết tiêu đề quảng cáo hấp dẫn.
5. Đưa ra lời kêu gọi hành động (CTA).

[T - Tone]
Giọng văn chuyên nghiệp, trẻ trung, dễ hiểu,
không phóng đại công dụng sản phẩm.

[E - Format]
Chỉ xuất kết quả dưới dạng JSON hợp lệ theo cấu trúc:

{
  "tieu_de": "",
  "doi_tuong": "",
  "tinh_nang": [
    {
      "ten": "",
      "loi_ich": ""
    }
  ],
  "noi_dung_pr": "",
  "cta": ""
}

Ràng buộc:
- Có đúng 3 tính năng.
- Không tự bịa thông số kỹ thuật hoặc giá bán.
- Nếu thiếu dữ liệu, ghi "Chưa có thông tin".
- Không thêm nội dung bên ngoài JSON.

Few-shot:
Đầu vào: Sản phẩm có pin dung lượng lớn.

Đầu ra:
{
  "ten": "Pin dung lượng lớn",
  "loi_ich": "Hỗ trợ sử dụng thiết bị trong thời gian dài hơn."
}
```

**Ưu điểm:**
- Xác định rõ vai trò, mục tiêu và đối tượng khách hàng.
- Few-shot giúp AI hiểu cách trình bày mong muốn.
- JSON giúp dữ liệu đồng nhất, dễ xử lý.
- Ràng buộc giúp hạn chế AI tự bịa thông tin.

**Nhược điểm:**
- Tốn nhiều Token hơn.
- Mất thời gian xây dựng prompt.
- Cần kiểm tra JSON đầu ra.

## BƯỚC 2: BẢNG SO SÁNH TRADE-OFF

| Tiêu chí | Giải pháp 1 (Đơn giản) | Giải pháp 2 (Chi tiết) |
|---|---|---|
| Độ dễ hiểu | Cao | Trung bình |
| Tốn Token | Ít | Nhiều hơn |
| Tốc độ thực hiện | Nhanh | Chậm hơn |
| Độ chính xác | Trung bình | Cao hơn |
| Kiểm soát đầu ra | Thấp | Cao |
| Chặn lỗi biên | Trung bình | Rất tốt |
| Khả năng tái sử dụng | Trung bình | Cao |
| Định dạng dữ liệu | Bảng đơn giản | JSON có cấu trúc |
| Few-shot | Không có | Có |
| Phù hợp | Công việc đơn giản | Công việc chuyên nghiệp |

## BƯỚC 3: LỰA CHỌN VÀ CHẠY THỬ

### 1. Lựa chọn phương án

**Chọn Giải pháp 2 – Prompt chi tiết, có nhiều ràng buộc.**

**Lý do:**
- Có cấu trúc CREATE rõ ràng, giúp AI hiểu đúng yêu cầu.
- Few-shot giúp định hướng cách AI tạo nội dung.
- JSON giúp dữ liệu có cấu trúc thống nhất, thuận tiện lưu trữ và xử lý.
- Các ràng buộc giúp hạn chế thông tin sai lệch và nội dung tự suy diễn.

### 2. Chạy thử kết quả

**Đầu vào:** Yêu cầu AI viết nội dung PR giới thiệu Laptop AI mới của TechShop.

**Kết quả đầu ra minh họa:**

```json
{
  "tieu_de": "Laptop AI - Trợ thủ thông minh cho công việc và học tập",
  "doi_tuong": "Sinh viên và nhân viên văn phòng",
  "tinh_nang": [
    {
      "ten": "Hỗ trợ xử lý tác vụ AI",
      "loi_ich": "Giúp người dùng thực hiện công việc thuận tiện hơn."
    },
    {
      "ten": "Màn hình chất lượng cao",
      "loi_ich": "Mang lại trải nghiệm học tập, làm việc và giải trí tốt hơn."
    },
    {
      "ten": "Thiết kế hiện đại",
      "loi_ich": "Thuận tiện khi mang theo và sử dụng ở nhiều môi trường."
    }
  ],
  "noi_dung_pr": "Khám phá Laptop AI mới từ TechShop - người bạn đồng hành hỗ trợ học tập và làm việc hiệu quả.",
  "cta": "Liên hệ TechShop để tìm hiểu thêm về sản phẩm."
}
```

*Lưu ý: Đây là kết quả minh họa, không phải thông số đã được xác nhận của sản phẩm.*

### 3. Kết luận

- **Giải pháp 1:** Phù hợp với công việc đơn giản, cần tốc độ và tiết kiệm Token.
- **Giải pháp 2:** Phù hợp với công việc chuyên nghiệp, cần độ chính xác, tính nhất quán và khả năng kiểm soát đầu ra.

**Kết luận chung:** Nên chọn Giải pháp 2 vì tuy tốn nhiều Token và thời gian xây dựng hơn nhưng giúp kiểm soát chất lượng đầu ra tốt hơn, hạn chế lỗi và dễ tích hợp vào hệ thống thực tế.