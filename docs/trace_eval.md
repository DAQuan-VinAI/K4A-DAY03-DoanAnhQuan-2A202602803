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
    "output": "Chào bạn! Quy chế học vụ của Đại học VinUni bao gồm nhiều quy định cơ bản về việc học tập của sinh viên, bao gồm:\n\n1. **Đăng ký và tham gia khóa học**: Sinh viên cần đăng ký các môn học trong thời gian quy định và phải tham gia đầy đủ các buổi học.\n\n2. **Điểm số và đánh giá**: Sinh viên sẽ được đánh giá qua các bài kiểm tra, bài tập lớn, và điểm cuối kỳ. Điểm số thường được tính theo thang điểm 10 và có quy định về cách tính điểm tổng kết.\n\n3. **Vắng mặt và bảo lưu**: Có quy định về việc xin phép vắng mặt trong các buổi học và quy trình để bảo lưu kết quả học tập.\n\n4. **Khen thưởng và kỷ luật**: Đại học VinUni có các quy định về việc khen thưởng sinh viên xuất sắc và xử lý các hành vi vi phạm quy chế học vụ.\n\n5. **Hỗ trợ học vụ**: Sinh viên có quyền nhận hỗ trợ từ các cố vấn học tập để giải quyết các vấn đề liên quan đến học tập và thời gian biểu.\n\nBạn cần thông tin chi tiết hơn về bất kỳ điểm nào trong quy chế trên không?",
    "latency_ms": 3866.57
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
    "latency_ms": 2152.49
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenAI phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Thông tin học vụ của sinh viên SV2026001 như sau:\n\n- **Họ và tên:** Nguyễn Văn An\n- **Lớp:** AI-K4\n- **Điểm trung bình (GPA):** 3.85\n- **Email:** an.nv@vinuni.edu.vn\n- **Trạng thái học tập:** Đang học\n- **Cố vấn học tập:** PGS.TS Nguyễn Văn A\n\nNếu bạn cần thêm thông tin nào khác, hãy cho tôi biết!",
    "latency_ms": 1312.8
  },
  {
    "step": 1,
    "query": "tra cứu thông tin SV2026001, sau đó tra cứu thông tin SV2026002, sau đó đặt lịch cho SV2026001 6:00 ngày 1/10/2026",
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
    "latency_ms": 1283.74
  },
  {
    "step": 2,
    "query": "tra cứu thông tin SV2026001, sau đó tra cứu thông tin SV2026002, sau đó đặt lịch cho SV2026001 6:00 ngày 1/10/2026",
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
    "latency_ms": 1007.67
  },
  {
    "step": 3,
    "query": "tra cứu thông tin SV2026001, sau đó tra cứu thông tin SV2026002, sau đó đặt lịch cho SV2026001 6:00 ngày 1/10/2026",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "student_id": "SV2026001",
      "datetime_str": "01/10/2026 06:00",
      "advisor_name": "PGS.TS Nguyễn Văn A"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026001-99",
      "student_id": "SV2026001",
      "datetime": "01/10/2026 06:00",
      "advisor": "PGS.TS Nguyễn Văn A",
      "message": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 01/10/2026 06:00."
    },
    "latency_ms": 1324.52
  },
  {
    "step": 4,
    "query": "tra cứu thông tin SV2026001, sau đó tra cứu thông tin SV2026002, sau đó đặt lịch cho SV2026001 6:00 ngày 1/10/2026",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenAI phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Thông tin đã tra cứu:\n\n1. **Sinh viên SV2026001:**\n   - Họ và tên: Nguyễn Văn An\n   - Lớp: AI-K4\n   - GPA: 3.85\n   - Email: an.nv@vinuni.edu.vn\n   - Trạng thái: Đang học\n   - Cố vấn học tập: PGS.TS Nguyễn Văn A\n\n2. **Sinh viên SV2026002:**\n   - Họ và tên: Trần Thị Bình\n   - Lớp: AI-K4\n   - GPA: 3.6\n   - Email: binh.tt@vinuni.edu.vn\n   - Trạng thái: Đang học\n   - Cố vấn học tập: TS. Lê Thị B\n\n3. **Lịch hẹn:**\n   - Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc **01/10/2026 06:00**. Mã đặt lịch: BK-SV2026001-99.\n\nNếu bạn cần thêm thông tin hoặc hỗ trợ nào khác, hãy cho tôi biết!",
    "latency_ms": 2048.58
  },
  {
    "step": 1,
    "query": "Thay đổi mail sinh viên SV2026001 mail thành 123@gmail.com",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenAI phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Để cập nhật địa chỉ email cho sinh viên SV2026001 thành 123@gmail.com, tôi cần tiến hành hành động này. Tuy nhiên, việc thay đổi thông tin hồ sơ sinh viên là hành động nhạy cảm và cần phê duyệt.\n\nVui lòng xác nhận bạn muốn thực hiện thay đổi này không?",
    "latency_ms": 1155.5
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
    "latency_ms": 984.57
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV20260705.",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenAI phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Không tìm thấy dữ liệu học vụ của sinh viên với mã SV20260705. Có thể mã sinh viên này không chính xác hoặc chưa được đăng ký trong hệ thống. Bạn có thể kiểm tra lại mã sinh viên của mình hoặc cung cấp một mã khác để tôi tra cứu thêm.",
    "latency_ms": 1069.49
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [X] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini/OpenAI).
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 5 lượt.
- **Kết quả đẩy Repo nộp bài:** [X] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
