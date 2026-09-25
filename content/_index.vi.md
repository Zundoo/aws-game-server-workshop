---
title : "Tổng quan Workshop"
date : "2026-09-25" 
weight : 1 
chapter : false
---

# AWS REAL-TIME GAME SERVER WORKSHOP

#### Tổng quan bài thực hành
Workshop này tập trung vào quy trình thiết lập, vận hành và kiểm thử một hệ thống hạ tầng đám mây chịu tải cao cho ứng dụng **Real-time Game Server** sử dụng kết nối bền vững **WebSocket**. 

Toàn bộ hệ thống được xây dựng trên nền tảng đám mây **Amazon Web Services (AWS)** kết hợp với công nghệ đóng gói Container và bộ nhớ đệm In-memory, giúp tối ưu hóa hiệu suất truyền tải tin nhắn, đảm bảo tính sẵn sàng cao và khả năng tự động co giãn thông minh khi lượng game thủ vọt đỉnh.

![Kiến trúc Tổng thể Hệ thống AWS Game Server](/images/architecture-diagram.png?featherlight=false&width=90pc)

{{% notice info %}}
**Lưu ý về Bảo mật**: Hạ tầng áp dụng mô hình 3 lớp (3-Tier Architecture) để cô lập hoàn toàn lớp tính toán (Compute) và dữ liệu (Database) trong phân vùng mạng kín (**Private Subnets**). Bộ cân bằng tải ALB đặt tại Public Subnet đóng vai trò là cổng đón an toàn duy nhất từ Internet.
{{% /notice %}}

#### 🛠️ Các dịch vụ AWS cốt lõi áp dụng trong Dự án

*   **Amazon VPC**: Khởi tạo phân vùng mạng ảo độc lập, cấu hình dải Subnet Public/Private và thiết lập ma trận tường lửa Security Group chặt chẽ.
*   **Amazon ECR & Docker**: Đóng gói ứng dụng WebSocket Node.js thành Container Image và quản lý lưu trữ tập trung bảo mật.
*   **Amazon Elastic Container Service (ECS)**: Điều phối, vận hành và quản lý vòng đời các tác vụ Container thông qua mô hình Serverless AWS Fargate.
*   **Application Load Balancer (ALB)**: Cổng tiếp nhận lưu lượng kết nối tập trung, tự động xử lý nâng cấp giao thức mạng từ HTTP sang WebSocket.
*   **Amazon ElastiCache Redis**: Bộ nhớ đệm tốc độ cao (bật mã hóa đường truyền TLS) chịu trách nhiệm đồng bộ trạng thái phòng game đa máy chủ.
*   **Amazon CloudWatch**: Hệ thống giám sát tài nguyên phần cứng thời gian thực và quản lý nhật ký Log tập trung từ Container.

#### 💡 Các điểm nhấn Kỹ thuật nổi bật trong Workshop

1.  **Debug lỗi treo kết nối Redis TLS**: Học cách xử lý sự cố nghẽn mạng (Timeout) do tính năng *Encryption in-transit* bằng cách đồng bộ hóa cờ `--tls` trên terminal và cấu hình mã nguồn sang giao thức `rediss://`.
2.  **Sửa lỗi phân quyền CloudWatch Logs**: Khắc phục lỗi `AccessDeniedException` bằng cách bổ sung chính sách `CloudWatchAgentServerPolicy` vào IAM Role và cấu hình tham số `--log-driver=awslogs`.
3.  **Stress Test hệ thống gánh tải**: Sử dụng công cụ Artillery để giả lập **1.000 người chơi ảo kết nối đồng thời** và xử lý **46.500 tin nhắn real-time**, kiểm thử thành công cơ chế tự động nhân bản Container của Auto Scaling khi CPU vượt ngưỡng 70%.

---

#### 📂 Cấu trúc các bước triển khai trong Workshop

1. [4.1. Networking](4-workshop/4.1-networking/)
2. [4.2. Container](4-workshop/4.2-container/)
3. [4.3. Database](4-workshop/4.3-database/)
4. [4.4. Game Server](4-workshop/4.4-game-server/)
5. [4.5. Load Balancing](4-workshop/4.5-load-balancing/)
6. [4.6. Scaling](4-workshop/4.6-scaling/)
7. [4.7. Monitoring](4-workshop/4.7-monitoring/)
8. [4.8. CI/CD](4-workshop/4.8-cicd/)
9. [4.9. Load Testing](4-workshop/4.9-load-testing/)
10. [4.10. Cleanup](4-workshop/4.10-cleanup/)
