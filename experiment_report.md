# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600087
**Name:** Khuất Văn Vương
**Date:** 15-4-2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario                          | Agent Response                                                   | Accuracy (1-10) | Notes                                                |
| --------------------------------- | ---------------------------------------------------------------- | --------------- | ---------------------------------------------------- |
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200.            | 9               | Dữ liệu hợp lệ, giá trị hợp lý, kết quả đáng tin cậy |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 2               | Xuất hiện outlier và dữ liệu sai lệch nghiêm trọng   |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent trả lời sai khi dùng Garbage Data vì chất lượng dữ liệu đầu vào bị nhiễu hoặc sai lệch. Trong bộ dữ liệu này có thể tồn tại các vấn đề như:

- Outliers: Ví dụ Nuclear Reactor với giá $999999 là không thực tế trong ngữ cảnh mua sắm thông thường, nhưng agent vẫn chọn vì giá cao nhất.
- Sai kiểu dữ liệu: Nếu price hoặc category bị sai định dạng, quá trình xử lý có thể không loại bỏ được dữ liệu lỗi.
- Thiếu validation chặt chẽ: Pipeline chỉ kiểm tra price > 0 và category != None, chưa đủ để loại các giá trị bất thường.
- Dữ liệu không liên quan: Nuclear Reactor không phù hợp domain nhưng vẫn lọt vào hệ thống.
- Duplicate hoặc nhiễu: Có thể làm sai thống kê hoặc bias kết quả.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Đồng ý

Dữ liệu chất lượng cao quan trọng hơn prompt vì AI chỉ có thể đưa ra kết quả tốt nếu dữ liệu đầu vào đáng tin cậy. Một prompt tốt không thể cứu được dữ liệu sai hoặc nhiễu. Ngược lại, dữ liệu sạch và đúng sẽ giúp AI hoạt động hiệu quả ngay cả với prompt đơn giản. Vì vậy, đảm bảo data quality là yếu tố cốt lõi trong mọi hệ thống AI.
