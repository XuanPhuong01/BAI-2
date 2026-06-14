# BAI-2
PHÁT TRIỂN ỨNG DỤNG TRÊN THIẾT BỊ DI ĐỘNG
2. Viết app sử dụng Android Studio
   + Android manifest.xml  => mô tả gì? App cần quyền để do-st: khai báo ntn? Để làm gì?
   + vòng đời của 1 ứng dụng android.
     Code tự sinh sau khi tạo 1 project: có sẵn hàm oncreate: tại sao???
   + Code: java language. 
     App cần check xem có quyền để do-st? : code ntn? Ý nghĩa?
     Giao diện: (res/layout) mô tả bằng file XML + UI Design review
        + thuộc tính text, hoặc các thuộc tính khác: giá trị hardcode => lưu vào nới khác, tham chiếu tới nó:
          Cú pháp của việc tham chiếu là gì?
          Ưu điểm của việc tham chiếu này?
          OS hỗ trợ auto việc lấy giá trị tham chiếu theo LOCATION, LANGUAGE, THEME
          Việc hỗ trợ auto này giúp app làm được điều gì?	
        + đối tượng chứa: gộp các đối tượng con lại: cùng 1 quy luật sắp xếp để hiển thị 
          Các đối tượng con nằm kề nhau theo chiều dọc | hoặc ngang, gravity
     Code tương tác với layout: vd hiển thị text
          Mong muốn text hiển thị phù hợp với thiết lập LOCATION, LANGUAGE, THEME của người dùng
          Thì làm ntn? (tránh hardcode)
     Event (sự kiện) người dùng tác động vào app: CLICK vào button, click vào text,...
          Với 1 sự kiện nào đó, muốn chạy 1 đoạn code để do-st
          Thì LAYTOUT cần làm gì?
              CODE viết như nào (2 cách)
     Trong app có các thư mục đặc biệt: Assets
     Khi sử dụng Window Explorer để copy các files + folder vào trong Assets
     Thì khi compiler: mọi file này đều đi theo app, nằm trong app
     Trong app có thể truy cập được đến các file này
     Cú pháp truy cập vào là gì?
     Lợi ích của việc app có sẵn các files (offline cũng có)?
     Ứng dụng: app hướng dẫn việc X
==> tạo app1 sử dụng cơ chế Dữ liệu chuẩn bị trước trong Assets
         Format dữ liệu: tuỳ ý, nội dung tuỳ ý
         Công cụ để hiển thị dữ liệu: tuỳ ý
         Có cần phải tiền xử lý trước khi hiển thị ko: tuỳ ý.
         Sv tự đặt ra vấn đề => tự giải quyết vấn đề
         mô tả được dữ liệu có đặc thù gì
                    dùng thuật toán nào để xử lý dữ liệu (nếu cần)
                    dùng đối tượng nào để hiển thị dữ liệu.
                    (Độ sáng tạo là ko giới hạn)
APP2 (android studio):  tạo app tương đương với Mit App inventor
  App có 3 activity
  + activity1: about: about+nút gọi sang 2 activity còn lại
  + activity2: giải toán đơn giản (tuỳ ý). Mỗi khi giải xong bài toán: gọi api tại https://k58kmt.tdh.io.vn/api
    Để gửi bài toán lên đó
    {app_by:mã số sv, input: {a:1,b:2,c:3,name:"hello tắc kè"},output:{ketluan:"vô nghiệm", abc:"xyz", nghiem:3.14}}
    Nhận lại json: {ok:1, stt:1234}
  + activity3: 
    Dùng web-view để truy cập từ 
1 trang web https://k58kmt.tdh.io.vn?Masv=mã sv của bạn


Bước 1:Chuẩn bị cấu trúc dự án và tạo thư mục tệp tin assets, xây dựng tệp nganhhoc.json.

<img width="780" height="439" alt="image" src="https://github.com/user-attachments/assets/d608b362-0f10-4a5a-8bc1-e26911eed00e" />



