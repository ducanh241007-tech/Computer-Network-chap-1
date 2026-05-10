# COMPUTER NETWORKING CHAPTER 1
## 1.1 Tổng quan về mạng Internet
Mạng Internet là **mạng** của những thiết bị **đầu cuối/máy chủ**, các thiết bị này được liên kết với nhau qua các **đường liên kết (link)**. Các đường liên các khác nhau thì sẽ có **tốc độ truyền tải (transmission rate)** là khác nhau, được tính bằng **bits/s(bps)**. 

Khi cần gửi dữ liệu, các thiết bị sẽ gửi các **phân đoạn(segments)** sau đó sẽ được gán byte **tiêu đề(header bytes)** tạo thành **gói tin(packets)**, sau đó được gửi qua mạng tới thiết bị đích, ở đấy chúng được lắp ráp lại.

**Giao thức mạng(network protocol)** là tập hợp các quy tắc định nghĩa cách thức mà hai hay nhiều thiết bị giao tiếp với nhau.

1 số giao thức phổ biến :
- Giao thức **TCP**
- Giao thức **IP**
- Giao thức **HTTP** 
## 1.2 Biên Mạng (Network Edge)
### 1.2.1 Mạng truy cập (Access Network) 
- là mạng vật lý kết nối thiết bị cuối tới router đầu tiên (hay gọi là Edge Router)
![alt text](image-9.png)
Mạng truy cập được chia thành 3 loại dựa theo khu vực :

####  1. **Mạng truy cập gia đình**
##### **DSL(Digital Subscriber Line)**
Tận dụng các đường **dây cáp điện thoại**, thường thì với DSL thì **nhà mạng cũng chính là đơn vị cung cấp gọi điện thoại bàn** luôn. 1 cái máy **tách tần số** tại nhà sẽ tách dây cáp thành những tần số khác nhau : 
- tần số từ **0-4kHz** là cho **kênh điện thoại bàn** nghe gọi
- tần số từ **4kHz đên 50kHz** là kênh **tải lên**, dùng để upload ảnh, gửi email
- tần số từ **50kHz đến 1MHz** là kênh **tải xuống**. 

Khi đến trạm của nhà mạng thì họ sẽ dùng 1 thiết bị **tách tần số** gọi là **DSLAM** để tách thành **2 luồng gọi điện thoại bàn và Internet**.Nhưng tuy nhiên thì khoảng cách từ nhà đến trạm chỉ nên dưới 8-16km.Ngoài ra ta nhận thấy rằng có sự bất đối xứng giữa downstream và upstream.
![alt text](image-5.png)
##### **Cáp truyền hình**
- Sử dụng các đường cáp truyền hình(cáp đồng trục) 

- Sử dụng Splitter để chia dải tần số, Cable Modem(Modem cáp) để tách tín hiệu Internet ra khỏi tín hiệu TV. Tại trạm của nhà mạng thì sử dụng CMTS(Cable Modem Termination System) chuyển tín hiêu analog sang tín hiệu số và đưa vào Internet.
- Bất đối xứng, dải tần số Downstream rộng hơn rất nhiều Upstream, các chuẩn DOCSIS có : DOCSIS 2.0 Downstream 40Mbps/Upstream 30Mbps, DOCSIS 3.0 Downstream 1.2 Gbps/Upstream 100Mbps.
- Hơn thế nữa, mạng cáp lại là một môi trường chia sẻ, nghĩa là mọi gói tin được tải về từ CMTS. Ví dụ như là nếu 10 nhà cùng tải, băng thông tổng sẽ bị chia đều. Tốc độ thực tế mỗi nhà nhận được chỉ là 1.2Gbps/10=120Mbps.
![alt text](image-6.png)
##### **Cáp quang**
- Có 2 loại chính : Mạng chủ động và Mạng thụ động,
ở chương 1 ta chỉ nói về mạng thụ động

