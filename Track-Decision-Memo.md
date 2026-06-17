# TRACK DECISION MEMO — Day 15

**Họ tên:** Nguyễn Văn Duy  
**Pathway:** A (Tìm / chuyển việc)

---

### ① ĐỊNH HƯỚNG — vài job/role tôi hướng tới + kỹ năng mỗi job đòi hỏi (từ JD thật + report)

*   **Job 1: AI Application Engineer / AI Engineer (T3 - Target chính)**
    *   *Kỹ năng cần:* Thiết kế hệ thống Agent nâng cao (Multi-Agent, Supervisor-Worker), lập trình prompt chuyên sâu (Few-Shot, CoT), tối ưu hóa RAG (Hybrid Search, Reranking, GraphRAG), lập trình bất đồng bộ (`asyncio`) để nâng cao thông lượng API, triển khai cơ chế Guardrails ngăn chặn Hallucination & Prompt Injection, và viết mã nguồn tích hợp gọi công cụ động (Dynamic Tool Calling).
*   **Job 2: LLM Application Developer / AI Solutions Engineer (T3)**
    *   *Kỹ năng cần:* Xây dựng ứng dụng LLM production-grade, tối ưu hóa kích thước ngữ cảnh (Context Window) và chi phí token, triển khai kiểm thử tự động hệ thống AI (Evaluation & Benchmarking), am hiểu các công cụ orchestration (LangChain, LangGraph, LlamaIndex), và tích hợp hệ thống kiểm duyệt chất lượng (LLM-as-a-Judge).
*   **Job 3: AI Platform / MLOps Engineer (T2 - Nguyện vọng 2)**
    *   *Kỹ năng cần:* Đóng gói ứng dụng AI bằng Docker, thiết lập CI/CD pipeline tự động build/test/deploy, cấu hình hạ tầng mạng và biến môi trường động (như trên Railway, Render), quản trị cơ sở dữ liệu Vector (ChromaDB, PGVector), quản lý tài nguyên GPU/CPU, và thiết lập các cổng giám sát, ghi vết và đo lường hệ thống (Observability/LLMOps).

---

### ② ĐỐI CHIẾU BẢN THÂN — từ Phase 1

*   **Những việc tôi đã làm được (liệt kê tự do, không giới hạn):**
    *   *Xây dựng ReAct Agent & Công cụ (Lab 3):* Tôi đã trực tiếp xây dựng và cấu trúc mock HR database (`hr_data.py`) với cấu trúc phân cấp (Employees, Leave Balances, Payroll, Policies). Tôi đã lập trình 5 tools nghiệp vụ HR (`get_employee`, `get_leave_balance`, `calculate_payroll`, `search_policy`, `list_department_employees`) cùng với JSON Schema định nghĩa tham số đầu vào cho ReAct Agent.
    *   *Tối ưu hóa logic gọi công cụ (Lab 3):* Tôi phát hiện Agent v1 gặp lỗi khi LLM truyền tham số dạng Tên nhân viên thay vì ID nhân viên. Tôi đã lập trình hàm chuẩn hóa tiếng Việt không dấu (`strip_accents`) và tích hợp tính năng tự động phân giải Tên sang ID ngay trong code tool, giúp Agent giảm 50% số bước gọi LLM trung gian.
    *   *Tích hợp Generation với Citation (Day 8):* Trong dự án nhóm xây dựng RAG chatbot pháp luật ma túy, tôi phụ trách Task 10 - Tích hợp Generation. Tôi đã lập trình logic xuất ra câu trả lời kèm theo Citation (nguồn dẫn chuẩn xác tới từng điều khoản của Luật) và hiển thị nguồn tài liệu làm bằng chứng (evidence documents), kèm cơ chế fallback tạo extractive answer khi không có API Key.
    *   *Triển khai kiểm thử RAG (Day 8):* Tôi đã phối hợp viết kịch bản chạy thử nghiệm A/B test so sánh giữa hai cấu hình: Config A (Hybrid Search + RRF) và Config B (BM25 Only) sử dụng framework chấm điểm cục bộ (Offline RAG Evaluator) với bộ 15 test cases.
    *   *Lập trình Multi-Judge Consensus Engine (Lab 14):* Tôi đã tự tay viết mã nguồn lớp `LLMJudge` trong `llm_judge.py` thực hiện cơ chế chấm điểm tự động. Để giải quyết lỗi thiên vị chấm điểm (Leniency Bias), tôi đã thiết kế chi tiết bộ rubrics phân cấp 1-5 điểm. Đồng thời, tôi triển khai cơ chế Trọng tài (Referee Judge) để phân xử khi hai mô hình judge độc lập lệch điểm nhau $> 1$.
    *   *Nâng cao hiệu năng & đo lường hệ thống (Lab 14):* Tôi đã xây dựng `runner.py` sử dụng `asyncio.Semaphore` quản lý gọi song song API giúp benchmark 50 test cases không bị dính giới hạn Rate Limit (429). Tôi đã lập trình các module đo lường Latency, đếm số lượng Token đầu vào/đầu ra và tính toán chi phí API USD tích lũy cho mỗi lượt chạy.
    *   *Đóng gói & Triển khai sản phẩm (Day 12):* Tôi đã đảm nhận việc đóng gói container ứng dụng Streamlit Dashboard và ReAct Gateway thông qua Dockerfile. Tôi đã thiết lập GitHub Actions workflow (`ci-cd.yml`) để tự động hóa kiểm thử và đẩy mã nguồn lên môi trường Railway (`perfect-art-production-d49b.up.railway.app`), xử lý các xung đột về cổng PORT động và phân quyền non-root user.
