# Tổng quan JavaScript 
- Là một nguôn ngữ bậc cao(High-level).
- Tự động giải phóng bộ nhớ(Garbage-collected).
- Là một ngôn ngữ thông dịch và biên dịch Just-in-time.
- Hỗ trợ đa mô hình lập trình bao gồm: lập trình cấu trúc và hướng đối tượng.
- First-class functions: Hàm có thể được coi đơn giản như là một biến đển lấy làm tham số truyền vào hàm khác:
VD:
```js
const closeModal = () => {
    modal.classList.add("hidden");
}

// coi hàm closeModal như là một biến để truyền vào hàm addEventListener
modal.addEventListener("click", closeModal);
```
- Dynamic: Kiểu dữ liệu của biến sẽ được thay đổi phụ thuộc vào giá trị mà nó được gán.
VD:
```js 
let x = 15; // x được xác định là kiểu số nguyên
x = "Phan Chinh Quan" // x đã được chuyển sang kiểu chuỗi
```
- Là một ngôn ngữ đơn luồng(single-threaded).
    + Javascript chỉ chạy 1 luồng và vì vậy nó chỉ có thể làm được 1 việc tại một khoảng thời gian.

- Non-blocking event loop.