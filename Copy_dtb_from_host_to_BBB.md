Cách build ra thằng dtb (device tree source ) mới rồi copy sang thẻ , để BBB nó boot lại :

Cách 1 : Đầu tiên , sau khi sửa node trong device tree thì trỏ tới chỗ dts nhé 

sau đấy ta build file dts đấy ra dtb thông qua lệnh : make ARCH=arm CROSS_COMPILE=$CC dtbs (nhớ là đứng ở KERNEL)

<img width="624" height="332" alt="image" src="https://github.com/user-attachments/assets/768ba90c-ee40-4dff-a1ad-cf95c7a81238" />

Nó sẽ ra 1 file dtb mới tên vẫn giữ nguyên là am335x-boneblack.dtb (device tree binary) rồi copy nó vào thể nhớ để load xuống BBB . 

Sau đấy cắm thẻ nhớ vào nếu thấy thẻ chưa được mount (nó ghi là Part ở cột mountpoint) ấy 
Dùng lệnh : sudo mount /dev/sdb1 /media/rootfs/ 

<img width="624" height="109" alt="image" src="https://github.com/user-attachments/assets/7af67ca6-13d7-44f0-8b02-4c08c4de1e33" />

Thì thẻ (sdb1) sẽ được trỏ tới media/rootfs 
Sau đấy (nên tạo 1 tab mới ) , cd tới media/rootfs/boot/dtbs/kernel-version( ấn tab nó sẽ ra kernel-version) của mình ở đây là 5.4.288-bone69 .

Sau đấy copy cái đường dẫn: /media/rootfs/boot/dtbs/5.4.288-bone69 ( đây là kernel-version của mình thôi nhé ) .  ( Nói chung là lấy đường dẫn để cop file sang thôi ) .
Sau đấy bước cuối , copy file am335-boneblack.dtb tới cái đường dẫn trên nhé , nhớ là copy như thế này này : 

<img width="624" height="17" alt="image" src="https://github.com/user-attachments/assets/755fe8c5-bc74-451a-93da-384983bf5298" />

Lệnh đây : cp -f arch/arm/boot/dts/am335x-boneblack.dtb  /media/rootfs/boot/dtbs/5.4.288-bone69 . Phải để đường dẫn file từ arch thì nó mới nhận biết được. 

Rồi dùng tới lệnh (sync)  để đợi nó cop xong nhé , cho an toàn .
Sau đấy ls - l ra thì xem ngày giờ mới nhất của am335x-boneblack.dtb  , để xem có đúng là nó được cop chưa nhé 
THÁO THẺ NHỚ RỒI CẮM XUỐNG BBB , boot lên là được , tìm file trong device tree thì tự làm .



Cách 2 : Nói nhanh thôi ,  khi có được file dtb mới  thì SSH từ mấy host sang  máy target là BBB ( dùng scp ném  thằng file mới vào  phân vùng /media/rootfs/boot/..... .  Sau đấy reboot lại là xong . 
Cách này nhanh hơn .
