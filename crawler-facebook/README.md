#crawler-facebook

## Giới thiệu: 

Đây là ví dụ về việc Crawl dữ liệu từ Facebook bằng công cụ Puppeteer

## Collab
- [@nghminh163](https://github.com/nghminh163)

## Nhiệm vụ
- Login with Facebook
- Lấy dữ liệu

## Nội dung
- Mình tiến hành facebook bằng cách tìm các trường liên quan đến email và password và nhập chúng sau đó bấm nút login
```js
    await page.type("#email", "test_mqyhoct_app@tfbnw.net");
    await page.type("#pass", "a123123123");
    await page.click("#loginbutton");
```
Các bạn hoàn toàn có thể login bằng Facebook này do mình tạo đây là test user, không liên quan đến Facebook thường (Cái này mình lấy qua f12 trên chrome giống như việc crawl data = các lib có tính năng tương tự)

- Tìm các post: Ở đây mình mò ra 1 post facebook được bọc là 1 class `._5jmm ._5pat` nên mình sẽ sử dụng 
```js
    document.getElementsByClassName('_5jmm _5pat');
``` 
để có thể lấy ra tất cả các post trên News Feed

- Lấy các trường tương ứng
Hiện tại mình không có thời gian làm toàn diện nên mình chỉ hướng dẫn crawl các status (Chỉ có chữ, nền trắng)
Mình tiến hành forEach mảng post ở bên trên và sử dụng Selector để lấy các data như tên, time, content của status. Các bạn hoàn toàn có thể sử dụng Facebook trên mình có test 2 cái status để lấy data về. Mình có mò ra được `.fwb` là name của người up bài, `.timestampContent` là thời gian up, `._5_jv ._58jw` là nội dung của status.

## P/s
- Bạn hoàn toàn có thể collab bằng cách gửi issue thêm các tên class của các post tương ứng ví dụ như post share, post ảnh,...
- Hàm `page.evaluate` bản chất là sẽ chạy trong console của chrome nên nếu bạn sử dụng `console.log` hãy set `headless` thành `false` và mở devtools lên để xem
- Facebook trên là test hình như không đổi được pass =))) mong các bạn không đổi pass và cái Facebook đấy không làm được gì đâu nên đừng chôm Facebook của tôi :<