- Mỗi nhà sẽ có 1 thiết bị đổi tín hiệu điện và tín hiệu điện (ONT) được kết nối tới 1 bộ chia (Splitter) và kết nối tới bộ chuyển đổi tín hiệu quang-điện (OLT) tại trạm viễn thông và đưa ra Internet.
- ![alt text](image-8.png)
- Tín hiệu điện từ máy tính sẽ được chuyển sang tín hiệu quang tại ONT xong đi qua splitter, ở đấy splitter sẽ ghép tất cả các tín hiệu có cùng bước sóng vào và chuyển đến OLT để chuyển quang-điện xong mang ra internet. Ở nhà sẽ có 1 cái home router để phát sóng không dây, ở trạm viễn thông sẽ có 1 con telco Router để đưa tín hiệu ra Internet
![alt text](image-7.png)
2. **Mạng truy cập tổ chức** 
- Với mạng LAN có dây, người dùng Ethernet sử dụng 1 dây cáp để nối với bộ chuyển mạch (Ethernet switch), bộ chuyển mạch này, hoặc 1 mạng lưới các bộ chuyển mạch lớn hơn sẽ được kết nối với Internet
- Với mạng LAN không dây, người dùng nhận tín hiệu tới/từ điểm truy cập(AP-Access Point), thiết bị này sẽ được kết nối với mạng của tổ chức(thường là sử dụng mạng Ethernet có dây)
4. **Mạng truy cập không dây ở khu vực lớn**
- Mạng di động(Cellular) phủ sóng trong hàng chục Km, có mạng 3g 4g và 5g.
### 1.2.2 Môi trường truyền dẫn vật lý 
Các bit sẽ được gửi đi bằng cách lan truyền các **sóng điện từ (electromagnetic waves)** hoặc các **xung ánh sáng(optical pulses)** xuyên qua **môi trường vật lý (physical medium)**
Ta chia thành 2 loại môi trường truyền dẫn :
- **Truyền dẫn hữu tuyến (guided media)**
- **Truyền dẫn vô tuyến (unguided media)**
#### Cáp hữu tuyến (guided media)
Là khi các sóng/xung ánh sáng được dẫn đi thông qua **môi trường rắn**, như là **cáp quang**, **cáp xoắn đôi**, **cáp đồng trục**.
1. Cáp xoắn đôi :
Là cái rẻ nhất, phổ biến nhất, cáp xoắn đôi **chứa 2 sợi dây đồng được bọc cách điện**, mỗi sợi dày khoảng 1mm và **xoắn lại với nhau.** Các sợi được xoắn vào nhau để giảm nhiễu điện từ các cặp dây tương tự nằm kế bên. Tốc độ truyền tải của mạng LAN dùng cáp xoắn đôi dao động từ **10 Mbps đến 10 Gbps** và phụ thuộc vào **độ dày của sợi dây**, **khoảng cách giữa 2 thiết bị gửi/nhận** và **mật độ xoắn**
![alt text](image-10.png)
Có 2 loại cáp xoắn đôi
- **UTP** **(Unshielded Twisted Pair)** : Cáp xoắn đôi không bọc chống nhiễu.
- **STP** **(Shielded Twisted Pair)** : Cáp xoắn đôi có bóc chống nhiễu, có thêm 1 lớp giấy bạc bọc quanh các cặp dây để tăng cường khả năng chống nhiễu.
2. Cáp đồng trục : 
Giống cáp xoắn đôi, nó chứa **2 sợi dây đồng**, nhưng 2 sợi này **đồng tâm** chứ không song song. Nó có thể có tốc độ truyền tải cao. Cáp đồng trục có thể được sử dụng như một **môi trường chia sẻ có hướng**(guided shared medium), một số lượng hệ thống đầu cuối có thể kết nối trực tiếp vào 1 sợi cáp, từ đó **mỗi hệ thống đầu cuối** sẽ **nhận được bất cứ thứ gì được gửi bởi các hệ thống đầu cuối khác**
![alt text](image-11.png)
3. Cáp quang
Là 1 môi trường mỏng, linh hoạt chứa các **xung ánh sáng** với **mỗi xung biểu diễn cho 1 bit**, tốc độ truyền tải cũng có thể lên tận **mấy trăm Gb/s**. Nó **miễn nhiễm với nhiễu điện từ**, **dẫn rất xa(lên đến 100km)** và **bảo mật tuyệt đối**. Những yếu tố này giúp cho cáp quang trở thành 1 môi trường lí tưởng cho những đường **liên kết cự ly dài**, đặc biệt là các tuyến cáp vượt biển. 1 điểm yếu của nó là chi phí thiết bị đầu cuối quá đắt. Tốc độ truyền của cáp quang (OC hay Optical Carrier) dao động từ 51.8 Mbps đến 39.8 Gbp, hay ghi là **OC-n** với tốc độ bằng **n x 51.8 Mbps**.
![alt text](image-12.png)
#### Vô tuyến (unguided media) 
Là khi các sóng **lan truyền trong không gian**, như là **mạng LAN không dây** hoặc **một kênh vệ tinh**.
1. Sóng vô tuyến
Truyền tải **tín hiệu trong phổ điện từ**, chúng là **môi trường hấp dẫn** vì không yêu cầu lắp đặt dây, **có thể xuyên qua tường**, **cung cấp kết nối cho người dùng di động** và có **tiềm năng mang tín hiệu đi khoảng cách xa**. Sóng vô tuyến có thể chia thành 3 nhóm :
- nhóm hoạt động ở khoảng cách **gần** (1-2m)
- nhóm hoạt động ở khoảng cách **xa**(10-vài trăm km)
- nhóm hoạt động ở khoảng cách **rộng**(trải dài vài chục km)
2. Vệ tinh vô tuyến 
**Kết nối nhiều máy phát/máy thu vi ba** trên trái đất, được gọi là các trạm mặt đất. Vệ sinh **nhận các tín hiệu truyền tải trên một dải tần số**, **tái tạo tín hiệu bằng một bộ lặp**(repeater) và **truyền tín hiệu đó đi 1 dải tần số khác.**
Có 2 loại :
- Vệ tinh **địa tĩnh**
- Vệ tinh **quỹ đạo Trái Đất tầm thấp** (LEO-low-earth-orbiting satellites)

