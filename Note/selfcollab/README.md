Self-collaboration Code Generation via ChatGPT

Tóm tắt là các tác giả đề xuất A self-collaboration framework 
-> Mục tiêu là hướng dẫn các LLMs đồng hành cùng nhau xây dựng và làm các task.
-> Chia ra làm hai phần chính:
 - Division of Labor 
 - Collaboration 


Division of Labor 

-> Sử dụng LLMs để chia công việc phức tạp thành các step nhỏ hơn. 
kèm theo đó là xây dựng một số vai trò khác biệt . 

Người ta thường thừa nhận rằng các mô hình ngôn ngữ lớn (LLM) nhạy cảm với ngữ cảnh, vì chúng được huấn luyện để dự đoán các từ tiếp theo dựa trên các từ trước đó. Do đó, việc điều khiển LLM tạo nội dung bằng cách sử dụng các chỉ dẫn hoặc lời nhắc (prompts) là phổ biến [11, 40, 41]. Để đạt được sự phân công lao động, chúng tôi tạo ra một loại chỉ dẫn cụ thể để gán vai trò và trách nhiệm cho LLM, mà chúng tôi gọi là chỉ dẫn vai trò (role instructions). Cụ thể, chúng tôi yêu cầu LLM đóng vai một vai trò cụ thể có liên quan chặt chẽ đến trách nhiệm của nó. Hơn nữa, chúng tôi cần truyền đạt các nhiệm vụ chi tiết, tức là các trách nhiệm mà vai trò này nên thực hiện. Nói chung, một mô tả nhiệm vụ rõ ràng và không dài dòng trong chỉ dẫn có thể dẫn đến hành vi của LLM phù hợp hơn với kỳ vọng của bạn. Một trường hợp mà có thể không cần thiết phải nêu rõ trách nhiệm của một vai trò là khi sự phân công lao động đó đủ phổ biến để có thể tìm thấy các vai trò tương ứng trong thực tế.
Thông qua việc nhập vai, chúng tôi có thể đặt LLM vào một lĩnh vực cụ thể, từ đó khai thác được chuyên môn của nó trong lĩnh vực đó. Bằng chứng thực nghiệm của chúng tôi cho thấy rằng phương pháp nhập vai này mang lại kết quả vượt trội so với việc trực tiếp yêu cầu LLM thực hiện nhiệm vụ mà không có bối cảnh định sẵn. Vì vậy, nhập vai có thể được tận dụng như một công cụ hiệu quả để cải thiện hiệu suất của LLM trong các nhiệm vụ chuyên biệt.
Lưu ý rằng chỉ dẫn vai trò chỉ cần được cung cấp một lần tại thời điểm khởi tạo mỗi tác nhân LLM để cung cấp hướng dẫn cụ thể về hành vi của nó trong suốt các tương tác sau đó, do đó nâng cao hiệu quả và sự rõ ràng trong sự hợp tác tổng thể.

Division of Labor 

Trong bối cảnh các mô hình ngôn ngữ, sự hợp tác giữa các vai trò khác nhau bao gồm các bước sau:
Phân công và Tương tác Vai trò: Các vai trò khác nhau được phân công cho các mô hình ngôn ngữ. Khi quá trình tiến triển, các vai trò này tương tác với kết quả của nhau. Sự tương tác này tinh chỉnh công việc tổng thể, đảm bảo độ chính xác và sự chu đáo trong kết quả cuối cùng.
Giao tiếp bằng Ngôn ngữ Tự nhiên: Sự tương tác giữa các vai trò được thực hiện bằng ngôn ngữ tự nhiên, được hỗ trợ bởi các khía cạnh cơ bản của mô hình ngôn ngữ. Mỗi vai trò được cung cấp hướng dẫn cụ thể về thông tin cần xử lý và định dạng, đảm bảo sự hợp tác có kiểm soát và hiệu quả.
Chính thức hóa Sự hợp tác: Quá trình hợp tác có thể được biểu diễn dưới dạng toán học. Dưới đây là phân tích phương trình đã cho:



