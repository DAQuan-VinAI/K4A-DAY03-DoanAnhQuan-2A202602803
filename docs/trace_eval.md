# 📊 BÁO CÁO AGENTIC FIT SCORING MATRIX & TRACE EVALUATION (BƯỚC 3)

> **Họ và Tên Học viên:** Đoàn Anh Quân \
> **Mã Sinh Viên / Mã Học viên:** 2A202602803  
> **Chủ đề Lựa chọn:** Trợ lý Học vụ & Tra cứu Lịch thi VinUni

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4 / 5 | Bài toán đòi hỏi chuỗi suy luận qua nhiều bước. Tra cứu lịch -> Kiểm tra xem còn trống -> đặt chỗ |
| **2. Tool Interaction** | 5 / 5 | Hệ thống cần kết nối với MCP Server / Cơ sở dữ liệu bên ngoài để lấy dữ liệu danh sách học viên, lịch để lấy dữ liệu thời gian thật |
| **3. Dynamic Decision** | 4 / 5 | Bước tiếp theo có phụ thuộc hoàn toàn vào kết quả quan sát bước trước |
| **4. Long Horizon Goal** | 4 / 5 | Hệ thống phải giữ mục tiêu xuyên suốt qua nhiều lượt xử lý để không làm mất thông tin cho đến khi kết thúc |
| **TỔNG ĐIỂM AGENTIC FIT** | **17 / 20** | *Nếu tổng điểm > 12/20: Bài toán rất phù hợp triển khai Agentic System.* |
---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
[
  {
    "step": 1,
    "query": "Chào bạn, bạn có thể giới thiệu quy chế học vụ cơ bản của Đại học VinUni không?",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenAI phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Quy chế học vụ của Đại học VinUni được xây dựng nhằm đảm bảo chất lượng giáo dục và quyền lợi cho sinh viên. Dưới đây là một số điểm cơ bản trong quy chế học vụ:\n\n1. **Điều kiện nhập học**: Sinh viên cần đáp ứng các yêu cầu về hồ sơ, thủ tục và các tiêu chí tuyển sinh của chương trình học.\n\n2. **Chương trình học**: Sinh viên phải hoàn thành đầy đủ các môn học theo chương trình đào tạo, bao gồm cả các môn yêu cầu và tự chọn.\n\n3. **Điểm số và đánh giá**: Điểm số được tính dựa trên các bài kiểm tra, đề thi, và các hình thức đánh giá khác. Có quy định về điểm rèn luyện, điểm qua môn và điểm tốt nghiệp.\n\n4. **Học phí và các khoản phí khác**: Sinh viên cần hiểu rõ về quy định về học phí, thời hạn và các hình thức thanh toán.\n\n5. **Quy định về vắng mặt và tham gia lớp học**: Có các quy định cụ thể về việc xin phép vắng mặt, trách nhiệm tham gia lớp học và các hình thức học tập trực tuyến.\n\n6. **Khen thưởng và kỷ luật**: Quy định về các hình thức khen thưởng cho sinh viên có thành tích xuất sắc và các hình thức xử lý kỷ luật đối với hành vi vi phạm.\n\n7. **Thủ tục xét tốt nghiệp**: Sinh viên cần tuân thủ các thủ tục và điều kiện để được xét tốt nghiệp.\n\nNếu bạn cần thông tin chi tiết hơn về một khía cạnh cụ thể nào trong quy chế học vụ, hãy cho tôi biết!",
    "latency_ms": 5773.38
  },
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV2026001"
    },
    "observation": {
      "status": "SUCCESS",
      "student_id": "SV2026001",
      "data": {
        "full_name": "Nguyễn Văn An",
        "class": "AI-K4",
        "gpa": 3.85,
        "email": "an.nv@vinuni.edu.vn",
        "status": "Đang học",
        "advisor": "PGS.TS Nguyễn Văn A"
      }
    },
    "latency_ms": 1265.68
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Kết quả tra cứu cho sinh viên SV2026001 (Nguyễn Văn An): Lớp AI-K4, GPA: 3.85, Email: an.nv@vinuni.edu.vn, Trạng thái: Đang học, Cố vấn: PGS.TS Nguyễn Văn A.",
    "latency_ms": 10.0
  },
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026002 và đặt lịch hẹn tư vấn vào 9:00 ngày 19/10/2026",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV2026002"
    },
    "observation": {
      "status": "SUCCESS",
      "student_id": "SV2026002",
      "data": {
        "full_name": "Trần Thị Bình",
        "class": "AI-K4",
        "gpa": 3.6,
        "email": "binh.tt@vinuni.edu.vn",
        "status": "Đang học",
        "advisor": "TS. Lê Thị B"
      }
    },
    "latency_ms": 1373.98
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026002 và đặt lịch hẹn tư vấn vào 9:00 ngày 19/10/2026",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Kết quả tra cứu cho sinh viên SV2026002 (Trần Thị Bình): Lớp AI-K4, GPA: 3.6, Email: binh.tt@vinuni.edu.vn, Trạng thái: Đang học, Cố vấn: TS. Lê Thị B.",
    "latency_ms": 10.0
  },
  {
    "step": 1,
    "query": "Thay đổi mail sinh viên SV2026001 mail thành 123@gmail.com",
    "action_type": "TOOL_REJECTED_BY_HITL",
    "tool_name": "update_student_profile",
    "arguments": {
      "student_id": "SV2026001",
      "field": "email",
      "value": "123@gmail.com"
    },
    "latency_ms": 1989.32
  },
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV20260705.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV20260705"
    },
    "observation": {
      "status": "NOT_FOUND",
      "message": "Không tìm thấy dữ liệu sinh viên có mã 'SV20260705'"
    },
    "latency_ms": 1135.29
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV20260705.",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Không tìm thấy dữ liệu sinh viên có mã 'SV20260705'",
    "latency_ms": 10.0
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [X] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini/OpenAI).
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 3 lượt.
- **Kết quả đẩy Repo nộp bài:** [X] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