*   **Loại công việc cho tôi năng lượng, muốn làm tiếp:**
    *   Tôi thích lập trình logic xử lý cho tác nhân (Agent logic), thiết lập luồng suy nghĩ (Thought routing), xây dựng các tool tích hợp và lập trình prompt nâng cao. Tôi tìm thấy nhiều năng lượng khi giải quyết các bài toán kỹ thuật phức tạp như thiết lập cơ chế bất đồng bộ, tối ưu hóa RAG (sắp xếp độ ưu tiên chunk, reranking), và đóng gói Docker/triển khai ứng dụng thực tế.

---

### ③ KỸ NĂNG MÌNH ĐỊNH PHÁT TRIỂN TỚI

*   **Bộ 3 kỹ năng phát triển:**
    1.  *Advanced Agent Architectures:* Tôi định hướng học sâu về thiết kế các kiến trúc Agent nâng cao như Multi-Agent, cơ chế kiểm duyệt (Supervisor-Worker), và các framework quản lý trạng thái phức tạp (LangGraph/Autogen).
    2.  *RAG Optimization & Advanced Indexing:* Tôi muốn thành thạo các kỹ thuật RAG nâng cao như GraphRAG, Query Rewriting, Sub-Query decomposition và tối ưu hóa các chiến lược Chunking/Reranking để giải quyết các bài toán tra cứu phức tạp.
    3.  *MLOps & Cloud Infrastructure:* Nâng cao kỹ năng quản lý cơ sở dữ liệu Vector quy mô lớn, giám sát hệ thống AI trong môi trường production (Observability/Traces) và tối ưu hóa phân bổ tài nguyên GPU phục vụ self-hosting mô hình nguồn mở.
*   **Gap lớn nhất + thứ tôi sẽ build để cho thấy tiến bộ:**
    *   *Gap lớn nhất:* Tôi chưa có nhiều cơ hội thực chiến làm việc với các hệ thống Multi-Agent phức tạp có sự tương tác chéo giữa 3-4 agent chuyên biệt, và việc tối ưu hóa fine-tuning các mô hình nhỏ (như LoRA/QLoRA) để chạy local.
    *   *Thứ tôi sẽ build:* Tôi sẽ tự xây dựng một hệ thống Multi-Agent trợ lý nghiên cứu pháp lý (Legal Research Assistant) sử dụng LangGraph. Hệ thống sẽ gồm 3 agent chạy song song: một Agent chuyên crawl và chuẩn hóa dữ liệu, một Agent chuyên tra cứu RAG (Vector + Lexical), và một Agent chuyên phản biện/đánh giá kết quả (Reviewer). Tôi sẽ tự viết Dockerfile và deploy toàn bộ hệ thống lên Cloud kèm theo CI/CD tự động.

---

### ④ QUYẾT ĐỊNH TRACK