## 1.3 Lõi mạng
Là những **packet switches và links ở trung tâm** nối các **router biên/thiết bị cuối với nhau.**
![alt text](image-4.png)
Gói tin được truyền qua mỗi liên kết với tốc độ bằng với toàn bộ tốc độ truyền dẫn của liên kết đó.
### 1.3.1 Chuyển mạch gói (Packet Switching)
#### Lưu trữ và chuyển tiếp (Store and Foward Transmission) 
Đơn giản là 1 router nếu nhận 1 gói tin thì phải **nhận được đến bit cuối cùng** của gói tin đó thì **mới bắt đầu đẩy bit của gói tin** đó ra đường truyền tiếp theo 
![alt text](image-15.png)
Ví dụ : ta gửi 1 gói tin từ thiết bị A, gói tin chứa L bits đến thiết bị B qua router R, với tốc độ truyền dẫn là R bps thì tại thời điểm L/R gói tin mới đến router và tại thời điểm 2L/R gói tin mới đến B nhưng nếu switch foward luôn thì tốc độ sẽ chỉ là L/R
Ta có công thức : 
**($d_{end-to-end}$) = N x L/R**
và nếu có P gói tin thì **($d_{end-to-end}$) = (N+P-1) x L/R**
Với L là số bit trong gói tin, R là tốc độ truyền của liên kết(trong trường hợp tất cả liên kết có tốc độ R), N là số đường liên kết, N-1 là số router giữa 2 thiết bị.
#### Trễ hàng chờ và thất thoát gói tin
Mỗi switch đều có 1 **hàng chờ** để đưa gói tin sắp được chuyển tiếp vào liên kết tiếp theo. Nếu như gói tin vừa đến vào một hàng chờ nhưng thấy hàng chờ đang có những gói tin khác thì gói tin đấy phải chờ đến khi đến lượt. Trễ Hàng chờ **phụ thuộc vào mức độ tắc nghẽn** trong mạng

