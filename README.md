# BÁO CÁO THỰC HÀNH CÔNG CỤ KIỂM THỬ POSTMAN

## 1. Giới thiệu

Postman là một công cụ hỗ trợ kiểm thử API. Công cụ này cho phép người dùng gửi các request đến server, kiểm tra response trả về, xem status code, headers, body và viết các đoạn script để tự động kiểm thử kết quả.

Trong bài thực hành này, em sử dụng Postman để kiểm thử các API cơ bản với các phương thức HTTP phổ biến như:

* GET
* POST
* PUT
* DELETE

API được sử dụng để thực hành là JSONPlaceholder, một API giả lập miễn phí thường dùng để học và kiểm thử REST API.

## 2. Mục tiêu bài thực hành

Mục tiêu của bài thực hành gồm:

* Tìm hiểu công cụ kiểm thử API Postman.
* Biết cách tạo request trong Postman.
* Thực hiện kiểm thử các phương thức GET, POST, PUT, DELETE.
* Kiểm tra status code và dữ liệu response trả về.
* Biết cách lưu các request vào Collection.
* Biết cách viết test script đơn giản trong Postman.
* Tạo GitHub Repo và viết báo cáo kết quả thực hiện trong file README.md.

## 3. Công cụ và tài liệu sử dụng

### 3.1. Công cụ sử dụng

* Postman
* GitHub
* Trình duyệt web
* API mẫu: JSONPlaceholder

### 3.2. Tài liệu tham khảo

* Video học Postman do giảng viên cung cấp.
* Tài liệu Postman Learning Center.
* Tài liệu JSONPlaceholder Guide.

## 4. API sử dụng trong bài

Base URL:

```text
https://jsonplaceholder.typicode.com
```

Các endpoint sử dụng:

| Phương thức | Endpoint   | Chức năng                 |
| ----------- | ---------- | ------------------------- |
| GET         | `/posts`   | Lấy danh sách bài viết    |
| GET         | `/posts/1` | Lấy chi tiết một bài viết |
| POST        | `/posts`   | Tạo bài viết mới          |
| PUT         | `/posts/1` | Cập nhật bài viết         |
| DELETE      | `/posts/1` | Xóa bài viết              |

## 5. Các bước thực hiện

## 5.1. Tạo Collection trong Postman

Đầu tiên, em mở Postman và tạo một Collection mới với tên:

```text
Postman API Testing
```

Sau đó, em tạo các request tương ứng với từng phương thức HTTP và lưu vào Collection này.

Ảnh minh họa:

![Collection](images/collection.png)

## 5.2. Kiểm thử request GET

### Mục đích

Request GET được sử dụng để lấy dữ liệu từ server.

### Cấu hình request

Method:

```text
GET
```

URL:

```text
https://jsonplaceholder.typicode.com/posts
```

### Kết quả

Sau khi gửi request, server trả về danh sách các bài viết. Status code nhận được là:

```text
200 OK
```

Điều này cho thấy request đã được thực hiện thành công.

Ảnh minh họa:

![GET Request](images/get-request.png)

## 5.3. Kiểm thử request POST

### Mục đích

Request POST được sử dụng để tạo mới dữ liệu trên server.

### Cấu hình request

Method:

```text
POST
```

URL:

```text
https://jsonplaceholder.typicode.com/posts
```

Body chọn dạng raw JSON:

```json
{
  "title": "Postman Test",
  "body": "This is a test request using Postman",
  "userId": 1
}
```

### Kết quả

Sau khi gửi request, server trả về dữ liệu vừa được tạo. Status code nhận được là:

```text
201 Created
```

Điều này cho thấy dữ liệu đã được tạo thành công.

Ảnh minh họa:

![POST Request](images/post-request.png)

## 5.4. Kiểm thử request PUT

### Mục đích

Request PUT được sử dụng để cập nhật dữ liệu đã tồn tại trên server.

### Cấu hình request

Method:

```text
PUT
```

URL:

```text
https://jsonplaceholder.typicode.com/posts/1
```

Body chọn dạng raw JSON:

```json
{
  "id": 1,
  "title": "Updated Title",
  "body": "This content has been updated using Postman",
  "userId": 1
}
```

### Kết quả

Sau khi gửi request, server trả về dữ liệu đã được cập nhật. Status code nhận được là:

```text
200 OK
```

Điều này cho thấy request cập nhật dữ liệu đã thực hiện thành công.

Ảnh minh họa:

![PUT Request](images/put-request.png)

## 5.5. Kiểm thử request DELETE

### Mục đích

Request DELETE được sử dụng để xóa dữ liệu trên server.

### Cấu hình request

Method:

```text
DELETE
```

URL:

```text
https://jsonplaceholder.typicode.com/posts/1
```

### Kết quả

Sau khi gửi request, server trả về kết quả thành công. Status code nhận được là:

```text
200 OK
```

Điều này cho thấy request xóa dữ liệu đã được thực hiện thành công.

Ảnh minh họa:

![DELETE Request](images/delete-request.png)

## 6. Viết test script trong Postman

Ngoài việc gửi request thủ công, Postman còn hỗ trợ viết test script để kiểm tra kết quả trả về.

Ví dụ với request GET, em thêm đoạn script sau vào phần Post-response:

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response body is not empty", function () {
    pm.expect(pm.response.text()).to.not.be.empty;
});
```

Kết quả test hiển thị trong tab Test Results.

Ảnh minh họa:

![Test Result](images/test-result.png)

## 7. Bảng tổng hợp kết quả kiểm thử

| STT | Method | URL        | Expected Status | Actual Status | Kết quả |
| --- | ------ | ---------- | --------------- | ------------- | ------- |
| 1   | GET    | `/posts`   | 200 OK          | 200 OK        | Pass    |
| 2   | GET    | `/posts/1` | 200 OK          | 200 OK        | Pass    |
| 3   | POST   | `/posts`   | 201 Created     | 201 Created   | Pass    |
| 4   | PUT    | `/posts/1` | 200 OK          | 200 OK        | Pass    |
| 5   | DELETE | `/posts/1` | 200 OK          | 200 OK        | Pass    |

## 8. Kết quả đạt được

Sau khi hoàn thành bài thực hành, em đã đạt được các kết quả sau:

* Cài đặt và sử dụng được công cụ Postman.
* Tạo được Collection để quản lý các request API.
* Gửi được các request GET, POST, PUT, DELETE.
* Kiểm tra được status code và response body.
* Viết được test script đơn giản trong Postman.
* Biết cách lưu kết quả thực hành và báo cáo lên GitHub Repo.

## 9. Kết luận

Postman là một công cụ rất hữu ích trong kiểm thử phần mềm, đặc biệt là kiểm thử API. Công cụ này giúp người kiểm thử dễ dàng gửi request, kiểm tra response và tự động hóa một số bước kiểm thử bằng script.

Thông qua bài thực hành này, em đã hiểu được quy trình kiểm thử API cơ bản và biết cách sử dụng Postman để kiểm tra hoạt động của các phương thức HTTP thông dụng.
