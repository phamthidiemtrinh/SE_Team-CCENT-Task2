#TCP-IP
## 1. Transport layer
- tương đương với tầng transport trong mô hình OSI
- điều khiển các điểm kết nối end-to-end : có hai giao thức nổi tiếng là UDP và TCP
- Ghép các phiên truy nhập của các ứng dụng : các máy muốn trao duổi dữ liệu với nhau thì phải có các phiên truy nhập, các phiên truy nhập đều đi chung trên một kết nối end-to-end
- Phân mạch dữ liệu : phân thành các phân đoạn nhỏ
- Cung cấp điều khiển nguồn: điều tiết lưu lượng di chuyển data một cách hợp lý trên kết nối đầu cuối, tránh mất mát dữ liệu, không xử lý kịp thời ữ liệu được gửi đến ( chỉ có ở giao thức TCP và không phải lúc bào cơ chế điều khiển nguồn cũng thi hành, chỉ khi nhận được required thì mới thi hành) 
- Cung cấp kỹ thuật tryền ( Connection-oriented) :
	- Connection-oriented : truyền theo hướng kết nối (khi hai máy có ý định truyền ữ liệu cho nhau thì trước tiên phải thành lập được kết nối luận lý giữa hai máy)
	- Connectionless : khi máy tính có gói tin thì gói tin được tuyền trực tiếp vào đường truyền mà không phải thành lập kết nối luận lý
- Độ tin cậy: đảm bảo sự truyền và nhận dữ liệu (chỉ một vài giao thức cung cấp kiểu truyền này)