4. Cập nhật Kết quả Lặp lại: Kết quả OO được cập nhật lặp lại khi quá trình tiến triển qua các giai đoạn khác nhau SiSi​:



Thuật toán 


Instance 

Cụ thể, chúng tôi thiết kế một mô hình thác nước đơn giản hóa gồm ba giai đoạn: phân tích, mã hóa và kiểm thử, như một ví dụ cho việc tự cộng tác tạo mã. Quy trình làm việc của ví dụ này theo mô hình thác nước, di chuyển từ giai đoạn này sang giai đoạn khác, và nếu có vấn đề được phát hiện, nó sẽ quay lại giai đoạn trước để tinh chỉnh. Do đó, chúng tôi thiết lập một nhóm cơ bản, gồm một nhà phân tích, lập trình viên và kiểm thử viên, chịu trách nhiệm về các giai đoạn phân tích, mã hóa và kiểm thử, như minh họa trong Hình 2 (bên phải). Ba vai trò này được giao các nhiệm vụ sau:
Nhà phân tích
Mục tiêu của nhà phân tích là giảm bớt khó khăn của việc mã hóa bằng cách trừu tượng hóa và phân chia nhiệm vụ từ mức độ cao, thay vì đi sâu vào chi tiết của việc triển khai. Khi nhận được yêu cầu ωω, nhà phân tích sẽ chia ωω thành nhiều nhiệm vụ nhỏ dễ giải quyết để tạo điều kiện cho việc phân chia các đơn vị chức năng và phát triển một kế hoạch tổng thể để hướng dẫn lập trình viên viết mã.
Lập trình viên
Là vai trò trung tâm của nhóm này, lập trình viên chịu trách nhiệm viết mã, nhưng công việc của họ được thực hiện với sự hỗ trợ và giám sát của nhà phân tích và kiểm thử viên. Do đó, chúng tôi giao cho lập trình viên hai trách nhiệm: 1) Viết mã đáp ứng các yêu cầu đã chỉ định, tuân theo kế hoạch do nhà phân tích cung cấp. 2) Sửa chữa hoặc tinh chỉnh mã, xem xét phản hồi từ các báo cáo kiểm thử do kiểm thử viên cung cấp.
Kiểm thử viên
Kiểm thử viên chịu trách nhiệm kiểm tra mã và tạo báo cáo kiểm thử về các khía cạnh chức năng, khả năng đọc và khả năng bảo trì để giúp lập trình viên cải thiện chất lượng mã của họ. Thay vì trực tiếp giới thiệu trình biên dịch và các trường hợp kiểm thử để thực thi mã, chúng tôi sử dụng mô hình để mô phỏng quá trình kiểm thử và tạo ra các báo cáo kiểm thử, qua đó tránh các nỗ lực bên ngoài.



Phương án đánh giá: 

RQ1: Hiệu suất của phương pháp tự cộng tác so với các phương pháp cơ bản khác trên các tiêu chuẩn đánh giá mã công khai là gì?
RQ2: Ảnh hưởng của các vai trò trong tự cộng tác là gì? Cụ thể, nó có thể được chia thành ba câu hỏi: 1. Đóng góp của mỗi vai trò trong nhóm ảo là gì? 2. Ảnh hưởng của các nhóm ảo khác là gì? 3. Ảnh hưởng của việc đóng vai trò là gì?
RQ3: Hiệu suất của tự cộng tác dựa trên các mô hình ngôn ngữ lớn (LLM) khác nhau, đặc biệt là mô hình LLM mạnh nhất GPT-4, là gì?
RQ4: Ảnh hưởng của số lần tương tác đối với tự cộng tác là gì?
RQ5: Kết quả của phân tích chi tiết hơn (cụ thể là phân tích lỗi và phân tích chi phí) cho tự cộng tác là gì?
RQ6: Phương pháp tự cộng tác hoạt động như thế nào trong các kịch bản phát triển phần mềm ở cấp độ kho lưu trữ và hiệu suất của nó ra sao?
