# API GATEWAY

## CLIENT GIAO TIẾP TRỰC TIẾP VỚI MICROSERVICE

- Không phù hợp giữa nhu cầu của client và các API chi tiết được cung cấp bởi từng microservice
- Client phải thực hiện nhiều request riêng biệt tới từng services
- Một số microservice có thể sử dụng các giao thức không thân thiện với clients (GRPC, AMQP,...)
- Gây khó khăn trong việc tái cấu trúc microservices

## SỬ DỤNG API GATEWAY


> API Gateway là một máy chủ và là điểm đầu vào duy nhất của hệ thống. Nó có thể có một vài trách nhiệm như: 

- Xác thực (authentication)
- Giám sát (monitoring)
- Cân bằng tải (load balancing)
- Bộ nhớ đệm (caching)
- Chuyển đổi request (request shaping and management)
- Xử lý phản hồi tĩnh (static response handling)

> API Gateway chịu trách nhiệm định tuyến các request, tổng hợp và chuyển đổi giao thức

## LỢI ÍCH VÀ HẠN CHẾ CỦA API GATEWAY
## Lợi ích 
- Đóng gói cấu trúc bên trong của ứng dụng (Thay vì phải gọi các dịch vụ cụ thể, client chỉ cần nói chuyện với Gateway.)
- API Gateway cung cấp cho từng loại client với API cụ thể. Điều này làm giảm số lượng request/response giữa client và hệ thống. Nó cũng giúp đơn giản hóa client code.

## Nhược điểm 
- Nguy cơ là API Gateway trở thành nút thắt cổ chai (bottleneck)
- Cần phải develop, deploy, and manage một component khác có độ sẵn sàng cao (highly available) đảm nhận vai trò API Gateway

## IMPLEMENT API GATEWAY
- Performance and Scalability
- Using a Reactive Programming Model
- Service Invocation
- Service Discovery
- Handling Partial Failures

    - Network timeouts: timeout cho clients trong thời gian chờ hồi đáp, không block. Sử dụng timeouts đảm bảo tài nguyên client không bị chiếm dụng vô thời hạn.
    - Giới hạn số lượng các yêu cầu còn tồn tại: Đặt ngưỡng tối đa số request mà mỗi client có thể gởi tới. Quá con số này, mọi yêu cầu sẽ bị hủy. 
    - Mô hình cầu giao ngắt mạch (Circuit breaker pattern): Khi số yêu cầu lỗi vượt quá ngưỡng đã định, ngắt cầu giao (circuit breaker) để tất cả yêu cầu sau đó bị hủy ngay lập tức. Nếu số yêu cầu bị lỗi vẫn tiếp tục tăng lên, sẽ có thông báo rằng dịch vụ không thể truy cập và việc gửi các yêu cầu là vô nghĩa. Sau 1 chu kì timeout, client có thể thử lại, nếu thành công, circuit breaker sẽ được đóng lại.

## References

- https://www.nginx.com/blog/building-microservices-using-an-api-gateway/
