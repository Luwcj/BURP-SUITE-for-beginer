- Mở Burpsuite -> Proxy -> Bật Intercept -> Open browser.
- Gán url challenge vào browser của Burpsuite.
Và đây là giao diện khi thực hiện các bước trên:
![](https://media.discordapp.net/attachments/1098605833371267172/1099167511913713734/image.png?width=791&height=426)

Đây là gợi ý mà tác giả đưa ra: Content is not the only part of an HTTP response!
Ta gửi yêu cầu HTTP GET này tới Repeater:
![](https://media.discordapp.net/attachments/1098605833371267172/1099259073955909743/image.png?width=797&height=427)
![](https://media.discordapp.net/attachments/1098605833371267172/1099262481291018282/image.png?width=479&height=427)

Vẫn còn 1 gợi ý nữa: Get an administrator access to the webpage.
Ta thấy ở Request không có Heaer-RootMe-Admin, thử thêm vào Request để đi tiếp nhé:
![](https://media.discordapp.net/attachments/1098605833371267172/1099263341450494002/image.png?width=481&height=427)
Vậy là có password rồi : HeadersMayBeUseful