## 2. So sánh kiểu truyền tin cậy và kiểu truyền tổng lực
![](http://1.bp.blogspot.com/_pjnY1C-CtyM/TSKBeQ5Pi7I/AAAAAAAAABQ/2ehWXmV8Y30/s1600/reliable+vs+best-effort.jpg)
- trong đó Protocol là loại giao thức
- Sequencing : đánh số thứ tự 

## 3. Giao thức UDP (usermDatagram Protocal)
- thuộc lớp transport
- cho phép các ứng dụng truy nhập vào lớp mạng mà không cần thông tin về cơ chế quản lý độ tin cậy
- là một giao thức dạng connectionless
- Cung cấp cơ chế kiểm tra lỗi giới hạn
- cung cấp cơ chế best-effort
- không có cơ chế phục hồi dữ liệu ( đẩy tất cả các gói tin vào đường truyền mà không quan tâm bên nhận có nhận được đầy đủ dữ liệu hay không)

## 4. UDP-Header
![](https://upload.wikimedia.org/wikibooks/en/d/d9/Header_of_UDP.jpg)
- có hai trường là Source port và Destination port
- trong đó port là cách định danh (địa chỉ)  một session đang truy nhập vào đường truyền
- một gói tin có khả năng dài 2mũ 16 byte

## 5. TCP 
- hoạt động tại tầng trasport trong mô hình TCP/IP
- Giúp các ứng dụng có thể truy nhập vào tầng mạng
- kết nối theo hướng connection-oriented
- hỗ trợ truyền và nhận tại cùng một thời điểm (full-duplex)
- Cung cấp cơ chế kiểm tra lỗi, đánh số thứ tự các gói tin để có thể ráp lại cho đúng ở dầu nhận
- Cơ chế báo nhận : gửi gói tin cho đến khi đầu nhận báo nhận thì dừng
- Cung cấp cơ chế phục hồi dữ liệu

## 6 TCP –Header
![](http://intronetworks.cs.luc.edu/1/html/_images/tcp_header.png)
- trong đó
	- sequence nuber : dùng để đánh số thứ tự ( từ đây tính được số byte đã được truyền)
	- Acknowledgment number (Ack) : báo nhận xem đã nhận được gói tin nào và mong muốn nhận được byte thứ tự nào tiếp theo
	- Header-length : cho biết header dài bao nhiêu từ (gấp bao nhiêu lần của 4byte)
	- Các phần bit sau ( resv,ns,cwt,ece,urg,ack,psh, rst,syn,tin ) : bit điều khiển.
	- Window size : kích thước cửa sổ
	- TCP checksum : dùng để kiểm tra lỗi cho toàn bộ gói tin TCP
	- urgent pointer : sử dụng cho trường hợp khẩn cấp ( ưu tiên đữ liệu dùng chung cờ điều khiển urgent)
	- Options : cho phép lập trình thêm tính năng cho giao thức 

## 7.ứng dụng của chồng giao thức TCP/IP
- Truyền file (FTP,TFTP, network file system)
- Thư điện tử (SMTP)
- Truy nhập từ xa (telnet,rlogin)
- Quảng lý mạng ( SNMP)
- Quảng ý tên miền

## 8. Mapping layer 3 to layer 4
![](https://lh5.googleusercontent.com/bNqM7LMqZQqQSkXERX_nUhG2dU15kGagSeMbKFrwPaR7r4gO4UOcC4_OYyyL8PIIwaGin-_QsSWR2NDw4eo8jDYtL5YNGuk_s8b1-og9nJ06iKccpvQ9xt8BqUvq5Ht_RaF6aNBOe7Vs5sp9iQ)
-  Gói tin ip gồm 2 phần : ip header và và phần được bọc trong segment của lớp 4
- protocol : cho biết phần dữ liệu chứa loại gói tin phần giao thức nào

## 9. Mapping layer 4 to applications
- truyền dữ liẽu từ ứng dụng phải thông qua lớp trasport. 
- các ứng dụng muốn truy nhập vào lớp 4 phải sử ụng các port quy định cho nó.
- Ví dụ:
![](http://image.slidesharecdn.com/icnd110s01l05understandingthetcpiptransportlayer-130312094244-phpapp01/95/cours-cisco-10-638.jpg?cb=1363081403)
- Khi nào thì DNS sử dụng TCP, khi nào thì sử dụng UDP:khi DNS client truy vấn lên server thì phần lớn là sử dụng UDP.Còn TCP sẽ được sử dụng trong quá trình zone transfer (trao đổi dữ liệu zone giữa DNS primary và các DNS secondary)

## 9. Thiết lậ một kết nối – bắt tay 3 bước ( three –way handshake)
kết nối từ host tới host phải thông qa đám mây internet
![](https://lh4.googleusercontent.com/-HJ9ehwCKl04/V_3spI49HZI/AAAAAAAARtw/o7vXJJnTz_Q7fq7lndRIb3x9y7SlS-A9wCLcB/s1600/3-buoc.png)
- thông qua 3 bước

## 10. Cơ chế Flow control
- khi máy gửi gửi quá nhiều dữ liệu cho máy nhận, buộc máy nhận phải buffer các gói dữ liệu vào bộ đệm để xử lý, nhưng khi vùng đệm đầy thì máy nhận phải báo cho máy truyền ngừng truyền nữa
- khi may nhận xử lý xong (trống vùng đệm), thì nó gửi tín hiệu cho phép máy gửi tiếp tục truyền dữ liệu như cũ

## 11. TCP acknowledgment
- khi máy gửi gửi một gói tin cho máy nhận thì bắt buộc máy nhận phải gửi trở lại một ack ( báo nhận) cho máy gửi nếu không máy gửi sẽ chờ trong một khoảng thời gian và tiếp tục gửi lại.
![](https://lh3.googleusercontent.com/gRNdNlTwNzF3mNMwbjpDmsKDLXxb40CWRsEfsRZ5Nj80S9YESW99jdkkHvQoHUpELboSXY6V4DnvMhJSCAn6Pg7jAEyrSLMEIp1CtEix-RqMogoB7vlPFwuDXZ4yV4jn-jCNVN60vk9Mtn9GUQ)
- trong đo window size=1 nghĩa là chỉ gửi và nhận duy nhất 1 gói dữ liệu
-  Fixed windowing : vì gửi 1gói và nhận một gói chậm sẽ làm tăng window size lên nên đưa ra giải pháp gửi một lốc lớn dữ liệu ( ví dụ window size =3 thì cứ nhận được 3 gói thì cmới báo nhận một lần)
-  giả sử trong 3 segment gửi  đi, có một segment bị lỗi ( không đến được nơi nhận)  thì nơi nhận sẽ tự động ack 3 lại ( yêu cầu gửi lại segment 3), đồng thời yêu cầu gửi thông qua window size = 2 vì nơi nhận chỉ chịu được window size =2

## 12. Chuỗi tiến trình, và số hiệu báo nhận TCP
![](https://lh3.googleusercontent.com/Kt9JdzfgJFqkRoNhooc3raM4NKVPFdySZY3qFoJOm_llj35RLTPsxkbucbbGkF1SpvD_EbvQkkW-BqbczD6nUL1cAKlkeWgjZJMpkOM3i_cENCbFtBRj1P2BNm7YGS1YfSJvrBeHBP-KBvJ9FQ)
- số sequence là n thì số ack sẽ là n+1 : nghĩalà bên nhận đã nhận được n byte data và mong muốn nhận được tiếp byte thứ 11
 
 # Ethernet lan
Trong quá trình thao tác mạng, chúng ta cần thông qua 


	