Bởi vì hàng chờ cũng có giới hạn nên nếu gói tin vừa đến gặp một **hàng chờ đầy** thì router sẽ **hủy/drop gói tin** đó, gây ra hiện tượng **packet loss**.
#### Bảng chuyến tiếp và giao thức định tuyến (Fowarding Table và Routing Protocol) 
Mọi thiết bị cuối đều có **địa chỉ IP**, khi muốn gửi 1 gói tin đến thiết bị cuối đó thì thiết bị đầu sẽ **gán địa chỉ IP vào tiêu đề** của gói tin. Mỗi cái router sẽ **tra bảng chuyển tiếp và tìm liên kết tiếp theo**. Bảng chuyển tiếp sẽ được đặt tự động bởi các **giao thức định tuyến**. **1 giao thức định tuyến** có thể **tìm đường đi ngắn nhất qua mỗi router đến mỗi thiết bị cuối** để xem đường đi ngắn nhất và **tạo ra bảng chuyển tiếp**.
### 1.3.2 Chuyển mạch kênh (Circuit Switching)
1 liên kết sẽ được **chia** nhỏ ra thành nhiều **kênh**(circuits), và **toàn bộ tài nguyên của kênh** đấy sẽ được dành riêng cho **1 đường truyền** (**hàng chờ, liên kết, tốc độ đường truyền**).Bởi vì tốc độ đường truyền đã được dành riêng nên thiết bị gửi có thể đảm bảo gửi dữ liệu với **tốc độ tối đa của kênh** đấy (Lưu ý là **tốc độ của kênh bằng tốc độ của liên kết/số kênh**).
![alt text](image-14.png)
#### Ghép kênh trong chuyển mạch kênh
Có 2 cách chia kênh chính là : 
- **Chia kênh theo tần số** (**Frequency-Division Multiplexing** hay **FDM**) 
- **Chia kênh theo thời gian** (**Time-Division Multiplexing** hay **TDM**)

**Chia kênh theo tần số (FDM)** : Dải băng thông của liên kết được **chia** thành **nhiều tần số khác nhau**, **mỗi kết nối** được cấp cho **1 dải tần số** riêng. **Độ rộng của 1 dải** tần số thường là **4kHz** và được gọi là **băng thông.**
![alt text](image-16.png)

**Chia kênh theo thời gian** **(TDM)**: Thời gian sẽ **chia** thành những **khung thời gian(frame)** lặp lại, 1 frame sẽ có **1 số lượng slot** nhất định, và mỗi **một kết nối** sẽ chiếm 1** slot**.
![alt text](image-17.png)
So sánh giữa Circuit Switching và Packet Switching
| Đặc điểm     | Circuit Switching | Packet Switching | 
| :----------- | :---------------- | :--------------- |
| Đường đi     | Dành riêng cho kết nối | Chia sẻ |
| Tốc độ đường truyền |Được đảm bảo cố định và không thay đổi | Thay đổi liên tục, phụ thuộc vào số lượng người truy cập |
| Hình thức dữ liệu | Dòng bit liên tục | Gói tin |
| Delay | Không có trễ hàng đợi ,ổn định | Phụ thuộc vào tắc nghẽn mạng, có khả năng sinh ra trễ hàng đợi | 
| Hiệu suất tài nguyên | **Rất lãng phí,** nếu hai bên kết nối mà không truyền dữ liệu**(Silent periods)** thì kênh đấy người khác không được dùng. | **Tối ưu,** router liên tục đẩy các gói tin **theo nhu cầu**, luôn hoạt động hết công suất. |

=> Trong viễn thông hiện tại thì **Packet Switching** đang được sử dụng nhiều hơn do hiệu suất cao hơn Circuit Switching.

