#TCP-IP
``````````````````````

```````````````````
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

## 10. Mapping layer 4 to applications
- truyền dữ liẽu từ ứng dụng phải thông qua lớp trasport. 
- các ứng dụng muốn truy nhập vào lớp 4 phải sử ụng các port quy định cho nó.
- Ví dụ:
![](http://image.slidesharecdn.com/icnd110s01l05understandingthetcpiptransportlayer-130312094244-phpapp01/95/cours-cisco-10-638.jpg?cb=1363081403)
- Khi nào thì DNS sử dụng TCP, khi nào thì sử dụng UDP:khi DNS client truy vấn lên server thì phần lớn là sử dụng UDP.Còn TCP sẽ được sử dụng trong quá trình zone transfer (trao đổi dữ liệu zone giữa DNS primary và các DNS secondary)

## 9. Thiết lậ một kết nối – bắt tay 3 bước ( three –way handshake)
kết nối từ host tới host phải thông qa đám mây internet
![](https://lh4.googleusercontent.com/-HJ9ehwCKl04/V_3spI49HZI/AAAAAAAARtw/o7vXJJnTz_Q7fq7lndRIb3x9y7SlS-A9wCLcB/s1600/3-buoc.png)
- thông qua 3 bước

## 11. Cơ chế Flow control
- khi máy gửi gửi quá nhiều dữ liệu cho máy nhận, buộc máy nhận phải buffer các gói dữ liệu vào bộ đệm để xử lý, nhưng khi vùng đệm đầy thì máy nhận phải báo cho máy truyền ngừng truyền nữa
- khi may nhận xử lý xong (trống vùng đệm), thì nó gửi tín hiệu cho phép máy gửi tiếp tục truyền dữ liệu như cũ

## 12. TCP acknowledgment
- khi máy gửi gửi một gói tin cho máy nhận thì bắt buộc máy nhận phải gửi trở lại một ack ( báo nhận) cho máy gửi nếu không máy gửi sẽ chờ trong một khoảng thời gian và tiếp tục gửi lại.
![](https://lh3.googleusercontent.com/gRNdNlTwNzF3mNMwbjpDmsKDLXxb40CWRsEfsRZ5Nj80S9YESW99jdkkHvQoHUpELboSXY6V4DnvMhJSCAn6Pg7jAEyrSLMEIp1CtEix-RqMogoB7vlPFwuDXZ4yV4jn-jCNVN60vk9Mtn9GUQ)
- trong đo window size=1 nghĩa là chỉ gửi và nhận duy nhất 1 gói dữ liệu
-  Fixed windowing : vì gửi 1gói và nhận một gói chậm sẽ làm tăng window size lên nên đưa ra giải pháp gửi một lốc lớn dữ liệu ( ví dụ window size =3 thì cứ nhận được 3 gói thì cmới báo nhận một lần)
-  giả sử trong 3 segment gửi  đi, có một segment bị lỗi ( không đến được nơi nhận)  thì nơi nhận sẽ tự động ack 3 lại ( yêu cầu gửi lại segment 3), đồng thời yêu cầu gửi thông qua window size = 2 vì nơi nhận chỉ chịu được window size =2

## 13. Chuỗi tiến trình, và số hiệu báo nhận TCP
![](https://lh3.googleusercontent.com/Kt9JdzfgJFqkRoNhooc3raM4NKVPFdySZY3qFoJOm_llj35RLTPsxkbucbbGkF1SpvD_EbvQkkW-BqbczD6nUL1cAKlkeWgjZJMpkOM3i_cENCbFtBRj1P2BNm7YGS1YfSJvrBeHBP-KBvJ9FQ)
- số sequence là n thì số ack sẽ là n+1 : nghĩalà bên nhận đã nhận được n byte data và mong muốn nhận được tiếp byte thứ 11

```````````````````````````````

