# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600928
**Name:** Nguyễn Việt Hoàng
**Date:** 10/06/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Trả lời chính xác với dữ liệu thực tế. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Agent bị đánh lừa bởi outliers và fake records. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi sử dụng Garbage Data, dữ liệu đầu vào chứa nhiều bản ghi nhiễu (như giá trị ngoại lai, sản phẩm không hợp lý như "Nuclear Reactor" với giá cực cao hoặc các bản ghi có loại dữ liệu sai, null values...). Agent chỉ dựa vào logic tìm kiếm thô (tìm giá cao nhất trong danh mục "electronics") mà không có cơ chế lọc, đánh giá tính logic hay làm sạch trước, dẫn đến việc trả về một sản phẩm hoàn toàn phi lý. Việc không làm sạch dữ liệu trước khiến cho Agent coi "rác" cũng là tri thức hợp lệ và trả về kết quả sai lệch.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Đồng ý.

Một prompt tốt đến đâu cũng không thể bù đắp được nếu nền tảng tri thức (dữ liệu đầu vào) mà Agent sử dụng bị sai lệch hoặc chứa nhiễu (Garbage In, Garbage Out). Dữ liệu chất lượng cao là cốt lõi để đảm bảo Agent có đủ thông tin đúng, từ đó đưa ra phản hồi chính xác và tin cậy. Dù prompt có tối ưu cách mấy, Agent vẫn sẽ phân tích và trả lời sai nếu bị "nhồi nhét" những dữ liệu ngoại lai hay phi thực tế.