### 1.3.3 Internet - Mạng của các mạng
Nhà cung cấp dịch vụ Internet (ISP)
Internet được chia thành 1 mạng lưới có các tầng.
1. **Tầng cao nhất (Tier 1 ISP (Cấp toàn cầu))** là những nhà cung cấp kết nối với nhau để **bao phủ toàn cầu**
2. **Tầng giữa (Regional ISP (Cấp quốc gia/khu vực))** là những nhà cung cấp **trả tiền để mua lưu lượng của Tier 1** để liên kết quốc tế
3. **Tầng cuối (Access ISP(Cấp truy cập))** là nhà cung cấp kéo cáp trực tiếp đến nhà, **phải trả tiền cho Tier 2 hoặc 1**
4. **Content Provider Networks** : là **những nhà cung cấp nội dung** có **hàng nghìn trong tâm dữ liệu trên toàn cầu**, thay vì phải trả tiền cho Tier 1 ISP thì họ **tự cung cấp dịch vụ đến các Access ISP/Regional ISP** luôn.
![alt text](image-18.png)
- **Kết nối ngang hàng(Peering)** là khi các **nhà cung cấp nối trực tiếp với nhau**, không ai phải trả tiền cho ai. Để cho dễ thì người ta xây **điểm trao đổi (IXP)** để các ISP **kết nối với nhiều ISP khác**.
- **Đa kết nối(Multihome)** là khi một nhà cung cấp **kết nối với 2 hoặc nhiều ISP cấp trên** cùng 1 lúc để **đề phòng rủi ro** 1 trong những ISP khác sập thì còn có nhà cung cấp dự phòng.
## 1.4 Độ trễ, thất thoát và tốc độ truyền thực tế trong mạng chuyển mạch gói (Packet-switched Networks)
### 1.4.1 Độ trễ trong mạng chuyển mạch gói
Gói tin đi qua 1 nút (máy chủ hoặc router) đến 1 nút khác sẽ phải chịu nhiều loại trễ khác nhau tại mỗi nút

Quan trọng nhất là **trễ xử lý (nodal processing delay)**, **trễ hàng đợi(queuing delay)**, **trễ tốc độ truyền(transmission delay)**, và **trễ truyền dẫn(propagation delay)**.

 **Tổng trễ tại nút (nodal delay) = 4 cái trễ cộng lại**
![alt text](image-20.png)
#### Trễ xử lý / Processing delay ($d_{proc}$)
- Là thời gian để **xem tiêu đề của gói tin**, quyết định xem nên gửi gói tin đi đâu bằng cách **tra bảng chuyển tiếp** (Fowarding Table) , và **kiểm tra xem có lỗi/thất thoát bit** trong gói tin không và các yếu tố khác.

- Trong router tốc độ cao thì trễ xử lý chỉ là **vài micro giây** và được coi như là **hằng số**, sau khi xử lý thì đẩy vào queue.
#### Trễ hàng đợi / Queueing delay ($d_{queue}$)

- Là thời gian gói tin phải chờ nếu hàng chờ có gói tin khác, phụ thuộc vào số lượng gói tin đang có trong hàng chờ. Nếu hàng chờ không có gói tin nào thì $d_{queue}$ = 0, nếu hàng chờ chứa nhiều gói tin thì $d_{queue}$ có thể lớn. Trong thực tế thì $d_{queue}$ dao động từ micro giây đến mili giây.

Giả sử 1 đường truyền có tốc độ truyền dẫn là R (bps), 1 router nhận a gói tin trong 1s với mỗi gói tin có L bits.
=> số bit trung bình đến hàng chờ là L.a bits/s. Giả sử hàng chờ vô hạn, ta có **cường độ lưu lượng(Traffic intensity)** của hàng chờ sẽ là **L.a/R**. 

Nếu
- **La/R > 1** thì tốc độ số bit gửi về sẽ lớn hơn tốc độ xử lý, nếu độ lớn hàng chờ vô hạn thì hàng chờ sẽ dài ra vô hạn,**$d_{queue}$ -> vô hạn**.
- **La/R tiến tới 0** nghĩa là tốc độ số bit gửi về rất chậm so với khả năng đấy của router => **$d_{queue}$ xấp xỉ 0**
- **La/R tiến tới 1** : Nếu gói tin được gửi đi **liên tục sau mỗi L/R** giây thì không có vấn đề **$d_{queue}$ = 0** , nhưng trong thực tế thì gói tin sẽ được **gửi liên tục trong 1 khoảng thời gian**, lúc đấy gói tin đầu tiên sẽ có $d_{queue}$ = 0, gói thứ n có $d_{queue}$ = (L-1)/R. Trung bình sẽ là **$d_{queuetb}$ = (n-1)L/2R**.

