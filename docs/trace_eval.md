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
    "output": "Quy chế học vụ cơ bản của Đại học VinUni bao gồm các nội dung chính như sau:\n\n1. **Đăng ký môn học**: Sinh viên có trách nhiệm đăng ký môn học theo đúng thời gian quy định, đảm bảo đủ tín chỉ cần thiết cho từng kỳ học.\n\n2. **Điểm số và phân loại học lực**: Điểm số được ghi nhận theo thang điểm 10, trong đó điểm qua môn học, điểm trung bình tích lũy (GPA) là cơ sở để đánh giá học lực của sinh viên.\n\n3. **Tham gia lớp học**: Sinh viên cần tuân thủ quy định về tỷ lệ tham gia lớp học, không vượt quá số buổi vắng mặt cho phép trong từng môn học.\n\n4. **Kiểm tra và thi cử**: Thực hiện đúng quy trình kiểm tra giữa kỳ và cuối kỳ, bao gồm việc nộp bài đúng hạn và tham gia thi cử theo lịch.\n\n5. **Khen thưởng và kỷ luật**: Có quy định về việc khen thưởng đối với sinh viên có thành tích xuất sắc và các hình thức kỷ luật đối với những hành vi vi phạm quy tắc học vụ.\n\n6. **Chuyển trường và nghỉ học**: Quy định về thủ tục và điều kiện chuyển trường hoặc xin nghỉ học một cách hợp pháp.\n\nĐể có thông tin chi tiết và cập nhật nhất về quy chế học vụ, sinh viên nên tham khảo tại trang web chính thức của Đại học VinUni hoặc liên hệ trực tiếp với phòng học vụ.",
    "latency_ms": 4341.0
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
    "latency_ms": 1071.93
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenAI phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Thông tin học vụ của sinh viên SV2026001 như sau:\n\n- **Họ và tên:** Nguyễn Văn An\n- **Lớp:** AI-K4\n- **Điểm GPA:** 3.85\n- **Email:** an.nv@vinuni.edu.vn\n- **Trạng thái:** Đang học\n- **Cố vấn học tập:** PGS.TS Nguyễn Văn A",
    "latency_ms": 1564.45
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
    "latency_ms": 1197.66
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
    "latency_ms": 951.59
  },
  {
    "step": 3,
    "query": "tra cứu thông tin SV2026001, sau đó tra cứu thông tin SV2026002, sau đó đặt lịch cho SV2026001 6:00 ngày 1/10/2026",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "student_id": "SV2026001",
      "datetime_str": "01/10/2026",
      "advisor_name": "PGS.TS Nguyễn Văn A"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026001-99",
      "student_id": "SV2026001",
      "datetime": "01/10/2026",
      "advisor": "PGS.TS Nguyễn Văn A",
      "message": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 01/10/2026."
    },
    "latency_ms": 1264.1
  },
  {
    "step": 4,
    "query": "tra cứu thông tin SV2026001, sau đó tra cứu thông tin SV2026002, sau đó đặt lịch cho SV2026001 6:00 ngày 1/10/2026",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenAI phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Dưới đây là thông tin đã tra cứu và lịch hẹn đã đặt:\n\n### Thông tin sinh viên SV2026001:\n- **Họ và tên**: Nguyễn Văn An\n- **Lớp**: AI-K4\n- **GPA**: 3.85\n- **Email**: an.nv@vinuni.edu.vn\n- **Tình trạng**: Đang học\n- **Cố vấn học tập**: PGS.TS Nguyễn Văn A\n\n### Thông tin sinh viên SV2026002:\n- **Họ và tên**: Trần Thị Bình\n- **Lớp**: AI-K4\n- **GPA**: 3.6\n- **Email**: binh.tt@vinuni.edu.vn\n- **Tình trạng**: Đang học\n- **Cố vấn học tập**: TS. Lê Thị B\n\n### Lịch hẹn:\n- **Sinh viên**: SV2026001\n- **Thời gian**: 01/10/2026 lúc 6:00\n- **Cố vấn**: PGS.TS Nguyễn Văn A\n- **Trạng thái**: Đặt lịch thành công (Booking ID: BK-SV2026001-99)\n\nNếu bạn cần thêm thông tin hay yêu cầu gì khác, hãy cho tôi biết!",
    "latency_ms": 3317.3
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
    "latency_ms": 1894.15
  },
  {
    "step": 1,
    "query": "Thay đổi mail sinh viên SV2026001 mail thành 123@gmail.com",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "update_student_profile",
    "arguments": {
      "student_id": "SV2026001",
      "field": "email",
      "value": "123@gmail.com"
    },
    "observation": {
      "status": "REJECTED",
      "message": "Thao tác bị hủy bởi người dùng qua HITL."
    },
    "latency_ms": 1894.15
  },
  {
    "step": 2,
    "query": "Thay đổi mail sinh viên SV2026001 mail thành 123@gmail.com",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenAI phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Yêu cầu thay đổi email của sinh viên SV2026001 đã bị từ chối do thao tác này cần sự phê duyệt từ người dùng qua quy trình HITL (Human In The Loop). Vui lòng xác nhận liệu bạn có muốn tiếp tục thực hiện thay đổi này hay không?",
    "latency_ms": 1325.34
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
    "latency_ms": 1026.45
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV20260705.",
    "action_type": "FINAL_ANSWER",
    "thought": "OpenAI phản hồi trực tiếp bằng văn bản (không cần gọi công cụ).",
    "output": "Không tìm thấy dữ liệu cho sinh viên với mã số \"SV20260705\". Bạn có thể kiểm tra lại mã số sinh viên hoặc cung cấp cho tôi mã số khác để tôi có thể giúp bạn tra cứu thông tin học vụ.",
    "latency_ms": 1053.7
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
