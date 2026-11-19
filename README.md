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