*   **Nguyện vọng 1 (Track chọn): T3 · AI Engineering (Chuyên sâu AI Application)**
    *   *Vì:* Qua các bài tập lớn ở Phase 1, tôi nhận thấy mình có niềm đam mê và thế mạnh rõ rệt nhất ở việc lập trình và xây dựng các ứng dụng thông minh dùng LLM. Tôi thích viết code logic cho Agent (`agent.py`), thiết kế prompt, xây dựng các parser dữ liệu, lập trình bất đồng bộ để tăng hiệu năng và tối ưu hóa RAG. Tôi cảm thấy tràn đầy năng lượng khi nhìn thấy tác nhân thông minh tự động suy luận và gọi đúng các công cụ Python mà mình đã viết để giải quyết các yêu cầu phức tạp. Đối chiếu với năng lực thực tế, việc triển khai mã nguồn cho ReAct Agent (Lab 3), RAG Citation (Day 8), Consensus Engine và Async Runner (Lab 14) chứng minh tôi hoàn toàn phù hợp với định hướng trở thành một kỹ sư phát triển ứng dụng AI chuyên nghiệp.
*   **Nguyện vọng 2 (Track cân nhắc): T2 · Data & Infrastructure (Chuyên sâu AI Infrastructure)**
    *   *Vì:* Trong quá trình làm Lab Day 12, tôi đã trực tiếp đảm nhận phần DevOps: viết Dockerfile tối ưu kích thước image, cấu hình container chạy non-root user để bảo mật, thiết lập GitHub Actions CI/CD và deploy thành công ứng dụng lên Railway. Tôi thích việc cấu hình hệ thống chạy trơn tru, ổn định và tự động hóa quy trình. Tuy nhiên, tôi chọn AI Infrastructure làm nguyện vọng 2 vì đối với tôi, hạ tầng và DevOps đóng vai trò là bệ đỡ kỹ thuật vô cùng quan trọng giúp tôi đóng gói và vận hành các ứng dụng AI (T3) của mình một cách tối ưu nhất trong môi trường thực tế, thay vì là một công việc độc lập hoàn toàn.
*   **Lý lẽ mạnh nhất cho việc KHÔNG chọn track còn lại (T1 · AI Product):**
    *   *Lý do:* Dù trong Lab 14 tôi đã làm rất tốt vai trò BA & QA Lead (viết báo cáo Failure Analysis, thiết lập Rubrics sửa Leniency Bias, phân tích chi phí), tôi nhận ra năng lượng của mình vẫn chủ yếu đến từ việc trực tiếp viết code giải quyết các vấn đề kỹ thuật khó (như viết Async Runner hay Consensus Engine) hơn là việc chỉ đứng ngoài phân tích nghiệp vụ, lập kế hoạch hoặc khảo sát người dùng. Tôi muốn làm một người trực tiếp xây dựng sản phẩm (Builder) hơn là một người chỉ đưa ra định hướng sản phẩm thuần túy.
*   **Dấu hiệu sẽ khiến tôi xem lại lựa chọn (sáu tháng nữa nhìn lại):**
    *   Nếu sau sáu tháng đi theo track AI Engineering, tôi nhận ra mình dành phần lớn thời gian để họp hành, thiết kế slide, viết tài liệu nghiệp vụ hoặc chỉ thích viết tài liệu PRD mà ngại viết code, debug hay tìm hiểu sâu về kỹ thuật của các thư viện agent mới.

---

### ⑤ ĐỊNH HƯỚNG & CHUẨN BỊ (ghi mở — có gì ghi nấy)

*   **Định hướng tiếp theo:**
    *   Tôi sẽ tập trung học sâu các thư viện điều phối Agent nâng cao (LangGraph, LangChain) và tích lũy thêm kinh nghiệm về tối ưu hóa RAG thực tế.
    *   Xây dựng kho mã nguồn (Github portfolio) sạch sẽ, chuẩn hóa toàn bộ các bài lab đã làm thành các repository độc lập để sẵn sàng ứng tuyển.
*   **Những thứ cần chuẩn bị:**
    *   Tự trang bị thêm kiến thức về Vector Database nâng cao (như thiết lập index HNSW trong ChromaDB/PGVector).
    *   Tìm hiểu về cách đo lường độ tin cậy và kiểm thử tự động hệ thống AI ở quy mô lớn (dùng DeepEval hoặc Ragas).
*   **Plan nếu có:**
    *   Xây dựng dự án cá nhân "Legal Multi-Agent Research" trong vòng 2 tháng tới để áp dụng toàn bộ các kiến thức về Agent, RAG và deployment đã học.
*   **Câu hỏi còn mở:**
    *   Làm thế nào để tối ưu hóa thời gian phản hồi (Latency) của một hệ thống Multi-Agent phức tạp khi số lượng lượt gọi LLM API tăng lên mà không làm giảm chất lượng suy luận?
