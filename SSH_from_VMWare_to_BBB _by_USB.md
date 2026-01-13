CÁCH SSH TỪ MÁY ẢO VMWARE VÀO BBB BẰNG CỔNG USB

Sau khi đã cắm boot thẻ sd xuống BBB rồi nhé , và lúc boot chắc bạn cũng biết rồi ( nhấn giữ S2 và cắm nguồn vào ) 

<img width="913" height="454" alt="image" src="https://github.com/user-attachments/assets/1a84efe5-2f89-45f6-9016-9311293f56d9" />
(  Ảnh này là khi USB UART  kết nối với máy host là Ubuntu nhé ) 

Kết quả sau khi boot image OS xuống board BBB .

<img width="916" height="485" alt="anh2" src="https://github.com/user-attachments/assets/ce103be9-3161-4695-9286-5510f3efe201" />


CÁC BƯỚC SSH TỪ VM VÀO BBB QUA USB MINI : 

Bước 1 : Nạp module USB Ethernet Gadget (g_ether) trên BBB
Giao tiếp giữa VM Ubuntu (host: 192.168.7.1) và BBB (gadget: 192.168.7.2) qua cổng USB mini dạng g_ether.
Lưu ý là máy ảo VM Ubuntu thì cứ dùng trên MobaXterm cho tiện nhé , copy lệnh các thứ cho dễ .
Nhớ là trên BBB (qua UART Console) cổng COM UART 

Ta gõ lệnh : 
sudo modprobe g_ether 9 


