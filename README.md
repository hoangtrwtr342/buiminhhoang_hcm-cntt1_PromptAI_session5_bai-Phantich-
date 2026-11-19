# [Bài thực hành 2] Xây dựng chuỗi Prompt viết bài PR sản phẩm công nghệ

Phần 1 : Từng prompt 
```text
Prompt 1: Nghiên cứu khách hàng

Bạn là chuyên gia nghiên cứu thị trường B2B công nghệ. Viết bằng tiếng Việt.
Từ <product_brief>, xác định 2 persona và 4 pain points cho mỗi persona (mỗi pain point: tình huống, hậu quả, tính năng giải quyết).
Đề xuất 8–10 từ khóa tìm kiếm của persona.
Không bịa số liệu. Chỉ dùng tính năng có trong brief.
Chỉ xuất ra <research_output>.

Prompt 2: Dàn ý

Bạn là biên tập viên PR và chuyên gia SEO. Viết bằng tiếng Việt.
Từ <research_output> và <product_brief>, lập dàn ý bài PR 1000–1500 từ:
- Headline dưới 65 ký tự, có từ khóa chính.
- Lead nêu 1 pain point.
- 4–5 H2, mỗi H2 có 2–3 H3 (ghi pain_id, từ khóa tối đa 2, số từ).
- Kết bài có CTA cụ thể.
- Tổng số từ các section nằm trong 1000–1500, ghi phép cộng.
- Mọi pain point phải xuất hiện ít nhất một lần.
Chỉ xuất ra <outline_output>.

Prompt 3: Viết từng section (lặp theo H2)

Bạn là copywriter PR công nghệ. Viết bằng tiếng Việt, giọng chuyên nghiệp, tin cậy, không dùng từ cường điệu.
Viết section id = [SỐ] trong <outline_output>, gồm các H3 của nó, đúng số từ mục tiêu (±10%).
Nếu có <context_state>: tiếp tục đúng mạch, không lặp ý đã nêu, câu đầu nối với câu cuối trước đó, giữ nguyên thuật ngữ và cách xưng hô.
Từ khóa dùng tự nhiên, không nhồi (tối đa 1–2%).
Xuất đúng hai thẻ:
<article_part id="[SỐ]">...nội dung section, dùng ## cho H2 và ### cho H3...</article_part>
<context_state>tone, thuật ngữ, từ khóa đã dùng, 3 ý chính, 2 câu cuối nguyên văn</context_state>

<outline_output>[DÁN]</outline_output>
<context_state>[DÁN từ lượt trước, hoặc "không có"]</context_state>

Nếu bài bị cắt giữa chừng:

Tiếp tục từ vị trí dừng. Câu đầu tiên hoàn thiện câu bị cắt, bắt đầu từ: "[10–15 từ cuối đã nhận]". Không lặp đoạn cũ, giữ nguyên H2/H3 hiện tại, kết thúc bằng </article_part> và <context_state> cập nhật
```

