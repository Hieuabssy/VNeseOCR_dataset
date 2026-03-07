# Dataset OCR Đại Việt Sử Ký Toàn Thư

Đây là bộ dữ liệu OCR (Nhận dạng quang học ký tự) cho tác phẩm lịch sử "Đại Việt sử ký toàn thư". Bộ dữ liệu bao gồm các trang ảnh chụp từ sách và nhãn (label) tương ứng chứa nội dung văn bản và tọa độ khung bao.

## Mô tả dữ liệu

Bộ dữ liệu gồm các thư mục chứa ảnh và file nhãn.
- Ảnh: Các trang sách được chụp lại (định dạng .jpg).
- Nhãn: File `Label.txt` chứa thông tin tóm tắt và tọa độ chữ.

## Định dạng nhãn (Label.txt)

File nhãn thường có định dạng từng dòng, mỗi dòng tương ứng với một ảnh:
`Đường_dẫn_ảnh [TAB] Danh_sách_JSON`

Trong đó danh sách JSON chứa các đối tượng có trường:
- `transcription`: Nội dung chữ trong ảnh.
- `points`: Tọa độ khung bao (bounding box) của dòng chữ.
- `difficult`: Độ khó (true/false).

Ví dụ dữ liệu từ Label.txt:
`dai viet su ky toan thu-tap 3 --477(ảnh Việt)/page_7.jpg [{"transcription": "KY HIEU VA CHU VIÉT TAT", "points": [[670, 700], [1302, 700], ...], "difficult": false}, ...]`

## Phân tích thống kê dữ liệu

### Dữ liệu Thô
- Số lượng 6,858 dòng dữ liệu ban đầu được tạo ra tự động bởi công cụ PPOCRLabel.
- Số lượng này bao gồm các dòng bị trùng lặp, các dòng không chứa nội dung văn bản (ví dụ: các dòng trống, ký hiệu, hoặc các bbox lỗi), và các dòng bị cắt không trọn vẹn do sai sót của thuật toán phát hiện vùng (bbox).

### Dữ liệu Đã Xử Lý
- Sau quá trình hiệu chỉnh thủ công và gióng hàng (alignment) nội dung, số lượng mẫu dữ liệu đã giảm xuống còn 6,220 mẫu.
- Sự khác biệt này (giảm 638 mẫu, tương đương khoảng 9.3%) thể hiện số lượng dữ liệu lỗi, trùng lặp hoặc không hợp lệ đã được loại bỏ hoặc hợp nhất để đảm bảo mỗi mẫu dữ liệu cuối cùng là một dòng văn bản hợp lệ, trọn vẹn và có nhãn chính xác.
- Tổng dung lượng ảnh giảm nhẹ từ 166 MB xuống còn khoảng 150 MB do việc loại bỏ các file ảnh crop lỗi hoặc trùng lặp.

## Tải dữ liệu

Bạn có thể tải bộ dữ liệu đầy đủ tại liên kết sau:
https://drive.google.com/drive/folders/1l_TSgZANnLaArrKgk2TbZZQahpUd4nrB
