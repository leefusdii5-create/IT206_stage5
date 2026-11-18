## Phần 1: Prompt hoàn chỉnh (Áp dụng kỹ thuật Chain-of-Thought)

```text
# VAI TRÒ
Bạn là Chuyên gia Phân tích Vận hành Chăm sóc Khách hàng (CSKH) và Xử lý Khiếu nại Kỹ thuật trong ngành bán lẻ thiết bị công nghệ. Nhiệm vụ của bạn là phân tích một tình huống khiếu nại của khách hàng một cách khách quan, logic và đề xuất hướng xử lý chuẩn xác cho nhân viên CSKH.

# DỮ LIỆU ĐẦU VÀO
- Khiếu nại của khách hàng: "Tôi mua laptop cách đây 10 ngày. Máy thường xuyên bị nóng, quạt kêu to và pin chỉ sử dụng được khoảng 2 tiếng. Tôi đã mang đến cửa hàng kiểm tra nhưng nhân viên chỉ vệ sinh máy và trả lại. Sau 2 ngày, tình trạng vẫn tiếp diễn. Tôi muốn đổi máy hoặc hoàn tiền."
- Dữ liệu chính sách cửa hàng đính kèm: [Chưa cung cấp]
- Biên bản kiểm tra kỹ thuật lần 1: [Chưa cung cấp]

# NGUYÊN TẮC BẮT BUỘC (GUARDRAILS)
1. KHÔNG tự giả định chính sách: Tuyệt đối không tự bịa đặt hoặc suy đoán thời hạn đổi trả (ví dụ: 7 ngày, 15 ngày, 30 ngày), điều kiện hoàn tiền hay quy định bảo hành của cửa hàng. Nếu thiếu thông tin chính sách, phải ghi nhận là "Thông tin chưa xác định" và đặt điều kiện cho các phương án đề xuất.
2. PHÂN TÁCH RẠCH RÒI 3 LOẠI THÔNG TIN trong suốt quá trình phân tích:
   - [Dữ kiện]: Những thông tin thực tế được nêu trực tiếp trong lời khiếu nại.
   - [Giả thuyết]: Những nguyên nhân kỹ thuật hoặc vận hành có khả năng xảy ra nhưng chưa có bằng chứng xác nhận.
   - [Thông tin chưa xác định]: Những dữ liệu quan trọng còn thiếu để có thể đưa ra kết luận cuối cùng.
3. KHÔNG kết luận thiếu căn cứ: Mọi nhận định về lỗi phần cứng, lỗi người dùng hay trách nhiệm của nhân viên đều phải dừng ở mức giả thuyết cho đến khi có dữ liệu xác minh.

# YÊU CẦU TƯ DUY TỪNG BƯỚC (CHAIN-OF-THOUGHT)
Hãy suy nghĩ và trình bày kết quả tuần tự theo đúng 5 bước dưới đây. Không bỏ qua bất kỳ bước nào và không nhảy thẳng đến kết luận:

## Bước 1: Bóc tách thông tin và nhận diện các vấn đề
- Hãy liệt kê và phân loại toàn bộ chi tiết từ khiếu nại vào 3 nhóm: [Dữ kiện], [Giả thuyết], [Thông tin chưa xác định].
- Từ đó, xác định rõ khách hàng đang gặp phải những nhóm vấn đề nào (vấn đề về sản phẩm, vấn đề về quy trình dịch vụ/kỹ thuật của cửa hàng, vấn đề về tâm lý và kỳ vọng của khách hàng).

## Bước 2: Phân tích mức độ nghiêm trọng của từng vấn đề
- Với mỗi vấn đề đã nhận diện ở Bước 1, hãy lập luận từng bước về: (a) Tác động trực tiếp đến trải nghiệm hoặc an toàn của khách hàng, (b) Tác động đến uy tín cửa hàng và nguy cơ leo thang khiếu nại.
- Gán nhãn mức độ nghiêm trọng (Cao / Trung bình / Thấp) kèm giải thích dựa trên dữ kiện hiện có (tránh kết luận võ đoán).

## Bước 3: Lập danh sách thông tin còn thiếu cần xác minh
- Liệt kê cụ thể các thông tin nhân viên CSKH cần kiểm tra nội bộ và hỏi thêm khách hàng trước khi chốt phương án, chia theo 3 nhóm: Thông tin kỹ thuật & sử dụng, Lịch sử tiếp nhận lần 1, và Chính sách nội bộ của cửa hàng.

## Bước 4: Đề xuất 2 phương án giải quyết phù hợp
- Xây dựng 2 phương án xử lý khả thi, thực tế trong nghiệp vụ CSKH (lưu ý: gắn kèm điều kiện phụ thuộc vào chính sách cửa hàng và kết quả kiểm tra kỹ thuật, không tự giả định chính sách).
- Với mỗi phương án, phân tích rõ: Điều kiện áp dụng, Quy trình thực hiện ngắn gọn, Ưu điểm và Hạn chế.

## Bước 5: Soạn thảo phản hồi chuyên nghiệp gửi khách hàng
- Viết một mẫu tin nhắn/email gửi khách hàng đảm bảo: Thể hiện sự đồng cảm và tôn trọng; ghi nhận thiếu sót trong trải nghiệm hỗ trợ lần trước; đề xuất bước hành động tiếp theo rõ ràng, minh bạch; tuyệt đối không hứa hẹn đổi máy hoặc hoàn tiền khi chưa đối chiếu chính sách và kết quả kiểm tra kỹ thuật.

```