`````````````````````````````````
 # Ethernet LAN
- Trong quá trình thao tác mạng, chúng ta cần thông qua một loại mạng có quy mô nhỏ tốc độ cao , hỗ trợ chia sẻ mạng trong hệ thống.
- mạng nội bộ có thể là mạng có diện tích nhỏ hoặc rất lớn
- Một trong số đó là ethernet lan

## 1. Các thành phần của mạng LAN
- các máy tính : pc, server..
- các kết nối mạng : cạc mạng kkết nối, phương tiện truyền dân
- các thiết bị mạng: hubs, switch router
- giao thức truyền số liệu : ethernet, IP, ARP, DHCP

## 2. Chức năng của mạng LAN
- dùng để chia sẻ dữ liệu, ứng dụng
-  tài nguyên
- cung cấp đường kết nối tới một mạng LAN khác	
- Quy mô mạng Lan có thể có kích thước nhỏ (SOHO) được sử dụng tại nhà hoặc văn phòng
-quy mô mạng LAN lớn ( enterprise) được sử dụng tại các doanh nghiệp.....

## 3. Các chuẩn về mạng LAN
- các chuẩn chủ yếu tập trung ở mô hình OSi , hai lớp là physical layer và data link layer
- lớp LLC (logical link control) : giao tiếp với các hệ thống layer 3
- lớp MAC (media access control)  : điều khiển việc truy nhập đường truyền phía dưới
![](http://ptgmedia.pearsoncmg.com/images/chap3_9781587143762/elementLinks/03fig04.jpg)
- có các chuẩn đi từ lớp physical đến lớp data link, một số khác thì không

## 4.CSMA/CD
-  CSMA/CD (Carrier Sense Multiple Access with Collision Detection) : Phương pháp đa truy nhập sử dụng sóng mang có phát hiện xung đột
- Phương pháp này sử dụng cho topo dạng tuyến tính, trong đó tất cả các trạm của mạng đều được nối trực tiếp vào bus. Mọi trạm đều có thể truy nhập vào bus chung (đa truy nhập) một cách ngẫu nhiên và do vậy rất có thể dẫn đến xung đột (hai hoặc nhiều trạm đồng thời truyền dữ liệu). 
- Tư tưởng : một trạm cần truyền dữ liệu trước hết phải “nghe” xem đường truyền đang rỗi hay bận. Nếu rỗi thì truyền dữ liệu đi theo khuôn dạng đã quy định trước. Ngược lai, nếu bận (tức là đã có dữ liệu khác) thì trạm phải thực hiện một trong 3 giải thuật sau (gọi là giải thuật “kiên nhẫn”)
- Tạm “rút lui” chờ đợi trong một thời gian ngẫu nhiên nào đó rồi lại bắt đầu nghe đường truyền (Non persistent - không kiên trì) :hiệu quả trong việc tránh xung đột vì hai trạm cần truyền khi thấy đường truyền bận sẽ cùng “rút lui” chờ đợi trong các thời đoạn ngẫu nhiên khác.→ Nhược điểm có thể có thời gian chết sau mỗi cuộc truyền
- Tiếp tục “nghe” đến khi đường truyền rỗi thì truyền dữ liệu đi với xác suất = 1: khắc phục nhược điểm có thời gian chết bằng cách cho phép một trạm có thể truyền ngay sau khi một cuộc truyền kết thúc. → Nhược điểm: Nếu lúc đó có hơn một trạm đang đợi thì khả năng xảy ra xung đột là rất cao
- Tiếp tục “nghe” đến khi đường truyền rỗi thì truyền đi với xác suất p xác định trước (0 < p <1) : Trung hoà giữa hai giải thuật trên
- Để có thể phát hiện xung đột, cải tiến thành phương pháp CSMA/CD (LWT - Listen While Talk - nghe trong khi nói) tức là bổ xung thêm các quy tắc:
	- Khi một trạm đang truyền, nó vẫn tiếp tục nghe đường truyền. Nếu phát hiện thấy xung đột thì nó ngừng ngay việc truyền nhưng vẫn tiếp tục gửi sóng mang thêm một thời gian nữa để đảm bảo rằng tất cả các trạm trên mạng đều có thể nghe được sự kiện xung đột đó.
	 - Sau đó trạm chờ đợi một thời gian ngẫu nhiên nào đó rồi thử truyền lại theo các quy tắc của CSMA
- nguồn tham khảo : https://voer.edu.vn/m/cac-phuong-phap-truy-nhap-duong-truyen-vat-ly/61e112e1

## 5.Cấu trúc của Ethernet  frame
![](http://www.learncisco.net/assets/images/icnd1/21-ethernet-frame-tructure.jpg)

## 6. Các hình thức truyền thông trong một mạng LAN
- Unicast : truyền thông 1-1 ( từ một host tới một host)
- Broadcast : từ một host gửi dữ liệu đến tất cả các host trong hệ thống
- Muticast: một host truyền dữ liệu đến một nhóm host trong hệ thống.

## 7. Địa chỉ MAC
- là loại địa chỉ vật lý trong môi trường layer 2, là địa chỉ máy ( duy nhất)
- là dãy nhị phân dài 48 bit được chia thành hai phần :
	- 24 bit đầu: có 2 bit dùng để chỉ thi cho những tính năng đặc biệt của địa chỉ, 22 bit sau dùng để định danh cho nhà sản xuất ( là duy nhất) OUI ( định danh cho nhà sản xất)
	- 24 bit sau : khi mỗi nhà sản xuất được cấp OUI thì họ gán tiếp các dãy địa chỉ cho các thiết bị cho họ sản xuất ra. ( định danh cho từng thiết bị được sản xuất)
- được thể hiện dưới dạng hexa


``````````````````````````

``````````````````
# Cabing
Chúng ta cần có các đường dây cab để đấu nôi các thitết bị với nhau

## 1. Đấu nối vào mạng Ethernet Lan
- cần thiết bị là Network Interface Card
- các chuẩn về phương tiện truyền dẫn và yêu cầu:
![](http://image.slidesharecdn.com/icnd110s01l08-150412082121-conversion-gate01/95/ccna-icnd110-s01l08-3-638.jpg?cb=1428827288)
- trong đó
	- T: cáp xoắn đôi (chống nhiễu0
	- UTP : cáp xoắn đôi không có lớp vỏ bảo vệ
	- STP: cáp xoắn đôi có lớp vỏ bảo vệ
	- Category : phân hạng cab
	- X: cab  quang
- ngày nay chúng ta thường sử dụng chuẩn 1G : buộc phải sử dụng từ cate 5e trở lên

## 2. Sự khác nhau giữ các card mạng:
- Các đầu kết cuối thường là R-J-45 và R-J-11
- R-J-11 sử dụng cho đường ây điện thoại ,, hỗ trợ voice
- Đầu nối quang : sử dụng 2 đường dây quan, một dường dây phát tín hiệu (TX) và đầu thu (RX)
- Card gbic : tốc độ 1Gb/S có đầu kết cuối là RJ45

## 3. Unshielded Twisted-pair cable
-  có 1 lớp vỏ nhựa bên ngoài, gồm tổng cộng 4 cặp sợi xoắn đôi (cable xoắn đôi), trên mỗi doạn cable đều có các mã màu chỉ thị. Một đoạn cable xoắn đôi sẽ được kết nối với một đầu R-J-45.
- tốc độ truyền từ 10-1000 Mb/s 
- Giá thành tương đối rẻ tiền và phổ biến
-các phương tiện truyền dẫn và kích thước đầu nối nhỏ
- chiều ài cable có thể thay đổi được

## 4.Đầu nối RJ-45 
- có 1 lơp vỏ nhựa bên ngoài vài 8 miếng đồng bên trong ( 8 chân truyền đi)
![](https://rubimages-liberty.netdna-ssl.com/hi-res/10005USOP.png)

## 5. Cách triển khai cable xoắn đôi
- hai kĩ thuật bấm cable
![](http://www.cablinginstall.com/content/cim/en/articles/2011/03/differences-between-t568a-and-t568b-explained/_jcr_content/leftcolumn/article/footerimage.img.jpg/1343747829379.jpg)
- bấm cable chéo:
![](https://www.facebook.com/photo.php?fbid=1690041167974013&set=a.1469600833351382.1073741830.100009044372312&type=3&theater)
- bấm cable thẳng là khi cả hai đầu đều cùng chuẩn ( chỉ sử dụng 4 sợi là 1,2,3,6)
- Sử dụng cáp thẳng khi đấu giữa: 
	- switch  với : rounter, pc, server
	- hub với : PC , server
- sử dụng cáp chéo khi đấu nối  giữa
	- switch với : switch, hub
	- hub với hub
	- rounter với: rounter, PC
	- PC với PC
- Cùng nhóm (hub, switch) cáp chéo, khác nhóm cáp thẳng
![](http://image.slidesharecdn.com/ccnapres-130226194445-phpapp02/95/ccna-cisco-61-638.jpg?cb=1361908565)

````````````````````````

`````````````````````````````
# WAN
- Khi đấu nối với nhà cung cấp dịch vụ để thuê kênh thuê riêng, thì cần một loại mạng khác
- WAN : wide area network
-  khi thuê đường truyền WAN link của nhà cung cấp dịch vụ, khi đó họ sẽ thực hiện mở một dường truyền vật lý, và đưa vào office một con DCE và rounter riêng của doanh nghiệp sẽ đấu nối ào đường truyền của họ bằng một loại cáp đặc biệt, từ đó truyền dữ liệu vào DCE và truyền lên đường truyền của nhà cung cấp dịch vụ
![](http://www.blogalways.com/wp-content/uploads/2015/02/dce-dte.png)
- DCE chiệu trách nhiệm trong việc đồng bộ tín hiệu
-Các loại cable đấu nối trong WAN
![](http://ptgmedia.pearsoncmg.com/images/chap04_1587051613/elementLinks/fig16.gif)
- cáp serial : đấu nối vào link line.
- cổng WIC-1T
- có 2 loại cable là : 1T và 2T
- trong môi trường lab thì không cần giả lập toàn bộ hệ thống mạng truyền dẫn 
- cable cấu hình:  cáp console có một đầu 9 chân





	




