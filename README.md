mở thư mục ios bằng XCode và bắt đầu tạo các thiết lập tùy chỉnh:
* Đảm bảo "Runner" được chọn trong XCode.
* Trong cửa sổ chính, chọn nút "Runner" bên dưới "PROJECT" (KHÔNG phải bên dưới TARGETS)
* Chọn tab “Info”
* Trong phần “Configurations”, ta làm như sau:
    * Đổi tên “Debug” thành “Debug-dev”
    * Đổi tên “Release” thành “Release-dev”
    * Đổi tên “Profile” thành “Profile-dev”
    * Duplicate “Debug-dev” và đổi tên thành “Debug-live”
    * Duplicate “Release-dev” và đổi tên thành “Release-live”
    * Duplicate “Profile-dev” và đổi tên nó thành “Profile-live” Việc thiết lập các thông số phía trên sẽ tạo các cấu hình “Debug”, “Release” và “Profile” tương ứng cho từng flavor.
![alt text](https://github.com/nduc86686/config_flavor_ios/blob/main/flutter_flavors_ios_configurations.png?raw=true)
Bây giờ có thể thiết lập các “custom schemes” bằng cách thực hiện như sau:
* Đảm bảo rằng "Runner" được chọn trong XCode
* Chọn “Product -> Scheme -> Manage Schemes…” trên thanh công cụ chính.
* Thiết lập "dev" scheme:
    * Chọn "Runner" scheme, nhấp vào biểu tượng cài đặt ở trên cùng bên trái và chọn "Duplicate"
    * Đổi tên scheme thành “dev”
    * Đảm bảo rằng “Shared” được chọn
    * Đóng hộp thoại
* Thiết lập "live" scheme:
    * Chọn lại "Runner" scheme, nhấp vào biểu tượng cài đặt ở trên cùng bên trái và chọn "Duplicate"
    * Đổi tên scheme thành "live"
    * Đối với mỗi phần (“Run”, “Test”, “Profile”, “Analyze”, “Archive”) ở bên trái, hãy thay đổi cấu hình build phiên bản “-live” tương ứng.
    * Đảm bảo rằng “Shared” được chọn
    * Đóng hộp thoại
    * ![alt text](https://github.com/nduc86686/config_flavor_ios/blob/main/flutter_flavors_ios_live_scheme.png?raw=true)
Bây giờ có thể thiết lập các “custom schemes” bằng cách thực hiện như sau:
* Đảm bảo rằng "Runner" được chọn trong XCode
* Chọn “Product -> Scheme -> Manage Schemes…” trên thanh công cụ chính.
* Thiết lập "dev" scheme:
    * Chọn "Runner" scheme, nhấp vào biểu tượng cài đặt ở trên cùng bên trái và chọn "Duplicate"
    * Đổi tên scheme thành “dev”
    * Đảm bảo rằng “Shared” được chọn
    * Đóng hộp thoại
* Thiết lập "live" scheme:
    * Chọn lại "Runner" scheme, nhấp vào biểu tượng cài đặt ở trên cùng bên trái và chọn "Duplicate"
    * Đổi tên scheme thành "live"
    * Đối với mỗi phần (“Run”, “Test”, “Profile”, “Analyze”, “Archive”) ở bên trái, hãy thay đổi cấu hình build phiên bản “-live” tương ứng.
    * Đảm bảo rằng “Shared” được chọn
    * Đóng hộp thoại
* ![alt text](https://github.com/nduc86686/config_flavor_ios/blob/main/1604855a-b0d3-4cee-843b-0eb30ac6a355.jpeg?raw=true)
* Quay lại danh sách “schemes”, bây giờ ta có thể xóa scheme “Runner” hiện có. Sau khi xóa danh sách schemes sẽ trông như thế này:
*  ![alt text](https://github.com/nduc86686/config_flavor_ios/blob/main/05baf6a7-24fb-4057-9ed7-d82a08055714.jpeg?raw=true)
* Chạy ứng dụng iOS
Bây giờ chúng ta có thể chọn “dev” scheme trong thanh điều hướng trên cùng của XCode và chạy ứng dụng.
LƯU Ý: Nếu bạn gặp lỗi lạ lúc buildtừ XCode, hãy thử chuyển đổi giữa các scheme dev/live hoặc thử khởi động lại XCode hoặc chạy ứng dụng iOS từ Android Studio.
Lúc chạy thành công, ta sẽ thấy đầu ra console tương tự như đối với ứng dụng Android ở Phần 1:
2020-10-03 14:44:05.525493+0200 Runner[26055:336596] flutter: STARTED WITH FLAVOR dev
2020-10-03 14:44:05.526672+0200 Runner[26055:336596] flutter: API URL https://dev.flutter-flavors.chwe.at

Hiện tại tên ứng dụng trên iPhone vẫn là “flutter_flavors” và khi chạy cả hai phiên bản (dev/live), ta vẫn chỉ có một ứng dụng trên điện thoại của mình:
 ![alt text](https://github.com/nduc86686/config_flavor_ios/blob/main/407d7a63-adf2-4dee-84c8-3b575d945bc9.jpeg?raw=true)
Đặt bundle id cho từng Flavor
Mở file Info.plist thấy một khóa có tên Bundle identifier chứa giá trị động $(PRODUCT_BUNDLE_IDENTIFIER). Ta sẽ cần sửa đổi giá trị của khóa này trong Build settings:
* Trong XCode, chọn "Runner" trong cấu trúc dự án XCode
* Chọn “Runner” bên dưới TARGET
* Chuyển đến tab "Build Settings"
* Trong phần “Packaging”, tìm khóa “Product Bundle Identifier”
* Nhấp vào mũi tên nhỏ bên trái
* Đặt giá trị cho từng cấu hình build:
    * Debug-dev: at.chwe.flutterflavors.dev
    * Debug-live: at.chwe.flutterflavors
    * Profile-dev: at.chwe.flutterflavors.dev
    * Profile-live: at.chwe.flutterflavors
    * Release-dev: at.chwe.flutterflavors.dev
    * Release-live: at.chwe.flutterflavors
 ![alt text](https://github.com/nduc86686/config_flavor_ios/blob/main/e2434826-476f-4f02-b199-46db846ce047.jpeg?raw=true)
config icon flavor Android & IOS
https://www.youtube.com/watch?v=Vhm1Cv2uPko&ab_channel=MarcusNg 
lib
-base
—bloc
—base_bloc
package
-login
—lib
—bloc
—auth_state


  
