[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112795&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 2A202600928@student.fpt.edu.vn
**Name:** Nguyễn Việt Hoàng

---

## Mo ta

Bài Lab 10 tập trung vào việc xây dựng một đường ống ETL (Extract, Transform, Load) cơ bản và đánh giá tầm quan trọng của Data Observability thông qua việc kiểm tra chất lượng dữ liệu. Tôi đã hoàn thiện pipeline ETL trong `solution.py` và tiến hành chạy Stress Test để quan sát ảnh hưởng của Garbage Data đối với Agent thông qua mô phỏng.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Tao file garbage_data.csv
python generate_garbage.py

# Chay mo phong Agent voi Clean Data va Garbage Data
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- Pipeline đã đọc 5 bản ghi từ `raw_data.json`.
- Qua quá trình validation, 2 bản ghi lỗi bị loại bỏ và 3 bản ghi hợp lệ được giữ lại.
- Dữ liệu được tính thêm `discounted_price`, chuẩn hóa `category` và thêm mốc thời gian `processed_at`, lưu vào file `processed_data.csv`.
- Kết quả Stress Test cho thấy Garbage Data khiến AI Agent đưa ra những nhận định hoàn toàn sai lệch (ví dụ: tư vấn mua "Nuclear Reactor" thay vì đồ điện tử thật).