**Packet loss** : như nói ở phần trước, bởi vì queue có hạn nên khi 1 **packet đến 1 queue đầy** thì router sẽ **bỏ packet** đấy đi, gây ra hiện tượng packet loss, packet loss **tỉ lệ thuận với cường độ lưu lượng**.
#### Trễ truyền dẫn / Transmission Delay ($d_{trans}$)
- Là thời gian mà router cần để đưa toàn bộ số bit vào trong liên kết tiếp theo.

$d_{trans}$ = L/R 
với L là số bit trong gói tin (bit), R là tốc độ truyền dẫn(bps)
#### Trễ lan truyền
- Là thời gian mà các bit đi qua dây dẫn để đến router tiếp theo, tốc độ của các bit này có thể xấp xỉ, hoặc bằng tốc độ ánh sáng, dao động từ 2.10^8^ m/s đến 3.10^8^ m/s.

$d_{prop}$ = d/s với d là khoảng cách của dây dẫn (m) và s là tốc độ của liên kết.
 ### 1.4.2 Trễ từ thiết bị đầu - cuối
 $d_{end-to-end}$ = $\sum_{i=1}^{N}$ $d_{nodal.i}$
 ### 1.4.3 Tốc độ truyền thực tế 
 **Tốc độ truyền thực tế trung bình = F/T** với F là số lượng bits trong file, T là thời gian truyền.
 #### Nguyên lý nghẽn cổ chai (Bottleneck Link)
 Giả dụ Server gửi file cho máy qua 1 router, tốc độ đường truyền từ server đến router là **Rs**, tốc độ truyền từ router dến máy là **Rc**. Nếu **Rs > Rc** thì nghĩa là router sẽ xử lý chậm hơn tốc độ bit đến, và tốc độ thực tế sẽ **bằng Rc**. Ngược lại nếu **Rs < Rc** thì router sẽ xử lý nhanh hơn tốc độ bit đến, và tốc độ thực tế sẽ **bằng Rs**
 ![alt text](image-21.png)

 Nhận ra điều này, ta giả sử 1 server gửi đến máy 1 file và giữa chúng có **N-1 router và N đường truyền**, và tốc độ thực tế sẽ bằng **min{R1,...,Rn}**

 Nếu có chia sẻ băng thông thì 
 tốc độ thực tế = min{Rs, Rc, Rcore/n} với n là số kênh của băng thông.
![alt text](image-22.png)
## 1.5 Kiến trúc phân tầng
Các chức năng trong mạng thông thường
được phân loại và nhóm lại thành một số
tầng theo chiều dọc được gọi là “lớp”
(layer)
- Đối với các hệ thống phức tạp: đơn giản
hóa hệ thống bằng việc chia chức năng

- Cho phép xác định rõ nhiệm vụ của mỗi
bộ phận và quan hệ giữa chúng