Hình 2.1:  Cấu trúc tệp dữ liệu nganhhoc.json tổ chức lưu trữ trong thư mục assets
Bước 2: Xây dựng lớp mô hình đối tượng (Model) NganhHoc.java để ánh xạ các trường thông tin từ JSON.

<img width="780" height="428" alt="image" src="https://github.com/user-attachments/assets/93080f3d-2bd4-469d-882d-16691aae9e4c" />


      Hình 2.2: Lớp mô hình đối tượng dữ liệu NganhHoc.java quản lý cấu trúc các trường thông tin
      
Bước 3: Lập trình Adapter (NganhAdapter.java) để đổ dữ liệu vào giao diện danh sách RecyclerView.

<img width="767" height="346" alt="image" src="https://github.com/user-attachments/assets/0af97945-5a75-4aed-8d50-5c756a0bb021" />


      Hình 2.3: Bộ điều hợp dữ liệu NganhAdapter.java xử lý liên kết luồng hiển thị danh sách
Bước 4: Lập trình hàm đọc JSON và xử lý logic tìm kiếm tại lớp trung tâm MainActivity.java.

<img width="780" height="439" alt="image" src="https://github.com/user-attachments/assets/8adf0cba-4b14-4ca0-8361-429ba34fd33d" />

Hình 2.4: Lớp điều khiển chính MainActivity.java thực thi xử lý nạp đọc dữ liệu JSON ngoại tuyến

<img width="655" height="679" alt="image" src="https://github.com/user-attachments/assets/19b9b4a2-686f-42c2-9233-ffb38c1db24d" />

Hình 2.5: Trạng thái khởi tạo mặc định hiển thị toàn bộ danh sách ngành học của Ứng dụng 1.

<img width="585" height="917" alt="image" src="https://github.com/user-attachments/assets/f9b0f32f-ca21-4250-934a-65c7ae2fc0d8" />

Hình 2.6: Giao diện ứng dụng thực thi thuật toán tìm kiếm và lọc động dữ liệu với từ khóa cụ thể

<img width="780" height="439" alt="image" src="https://github.com/user-attachments/assets/96e289f7-8bbf-4f48-a0e6-ad71b084fbc6" />

Hình 3.1: Đoạn mã xử lý điều hướng logic tại AboutActivity

<img width="663" height="865" alt="image" src="https://github.com/user-attachments/assets/62c12b02-e0d5-4577-a8ad-6d4ee5b63891" />

Hình 3.1b: Giao diện thực tế của phân hệ Giới thiệu bản thân khi khởi chạy trên thiết bị.

<img width="780" height="439" alt="image" src="https://github.com/user-attachments/assets/15212986-4459-4436-9b9b-40790a4c368d" />

Hình 3.2: code khai báo biến và MSSV tại MathActivity.java

<img width="637" height="675" alt="image" src="https://github.com/user-attachments/assets/642855a2-273d-4210-bfc7-afee6ede7879" />

Hình 3.2: Ảnh chụp màn hình MathActivity khi nhập các hệ số số học, thực hiện tính toán và nhận kết quả phản hồi thành công từ Server.

<img width="729" height="447" alt="image" src="https://github.com/user-attachments/assets/fc0d854e-673a-44c2-bf6e-c853a38ae595" />

Hình 3.2: hiển thị layout activity_webview.xml

<img width="721" height="439" alt="image" src="https://github.com/user-attachments/assets/cc8b85f4-7a3d-4a0a-8cb1-bec59d359db0" />

Hình 3.2:hiển thị cấu hình mã nguồn WebViewActivity.java

<img width="693" height="914" alt="image" src="https://github.com/user-attachments/assets/3075c81a-5b2d-4411-a2e2-adc99a4dad75" />

Hình 3.3: Ảnh chụp màn hình WebViewActivity khi hiển thị giao diện WebView tải trang thành công, tích hợp đúng tham số mã sinh viên.