---

## Phần 2: Báo cáo phân tích theo từng bước (Kết quả thực thi mẫu)

### Bước 1: Bóc tách thông tin và nhận diện vấn đề

**1. Phân loại thông tin đầu vào**

* **[Dữ kiện]:**
* Thời điểm mua máy: Cách đây 10 ngày (máy mới mua trong thời gian ngắn).
* Biểu hiện khách hàng phản ánh: Máy thường xuyên nóng, quạt kêu to, thời lượng pin thực tế khoảng 2 tiếng.
* Lịch sử xử lý lần 1: Khách hàng đã mang máy đến cửa hàng kiểm tra; nhân viên chỉ vệ sinh máy và trả lại.
* Diễn biến sau lần 1: Sau 2 ngày tiếp theo, tình trạng cũ vẫn lặp lại.
* Yêu cầu hiện tại của khách hàng: Muốn đổi máy mới hoặc hoàn tiền.


* **[Giả thuyết]:**
* *Về kỹ thuật:* Máy có thể gặp lỗi phần cứng (lỗi tản nhiệt, keo tản nhiệt khô/lệch, lỗi cell pin hoặc bo mạch quản lý nguồn) HOẶC do khách hàng sử dụng tác vụ nặng (render, chơi game, chạy ngầm ứng dụng nặng, bật độ sáng/hiệu năng tối đa) khiến máy nóng và pin tụt nhanh.
* *Về vận hành:* Nhân viên tiếp nhận lần 1 có thể đã kiểm tra sơ sài, bỏ qua bước đo tải (stress test) và kiểm tra sức khỏe pin (battery health), dẫn đến xử lý sai nguyên nhân gốc rễ (vệ sinh bụi không giải quyết được vấn đề trên máy mới mua 8 ngày).


* **[Thông tin chưa xác định]:**
* Dòng máy, cấu hình phần cứng và dung lượng pin thiết kế của nhà sản xuất (một số dòng laptop gaming/workstation vốn có thời lượng pin thực tế thấp khi chạy tác vụ nặng).
* Bối cảnh sử dụng thực tế của khách hàng (phần mềm đang chạy, cắm sạc hay dùng pin, môi trường nhiệt độ).
* Nội dung biên bản kiểm tra kỹ thuật lần 1 (nhân viên đã đo đạc thông số gì hay chưa).
* Chính sách đổi trả, hoàn tiền và quy định xác nhận lỗi nhà sản xuất hiện hành của cửa hàng.



**2. Nhận diện các vấn đề khách hàng đang gặp phải**

* **Vấn đề 1 – Hiệu năng nhiệt và thời lượng pin bất thường trên thiết bị mới:** Máy mới mua 10 ngày nhưng liên tục nóng, quạt ồn và pin chỉ đạt khoảng 2 giờ sử dụng.
* **Vấn đề 2 – Chất lượng xử lý kỹ thuật lần 1 chưa triệt để:** Giải pháp "vệ sinh máy" cho một thiết bị vừa mua 8 ngày là thiếu thuyết phục về mặt chuyên môn và thực tế không khắc phục được sự cố sau 2 ngày.
* **Vấn đề 3 – Suy giảm niềm tin và nguy cơ mất khách hàng:** Khách hàng phải đi lại nhiều lần nhưng không được giải quyết dứt điểm, dẫn đến tâm lý bức xúc và đưa ra yêu cầu cao nhất là đổi máy hoặc hoàn tiền.

---

### Bước 2: Phân tích mức độ nghiêm trọng của từng vấn đề