- Cho phép dễ dàng bảo trì và nâng cấp
hệ thống
### Các mô hình tham chiếu
Các mô hình phân tầng được gọi là
“Mô hình tham chiếu” (Reference 
Model)
- Các loại mô hình tham chiếu:
- Mô hình OSI (7 lớp) do ISO đưa ra
![alt text](image-2.png)
- Mô hình TCP/IP (mô hình Internet)
![alt text](image-3.png)
### Chức năng các lớp 5 tầng TCP/IP
#### PHY (Lớp vật lý)
- Biến đổi dòng bit logic thành tín hiệu vật lý
phù hợp với đường truyền vật lý (ở bên phát) 
và ngược lại (ở bên thu): điều chế/giải điều
chế, biến đổi, khôi phục tín hiệu .v.v.
#### Data Link (Liên kết dữ liệu)
- Phát hiện và sửa lỗi khi truyền dữ liệu giữa
các thực thể trong mạng (switch, router, 
thiết bị đầu cuối)
- Nhận dữ liệu từ lớp Mạng, đóng gói dữ liệu
lớp Mạng vào các khung (frame) phù hợp với
mạng vật lý
- Tổ chức các bit trong frame theo thứ tự định
nghĩa sẵn
- Hoạt động theo nguyên tắc từng chặng
#### Network (lớp Mạng)
- Định tuyến trên một mạng gồm nhiều
nút trung gian giữa nguồn và đích
- Đánh địa chỉ lớp mạng
#### Transport (Lớp giao vận)
- Đảm bảo truyền dữ liệu tin cậy giữa 2 
thiết bị đầu cuối (end-to-end)
- Điều khiển luồng (flow control)
- Chia nhỏ hoặc ghép các khối dữ liệu từ lớp Phiên
#### Application (lớp Ứng dụng)
- Cung cấp các giao diện lập trình cho
ứng dụng của người sử dụng
## Sự đóng gói (Encapsulation)
- Bên gửi: Mỗi tầng thêm vào các thông tin điều khiển
vào phần đầu gói tin (header) và truyền xuống tầng
dưới
- Bên nhận: Mỗi tầng xử lý gói tin dựa trên thông tin 
trong phần đầu, sau đó bỏ phần đầu, lấy phần dữ liệu
chuyển lên tầng trên.
- Tầng ứng dụng tạo ra dữ liệu gốc, sau đó tầng giao vận bọc transport header chứa số hiệu cổng - Port, lúc này gói tin được gọi là segment, sau đó tầng mạng bọc thêm network header(chứa địa chỉ ip nguồn/đích) tạo ra datagram. Tại tầng liên kết datagram được bọc Link Header chứa địa chỉ MAC và thành Frame. Cuối cùng tại tầng vật lý sẽ chuyển Frame thành bit và truyền đi
![alt text](image-1.png)
## 1.6 An ninh mạng
### Malware 
- Các phần mềm độc hại hay còn được gọi là **malware** có thể **xâm nhập vào thiết bị để đánh cắp dữ liệu, xóa file**,.... Malware bây giờ có thể **tự nhân bản**, nghĩa là nó có thể dùng máy đã bị nhiễm để **phát tán malware** đi chỗ khác. **1 mạng lưới malware** sẽ được gọi là **botnet**.
### Tấn công DoS (denial-of-service attacks)
#### Có 3 hình thức phổ biến 
- **Vulnerability Attack** : kẻ tấn công sẽ gửi những g**ói tin cực kì tinh vi** để đánh vào một **lỗi lập trình** cụ thể
- **Bandwidth flooding** : kẻ tấn công gửi **1 đống gói tin** vào đường truyền khiến cho link bị tắc nghẽn, router sẽ vào trạng thái **La/R >= 1**, dẫn đến **trễ vô hạn và packet loss**
- **Connecting flooding** : kẻ tấn công mở hàng triệu kết nối ảo để **hút cạn tài nguyên**

Tuy nghiên nếu kẻ tấn công sử dụng 1 IP duy nhất thì máy chủ có thể nhận diện và chặn kết nối từ cái IP đấy, vì vậy **DDoS** sinh ra, DDoS đơn giản là kẻ tấn công sử dụng **1 mạng lưới máy tính** để **phân tán các gói tin** đi 1 cách không ai nghi ngờ.
### Nghe lén gói tin (Packet Sniffing)
- Người ta sẽ sử dụng 1 ứng dụng để có thể **track những gói tin trong shared media**, nếu bạn sử dụng 1 giao thức không mã hóa thì kẻ tấn công có thể **đọc gói tin** và biết được thông tin quan trọng
#### Địa chỉ IP nguồn giả mạo
- **Để mạo danh một máy tính** đáng tin bằng cách giả làm IP của người khác