Kết luận:

Cách để tăng performance cho react dựa vào webpack đó là:

\+ Sử dụng kĩ thuật code splitting để giảm dung lượng tải khởi tạo page

\+ Sử dụng kĩ thuật prefetch, preload kết hợp với code splitting để có
performance, UX hiệu quả

\+ Sử dụng các tool analyze size để kiểm tra

Các nội dung cần đọc:

1.  Thư viện react-loadable

<https://github.com/jamiebuilds/react-loadable>

Hỗ trợ code splitting cho react component, tối ưu performance code.

Với ReactJS chỉ có thể code spitting cho router. Với react-loadable, nó
hỗ trợ splitting nhỏ hơn nữa ở mức component. Đây giải pháp tối ưu
performance, hạn chế load các component không cần thiết khi khởi tạo,
giảm thời gian inital load.

Ví dụ:

\+
<https://techmaster.vn/posts/35604/chunking-code-hay-code-splitting-trong-react-voi-react-loadable>

2.  Hiểu về prefetch, preload để tối ưu performance, UX

<https://medium.com/webpack/link-rel-prefetch-preload-in-webpack-51a52358f84c>

Ví dụ:

\+ Giả sử trang home page, người dùng thường xuyên mở dialog Login. Thi
khi mới tải trang home page, mình không cẩn tải ngay dialog Login vì nó
chưa cần thiết. Mình set chế độ là prefetch (tải lúc rảnh rỗi) người
dùng muốn mở dialog Login thì nó sẽ hiển thị ngay, giảm bớt thời gian
tải. Như vậy với cách này, vừa giúp giảm thời gian inital load vừa có
thể hiển thị ngay các thành phần lazy load.

3.  Tree shaking webpack

<https://medium.com/webpack/better-tree-shaking-with-deep-scope-analysis-a0b788c0ce77>

Hiểu hơn về cách webpack loại bỏ code dự thừa, không sử dụng khi bundle
file. Không đơn giản là phát triển các biến import chưa sửa dụng (quên
xoá đi). Nó có loại bỏ các module export không sử dụng.

4.  1 series hướng dẫn về Webpack căn bản

<https://viblo.asia/p/webpack-tu-a-den-a-webpack-la-gi-1VgZveNMKAw>

5.  Các tool analyze size webpack

<https://viblo.asia/p/cac-tool-de-analyze-size-trong-project-javascript-RQqKLL8MK7z>

<https://developers.google.com/web/tools/chrome-devtools/coverage>

6.  Đánh giá về create-react-app

<https://www.quora.com/What-are-the-pros-and-cons-of-using-create-react-app-versus-just-placing-react-script-tags>

<https://stackshare.io/create-react-app>

<https://geekscreed.com/blog/use-create-react-app-to-scaffold-next-react-app/>