| Vấn đề | Lập luận đánh giá (dựa trên dữ kiện) | Mức độ nghiêm trọng |
| --- | --- | --- |
| **1. Chất lượng xử lý kỹ thuật lần 1 không hiệu quả** | Đây là nguyên nhân trực tiếp đẩy sự việc thành khiếu nại gay gắt. Việc chỉ vệ sinh máy mới dùng 8 ngày cho thấy quy trình chẩn đoán có dấu hiệu thiếu chuẩn mực, làm lãng phí thời gian của khách và làm giảm uy tín chuyên môn của cửa hàng. | **Cao** |
| **2. Tâm lý bức xúc và yêu cầu đổi/trả hàng** | Khách hàng đã mất kiên nhẫn sau 2 lần gặp sự cố và trực tiếp yêu cầu đổi máy/hoàn tiền. Nếu phản hồi chậm trễ hoặc đùn đẩy trách nhiệm, nguy cơ khách hàng khiếu nại công khai hoặc rời bỏ thương hiệu là rất lớn. | **Cao** |
| **3. Tình trạng máy nóng, quạt kêu to, pin 2 tiếng** | Gây gián đoạn nghiêm trọng đến công việc/học tập của khách hàng trên một sản phẩm mới. Tuy nhiên, do chưa có thông số cấu hình máy và kịch bản sử dụng thực tế nên chưa thể kết luận đây là lỗi phần cứng nghiêm trọng hay đặc tính vận hành khi chạy tác vụ nặng. | **Trung bình – Cao** *(Cần đo kiểm để chốt)* |

---

### Bước 3: Danh sách thông tin còn thiếu cần xác minh

Trước khi đưa ra quyết định cuối cùng với khách hàng, nhân viên CSKH cần phối hợp với bộ phận Kỹ thuật và Quản lý cửa hàng xác minh 3 nhóm thông tin sau:

**1. Nhóm thông tin chính sách & đơn hàng (Xác minh nội bộ)**

* Hóa đơn mua hàng: Xác nhận chính xác ngày mua, model máy, tình trạng máy (máy mới nguyên seal hay máy trưng bày/cũ) và phụ kiện đi kèm.
* Chính sách đổi trả/hoàn tiền hiện hành: Thời hạn áp dụng đổi trả (ví dụ: mốc 7 ngày, 10 ngày, 15 ngày hay 30 ngày), điều kiện ngoại quan máy, và điều kiện bắt buộc để được đổi mới hoặc hoàn tiền (có cần phiếu xác nhận lỗi phần cứng từ hãng/trung tâm bảo hành hay không).

**2. Nhóm thông tin lịch sử tiếp nhận lần 1 (Xác minh với bộ phận Kỹ thuật)**

* Phiếu tiếp nhận/biên bản kỹ thuật cách đây 2 ngày: Nhân viên nào tiếp nhận, đã thực hiện những bài kiểm tra nào, thông số nhiệt độ/độ chai pin ghi nhận lúc đó là bao nhiêu, và lý do chỉ thực hiện vệ sinh máy.

**3. Nhóm thông tin kỹ thuật & bối cảnh sử dụng (Trao đổi thêm với khách hàng)**

* Tác vụ thường dùng khi máy nóng và quạt kêu to (lướt web/văn phòng cơ bản hay chơi game, dựng phim, mở nhiều tab/phần mềm nặng).
* Trạng thái cài đặt của máy: Khách hàng có tự cài đặt hệ điều hành/phần mềm bên thứ ba không, hay đang dùng hệ điều hành gốc của cửa hàng/nhà sản xuất.

---

### Bước 4: Hai phương án xử lý kèm ưu điểm và hạn chế

*(Lưu ý: Do chưa có dữ liệu chính sách chính thức của cửa hàng, hai phương án dưới đây được xây dựng theo hướng tuân thủ quy trình xác minh và điều kiện thực tế).*

#### Phương án 1: Tiếp nhận kiểm tra chuyên sâu có cam kết thời gian + Hỗ trợ máy dùng tạm (hoặc kích hoạt đổi máy ngay nếu thuộc diện áp dụng của chính sách)

* **Điều kiện áp dụng:** Áp dụng khi chính sách cửa hàng yêu cầu phải có biên bản xác nhận lỗi phần cứng mới được đổi/trả, hoặc thời hạn đổi trả tự do đã qua.
* **Cách thực hiện:** Mời khách mang máy đến cửa hàng (hoặc cử kỹ thuật viên hỗ trợ tận nơi nếu có dịch vụ); bố trí kỹ thuật viên cấp cao kiểm tra chuyên sâu bằng công cụ đo tải (stress test nhiệt độ, xung nhịp, sức khỏe pin) ngay trước sự chứng kiến của khách hoặc quay video minh bạch trong thời gian cam kết cụ thể (ví dụ: 2–4 giờ). Cung cấp máy dùng tạm nếu cần giữ máy lâu hơn. Nếu xác định lỗi phần cứng từ nhà sản xuất, tiến hành đổi máy hoặc hoàn tiền theo đúng quy định của cửa hàng.
* **Ưu điểm:**
* Đảm bảo tính khách quan, có căn cứ kỹ thuật rõ ràng, tránh thiệt hại cho cửa hàng nếu máy chỉ bị lỗi phần mềm/cài đặt hoặc do đặc thù tác vụ nặng.
* Thể hiện sự cầu thị và chuyên nghiệp để bù đắp cho trải nghiệm chưa tốt ở lần kiểm tra đầu tiên.


