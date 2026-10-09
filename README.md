# BÁO CÁO THỰC HÀNH KIỂM THỬ API BẰNG POSTMAN

- **Họ và tên:** Đặng Thanh Tùng
- **Mã sinh viên:** 23010218
- **Lớp:** K17-CNTT_3
- **Link Video Tham Khảo:** https://www.youtube.com/watch?v=MFxk5BZulVU

---

## 1. Mục tiêu bài tập
- Nắm vững khái niệm cơ bản về RESTful API và phương thức kiểm thử API.
- Sử dụng công cụ Postman để gửi các Request (GET, POST, PUT, DELETE).
- Viết các đoạn Test Script bằng JavaScript để kiểm tra Status Code, Response Time và Response Body.

---

## 2. Dữ liệu API sử dụng
- **Base URL:** `https://jsonplaceholder.typicode.com`
- **Endpoint kiểm thử:** `/posts/1`

---

## 3. Kết quả thực hiện & Minh họa

### Test Case 1: Kiểm tra API GET /posts/1
- **Request URL:** `https://jsonplaceholder.typicode.com/posts/1`
- **Mục tiêu test:**
  1. Kiểm tra Status Code trả về là `200 OK`.
  2. Thời gian phản hồi (Response Time) `< 500ms`.
  3. Dữ liệu trả về đúng định dạng JSON và chứa trường `id = 1`.

#### Mã Test Script (Post-response):
```javascript
pm.test("Status code is 200 OK", function () {
    pm.response.to.have.status(200);
});

pm.test("Response time is less than 500ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});

pm.test("Check response data structure", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.id).to.eql(1);
});