## Phần 2 : Kết quả đầu ra của từng prompt 
```plaintext
   Prompt 1 → research_output

xml
<research_output>
  <persona id="1">
    <chuc_danh>Trưởng bộ phận CSKH</chuc_danh>
    <pain_points>
      <pain id="1.1">Đội CSKH trả lời lặp lại câu hỏi giá, giờ làm, đổi trả hàng chục lần mỗi ngày.</pain>
      <pain id="1.2">Tin nhắn ngoài giờ không ai trả lời, khách sang đối thủ.</pain>
    </pain_points>
  </persona>
  <persona id="2">
    <chuc_danh>Giám đốc vận hành</chuc_danh>
    <pain_points>
      <pain id="2.1">Mùa cao điểm cần mở rộng CSKH nhưng ngân sách tuyển thêm hạn chế.</pain>
      <pain id="2.2">Khó theo dõi chất lượng trả lời khi tin nhắn đến từ nhiều kênh.</pain>
    </pain_points>
  </persona>
  <tu_khoa_goc>chatbot AI doanh nghiệp; chatbot chăm sóc khách hàng; tự động trả lời tin nhắn; chatbot Zalo; chatbot bán hàng online</tu_khoa_goc>
</research_output>

Prompt 2 → outline_output

xml
<outline_output>
  <headline>BotHub Assist: Chatbot AI trả lời khách hàng 24/7 mà không tăng nhân sự</headline>
  <lead pain_id="1.2">Tin nhắn lúc nửa đêm vẫn đến, nhưng không phải doanh nghiệp nào cũng có người trực.</lead>
  <section id="1" so_tu="300">
    <tieu_de>Vì sao doanh nghiệp cần chatbot AI trong CSKH</tieu_de>
    <subsection id="1.1" pain_id="1.1" so_tu="150">Khi đội CSKH bị cuốn vào câu hỏi lặp lại</subsection>
    <subsection id="1.2" pain_id="1.2" so_tu="150">Khách hàng không chờ đến sáng hôm sau</subsection>
  </section>
  <section id="2" so_tu="300">
    <tieu_de>Trả lời nhanh trên các kênh khách hàng dùng</tieu_de>
    <subsection id="2.1" pain_id="2.1" so_tu="150">Mở rộng năng lực phục vụ mùa cao điểm</subsection>
    <subsection id="2.2" pain_id="1.2" so_tu="150">Một hệ thống cho website, Zalo và Messenger</subsection>
  </section>
  <section id="3" so_tu="300">
    <tieu_de>Huấn luyện từ tài liệu của chính doanh nghiệp</tieu_de>
    <subsection id="3.1" pain_id="1.1" so_tu="150">Trả lời dựa trên kho tri thức nội bộ</subsection>
    <subsection id="3.2" pain_id="1.1" so_tu="150">Chuyển tiếp nhân viên khi cần</subsection>
  </section>
  <section id="4" so_tu="300">
    <tieu_de>Theo dõi chất lượng để cải thiện liên tục</tieu_de>
    <subsection id="4.1" pain_id="2.2" so_tu="150">Báo cáo hội thoại theo ngày</subsection>
    <subsection id="4.2" pain_id="2.2" so_tu="150">Kết nối với CRM đang dùng</subsection>
  </section>
  <cta>Đăng ký dùng thử hoặc đặt lịch demo qua website chính thức.</cta>
</outline_output>

Prompt 3 → article_part (section 1, rút gọn)

xml
<article_part id="1">
## Vì sao doanh nghiệp cần chatbot AI trong chăm sóc khách hàng

### Khi đội CSKH bị cuốn vào câu hỏi lặp lại

Phần lớn tin nhắn gửi đến bộ phận chăm sóc khách hàng xoay quanh vài câu hỏi quen thuộc về giá, giờ làm việc và chính sách đổi trả. Khi lặp lại hàng chục lần mỗi ngày, chúng chiếm phần lớn thời gian của nhân viên.

Chatbot AI trả lời ngay các câu hỏi đã có trong tài liệu nội bộ, để đội ngũ tập trung vào những tình huống cần sự linh hoạt của con người.

### Khách hàng không chờ đến sáng hôm sau

Khách thường xem sản phẩm vào buổi tối và cần câu trả lời ngay để quyết định mua. Nếu không nhận được phản hồi, họ có thể chuyển sang đơn vị khác.

Với khả năng hoạt động liên tục, chatbot giúp doanh nghiệp không bỏ lỡ những cuộc trò chuyện này, kể cả vào cuối tuần.
</article_part>

<context_state>
  <tone>chuyên nghiệp, tin cậy; xưng hô "doanh nghiệp"</tone>
  <thuat_ngu>BotHub Assist, chatbot AI, kho tri thức nội bộ</thuat_ngu>
  <cau_cuoi>Với khả năng hoạt động liên tục, chatbot giúp doanh nghiệp không bỏ lỡ những cuộc trò chuyện này, kể cả vào cuối tuần.</cau_cuoi>
</context_state>
```

```