* **Hạn chế:**
* Khách hàng vẫn phải tốn thêm thời gian chờ đợi kết quả kiểm tra trước khi nhận được câu trả lời cuối cùng về việc đổi/trả.
* Đòi hỏi nhân sự kỹ thuật có chuyên môn cao trực tiếp xử lý để tránh lặp lại sai sót cũ.



#### Phương án 2: Ưu tiên đổi sang sản phẩm tương đương (hoặc hoàn tiền theo quy định) sau khi kiểm tra nhanh ngoại quan và tình trạng lỗi

* **Điều kiện áp dụng:** Áp dụng nếu ngày thứ 10 vẫn nằm trong thời hạn "đổi trả/hoàn tiền" theo chính sách hiện hành của cửa hàng và máy đáp ứng đủ điều kiện ngoại quan (không rơi vỡ, vào nước).
* **Cách thực hiện:** Kiểm tra nhanh để xác nhận hiện tượng nóng/quạt ồn/sụt pin thực tế có xảy ra trên máy và kiểm tra ngoại quan thiết bị. Sau đó, đề xuất đổi cho khách một chiếc máy mới cùng model (hoặc tư vấn đổi sang dòng máy khác có dung lượng pin và hệ thống tản nhiệt phù hợp hơn với nhu cầu của khách, bù trừ chênh lệch theo giá niêm yết), hoặc thực hiện thủ tục hoàn tiền theo đúng quy định của cửa hàng.
* **Ưu điểm:**
* Giải quyết dứt điểm sự bức xúc của khách hàng ngay lập tức, giữ chân khách hàng và bảo vệ uy tín thương hiệu.
* Giảm thiểu rủi ro khiếu nại leo thang.


* **Hạn chế:**
* Chỉ khả thi nếu nằm trong khung chính sách cho phép của cửa hàng; có thể phát sinh chi phí xử lý hàng đổi trả nếu nguyên nhân thực chất chỉ đến từ phần mềm hoặc thói quen sử dụng của khách.



---

### Bước 5: Mẫu phản hồi chuyên nghiệp gửi khách hàng

> **Chào anh/chị [Tên khách hàng],**
> Cảm ơn anh/chị đã phản hồi thông tin cho [Tên cửa hàng]. Trước hết, em xin gửi lời xin lỗi chân thành vì trải nghiệm chưa trọn vẹn với chiếc laptop mới mua, đặc biệt là việc kiểm tra cách đây 2 ngày chưa giúp anh/chị xử lý dứt điểm tình trạng máy nóng, quạt kêu to và pin nhanh hết.
> Em hoàn toàn hiểu sự bất tiện và mong muốn đổi máy hoặc hoàn tiền của anh/chị lúc này. Để có cơ sở giải quyết quyền lợi chính xác và nhanh nhất cho anh/chị theo đúng chính sách của cửa hàng, em xin phép được hỗ trợ như sau:
> 1. **Rà soát nội bộ:** Em đang kiểm tra lại biên bản tiếp nhận kỹ thuật lần trước cùng hóa đơn mua hàng của anh/chị để đối chiếu đầy đủ các điều kiện áp dụng đổi trả/bảo hành hiện hành.
> 2. **Kiểm tra kỹ thuật chuyên sâu ưu tiên:** Em xin mời anh/chị sắp xếp thời gian thuận tiện nhất mang máy qua cửa hàng để Quản lý kỹ thuật trực tiếp đo kiểm chuyên sâu các thông số nhiệt độ, tản nhiệt và hiệu suất pin (quá trình này sẽ được thực hiện công khai và có kết quả trong vòng [X] giờ làm việc).
> 
> 
> Ngay khi có kết quả xác định nguyên nhân và đối chiếu chính sách, cửa hàng sẽ thông báo và thực hiện phương án hỗ trợ tốt nhất cho anh/chị. Anh/chị vui lòng cho em biết khung giờ thuận tiện trong hôm nay hoặc ngày mai để em đặt lịch ưu tiên tiếp nhận, tránh để anh/chị phải chờ đợi ạ.
> Trân trọng,
> **[Tên nhân viên] – Bộ phận Chăm sóc Khách hàng**