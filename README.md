# Đụt — bản demo

Mở file `index.html` bằng trình duyệt (Chrome, Edge, Firefox, Safari) là chơi được, không cần cài gì.

Điều khiển:
- Máy tính: phím ← → (hoặc A, D) để đi, phím cách / ↑ / W để nhảy. Giữ phím nhảy lâu thì nhảy cao hơn.
- Điện thoại: chạm góc trái dưới để đi trái/phải, chạm nửa phải màn hình để nhảy.
- Lúc Đụt thức giấc: chạm hoặc nhấn phím cách theo nhịp tim.

## Các màn trong demo
1. **Mở đầu:** chỉ có dòng 4/5/2026, rồi chiếc hộp giày hiện ra trong bóng tối.
2. **Thức giấc:** mỗi lần chạm theo nhịp tim, Đụt chui ra khỏi hộp và Hành tinh Meo sáng dần lên: sao trời, cực quang, hành tinh có vành đai, đảo bay, nấm phát sáng.
3. **Đồng cỏ bạc hà mèo:** đi cảnh 2D. Đụt nhảy qua vực và các đảo nổi, nhặt bóng màu; mỗi quả bóng là một nốt của bài hát của Đụt. Rơi xuống vực thì Đụt hiện lại ở đèn lồng gần nhất, không mất gì. Cuối màn là cổng ánh sáng.
4. **Ký ức – căn phòng:** căn phòng quen thuộc với đồng hồ, tủ lạnh, khay vệ sinh, tủ bếp, bếp và cửa phòng ngủ. Có 5 dấu chân phát sáng, mỗi chỗ là một ký ức: đi vệ sinh rồi quay lại cào cát, hất quả bóng rồi đuổi theo vồ, ngồi nhìn đồng hồ chờ chủ về, nằm sưởi cạnh bếp, và chủ (ngẫu nhiên nam hoặc nữ) từ phòng ngủ bước ra, mở tủ lạnh lấy kem hoặc sữa chua rồi quỳ xuống cho Đụt ăn. Gom đủ 5 ký ức thì cửa phòng ngủ mở ra.
5. **Thung lũng nắng:** Đụt ngồi một mình nhìn quanh, rồi từng bạn mèo lần lượt tới ngồi, nằm cạnh. Cả nhóm cùng chớp mắt chậm, Đụt nằm xuống giữa các bạn và gửi sao băng về Trái Đất.

Vào ngày 4/5 có thêm pháo hoa ở màn cuối. Muốn xem trước, mở `index.html#45`.

## Thay hình của Đụt
Tất cả khung hình của Đụt nằm chung trong **một sprite sheet**: `sprites/dut_sheet.png`. Các khung được dựng từ ảnh Đụt pixel bạn vẽ: tư thế ngồi dùng nguyên ảnh gốc, các tư thế khác dùng đúng cái đầu trong ảnh gốc và vẽ thêm thân cùng bảng màu. Các bạn mèo là Đụt đổi bảng màu.
Mở `sprite_guide.png` (bản phóng to có lưới và nhãn từng ô) để biết ô nào là tư thế nào.

Sheet là lưới ô vuông 40×40 px, 4 cột, 7 hàng:

| Hàng | Nội dung | Ghi chú |
|---|---|---|
| 0 | Đi bộ, 4 khung | Thứ tự: sải bước → chân khép → sải bước ngược → chân khép. Khung chân khép nên nhô thân lên 1 px |
| 1 | Ngồi, 4 khung | Ô thứ 3 (cột 2) là khung chớp mắt; các ô khác vẫy đuôi nhẹ |
| 2 | Nằm, 4 khung | Mở mắt, lim dim, nhắm, ngủ |
| 3 | Ăn, 4 khung | Cúi đầu xuống (bát/hũ sữa chua do game tự vẽ phía trước) |
| 4 | Nhảy lên, rơi xuống, vươn vai, ngơ ngác | Mỗi tư thế 1 khung |
| 5 | Đứng yên | 1 khung |
| 6 | Cào cát, 4 khung | Cúi thấp, một chân trước giơ lên → với ra → gạt xuống → kéo về |

Lưu ý khi vẽ:
- Đụt quay mặt sang **phải**, chân chạm **mép dưới** của ô. Khi đi sang trái game tự lật hình.
- Không cần vẽ bóng dưới chân, game tự vẽ bóng đổ.
- Muốn vẽ ô lớn hơn (ví dụ 48×48), đổi `SHEET.cell` và `SPRITE_BOX.cat` trong `index.html` và vẽ cả sheet theo kích thước mới.
- Muốn thêm khung cho một hoạt ảnh, vẽ thêm ô vào hàng đó (sheet có thể rộng hơn 4 cột) rồi thêm số cột vào `frames` của hoạt ảnh trong bảng `SHEET.anims`. Tốc độ chỉnh ở `fps`.

**Các bạn mèo ở màn cuối** nằm trong `sprites/friends_sheet.png`: lưới 40×40, 8 cột (đi 1–4, ngồi, ngồi chớp mắt, nằm, nằm ngủ), mỗi hàng một bạn: Cam (cam trắng), Bông (mèo trắng), Mun (đen trắng), Tam thể, Kem (mèo con, game vẽ nhỏ hơn). Muốn đổi chỗ đứng hay thời điểm xuất hiện của từng bạn, sửa bảng `FRIENDS` trong `index.html`.

**Người trong ký ức tủ lạnh** nằm trong `sprites/people_sheet.png`: ô 40×84, hàng 0 là nữ (tóc đen ngang vai, lô cuốn trên mái, đầm hồng hoa nhí), hàng 1 là nam (tóc đen layer, áo thun đen, quần đùi đen). 9 cột: đi 1–4, đứng, với tay mở tủ, cầm đồ, quỳ, quỳ đưa đồ ăn. Quay mặt sang phải.

Các hình khác vẫn là file riêng: `box_base.png` (thân hộp giày 40×22), `box_lid.png` (nắp hộp 44×7), `ball_*.png` (bóng 5 màu 10×10).

Nhạc và âm thanh được tạo trực tiếp bằng code (Web Audio), không cần file âm thanh.
