# JavaScript Engine

- **Hiểu đơn giản là một chương trình hoặc trình thông dịch thực thi mã Javascript.**
- Một Javascript engine là một nguôn ngữ thông dịch và biên dịch just-in-time từ Javascript thành mã máy.

## 1. Thông dịch.
- Chương trình chạy đến dòng nào thì dịch dòng đó.
- Bộ thông dịch gọi là **interpreter**.

* Ưu điểm:
    - Interpreter dễ hiện thực hơn do bỏ qua việc kiểm tra lỗi và tối ưu code thường được thực hiện trong quá trình compiled.
    - Hỗ trợ đa nền tảng.
    - Kích thước chương trình thực thi nhỏ hơn.

* Khuyết điểm:
    - Chương trình có độ tin cậy thấp hơn do bỏ qua bước kiểm tra loại bỏ một số lỗi thường thực hiện trong quá trình compiled.
    - Source code dễ dàng bị dịch ngược.
    - Tốc độ thực thi chậm hơn.
    - Tiềm tàng nguy cơ có lỗi do thiếu.

## 2. Biên dịch Just-in-time.
### a) Biên dịch
- Chương trình sẽ dịch toàn bộ thành mã máy rồi mới tiến hành thực thi.
- Bộ biên dịch thực hiện quá trình biên dịch được gọi là compiler.

* Ưu điểm:
    - Chương trình sau đó được thực thi nhanh hơn.
    - Độ tin cậy cao
    - Khó bị dịch ngược mã nguồn.

* Khuyết điểm:
    - Khó xây dựng một compiler có tính chính xác cao để chuyển toàn bộ chương trình thành mã máy.
    - Mã máy của mỗi nền tảng là khác nhau, khó thực hiện đa nền tảng.

### b) Just-in-time trong JavaScript.
#### Monitor / Profiler
- **Monitor**_(Một số tài liệu gọi là **Profiler**)_ là một phần của JavaScript Engine. 
- Có nhiệm vụ theo dõi các đoạn code đang chạy và ghi chú xem rằng nó đã được chạy bao nhiêu lần và các kiểu dữ liệu được sử dụng. Lúc đầu, Monitor chỉ chạy tất cả mọi thứ thông qua thông dịch(Interpreter).
- Nếu đoạn code được chạy một vài lần thì được gọi là **swam**, chạy nhiều lần thì được gọi là **hot**.

#### Baseline Compiler
- Khi một đoạn mã được xác định là swam. Nó sẽ được JIT biên dịch. Trong thời gian compliler, trình dịch có thể mất thời gian để tối ưu đoạn code _(Optimizing compiler)_ đến khi mà nó cho là đã được tối ưu và lưu bản dịch lại. Bản dịch được lưu lại có thể sẽ được sử dụng lại khi mà Monitor phát hiện ra rằng 1 đoạn mã tương tự với source code. Điều này giúp giảm thiểu thời gian trong toàn bộ quá trình biên dịch.

#### Optimizing Compliler
- Một đoạn code được xác định là hot. Trình biên dịch sẽ mất nhiều thời gian hơn để tối ưu cho nó.
- Trình dịch sẽ tối ưu code bằng cách đưa ra nhiều giả định. Giả định trước đúng sẽ được tiếp tực được sử dụng cho giả định sau.
- Sau mỗi giả định, code mới sẽ quay trở lại bước thông dịch hoặc biên bản biên dịch (Baseline compiler) cơ sở. Trính trình này được gọi là **Deoptimization** _(hoặc là **Bailing**)_.
- Việc deoptimization xảy ra nhiều lần đôi khi lại dẫn đến mất thời gian hơn so với những bản dịch cơ sở. Javascript có cơ chế để dừng điều này lại.

Tài liệu tham khảo:
https://viblo.asia/p/trinh-bien-dich-javascript-jit-just-in-time-jvElaXRdZkw
http://icthanoi.edu.vn/trinh-bien-dich-just-in-time-2012.htm


