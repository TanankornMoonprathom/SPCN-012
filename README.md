# SPCN-012

**Hypervisor Technology**

- คือ เทคนิคการจำลองให้ OS หลายระบบสามารถทำงานได้พร้อมๆกันบน Host ได้ โดย Hypervisor คือการตั้งค่าระบบ OS แต่ละระบบไม่ให้มีการทำงานทับซ้อนกัน  Hypervisor ถูกเรียกได้อีกวาส Virtual Machine Management (VMM)
- จุดประสงค์ของ Hypervisor
  - คือการทำให้คอมพิวเตอร์หลายเครื่องสามารถแบ่ง Platform บน Hardware เดียวกันได้ โดยปกติ OS ทำการออกแบบมาให้ทำงานกับ Hardware แบบ 1:1 เท่านั้น แต่ Processor กับ RAM จำนวนมากทำให้สามารถ Run ได้พร้อมกันหลายตัว
- ประโยชน์ของ Hypervisor
  - มีความปลอดภัย ถ้าคุณต้องการทดสอบ Software ซึ่งอาจจะมีความเสียง หรือเป็นอันตรายต่อ hardware จะสามารถทดสอบผ่าน Hypervisor ได้ เพราะหาก OS มี Virus จะไม่ส่งผลกระทบกับ File ที่อยู่บน Host
- Hypervisor มี 2 ประเภท
  - Hypervisor Type 1 (Baremetal Architecture)
          - จะทำงานโดยตรงกับ Hardware ของ Server
  - Hypervisor Type 2 (Hosted Architecture)
          - จะทำหน้าที่เป็น Software ของ Server ดังนั้นจึงไม่ต้องใช้ OS อื่นเพื่อที่จะใช้ Hypervisor ตัวนี้

อ้างอิง: [personet.co.th](https://personet.co.th/hypervisor/)

**Container Technology**

- คือ เปรียบเสมือนตู้ Container ที่อยู่บนเรือที่สามารถยกเข้า/ยกออกได้ สำหรับ Infrastructure ที่ต้องเตรียมสำหรับ Container จะประกอบด้วย
  - Infrastructure – โครงสร้างพื้นฐาน หรือ Physical Server นั่นเอง
  - Host Operating System – เป็น Operating System ที่ติดตั้งบน Server อาจจะเป็น Windows หรือ Linux ก็ได้
  - Container Runtime – หรือที่หลาย ๆ คนรู้จักกันในชื่อ Container Engine เป็น Software ที่ใช้รองรับการสั่งงานผ่าน Command Line สำหรับ Brand ที่นิยมใช้กันคือ Docker ครับ แต่บางรายอาจจะพัฒนา container platform ขึ้นมาใช้เอง
  - Binary/Library – เป็นชุดข้อมูลที่อาจจะเป็นไฟล์ภาพ,ไฟล์เสียง หรือไฟล์ที่ใช้ในการรันโปรแกรม
  - Application – เป็น Software หรือ โปรแกรมที่ออกแบบให้ End user ใช้งาน เช่น Web Browser และ Spreadsheet เป็นต้น
- ประโยชน์ของ Containers
  - ใช้ Resource น้อยกว่า เนื่องจากโครงสร้างของ Containers ไม่จำเป็นต้องมี Operating System image เหมือนกับ VM ทำให้ใช้งาน Resources ไม่ได้มากเท่า
  - เพิ่มช่องทางในการ Run Application เนื่องจาก Application ที่ Run อยู่บน Containers สามารถ Deploy ไปบน OS และ Hardware อะไรก็ได้ (อาจไม่ Support ทั้งหมด แต่ Support เป็นส่วนใหญ่)
  - Operation ทำงานได้อย่างราบรื่น เพราะ Application ที่อยู่บน Containers จะทำงานได้เหมือนเดิม ไม่ว่าจะ Deploy ไปไว้บนไหนก็ตาม
  - ให้ประสิทธิภาพการทำงานดี เพราะว่าสามารถ Deploy ได้ไว Update Patch ได้ง่ายไม่กระทบการทำงานส่วนอื่น และยัง Scale ได้ง่าย หาก Resource ไม่เพียงพอ

อ้างอิง: [blog.cloudhm.co.th](https://blog.cloudhm.co.th/containers-vs-vm/)

**Monolithic MicroService**

- Monolithic Architecture คือ สถาปัตยกรรมการออกแบบ และพัฒนาซอฟต์แวร์ ระบบหรือบริการ (Service) ที่รวมทุกส่วนเอาไว้ในสภาพแวดล้อม (Environment) เดียวกัน ใช้ฐานข้อมูลเดียวกัน (Database) ตามรูปด้านล่าง
- Microservices คือ การแบ่งระบบออกเป็นส่วนย่อยๆ แทนที่จะรวมเป็นระบบเดียวอย่าง Monolithic
- ข้อดีของ Monolithic
  - ง่ายต่อการพัฒนา
  - ง่ายต่อการใช้ทดสอบ
  - ง่ายต่อการ Deploy
  - Scale ในแนวกว้างได้ง่าย เพราะสามารถทำซ้ำ ๆ ได้ผ่าน Load Balancer
- ข้อดีของ Microservices
  - แต่ละ Service แยกออกจากกัน ทำให้แต่ละทีมสามารถโฟกัสกับ Service ที่รับผิดชอบได้โดยตรง
  - สามารถปรับเปลี่ยน และใช้เทคโนโลยีใหม่ ๆ ได้ง่ายขึ้น Developer สามารถเลือกภาษา หรือ Framework ต่าง ๆ ที่เหมาะสมกับ Service ส่วนนั้นได้ โดยไม่ต้องยึดติดกับภาษาที่เลือกมาแต่แรก
  - สามารถ Deploy อย่างต่อเนื่องได้ เพราะแต่ละ Service สามารถ Deploy เองได้ ไม่ต้องทำไปพร้อม ๆ กันทั้งหมด
  - แต่ละ Service สามารถ Scale เองได้

อ้างอิง: [ooneunhye.medium.com](https://ooneunhye.medium.com/monolithic-architecture-%E0%B8%84%E0%B8%B7%E0%B8%AD-%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3%E0%B9%80%E0%B8%AB%E0%B8%A3%E0%B8%AD-5737857fe9be) และ
[blog.skooldio.com](https://blog.skooldio.com/microservices-vs-monolithic/#Microservices)

**Proxmox**

- Proxmox คือ แพลตฟอร์มการจัดการเซิร์ฟเวอร์โอเพ่นซอร์ซที่สมบูรณ์แบบสำหรับการจำลองเสมือนขององค์กร ได้รับการพัฒนาโดย Proxmox Server Solutions ในออสเตรียภายใต้ Internet Foundation of Austria และเผยแพร่ภายใต้ GNU General Public License
- ข้อดี PROXMOX
  - ใช้ Debian เป็น OS หลัก  ซึ่งเป็น Linux มีความ Stable สูง , รองรับ Driver Hardware ที่หลากหลาย  และพัฒนาอย่างต่อเนื่อง  ทำให้ PROXMOX เป็นระบบจัดการ VM ที่มีความ Stable สูง
  - ใช้ Kernel-based Virtual Machine (KVM) เป็นระบบ Virtualization ที่ลงลึกระดับฮาร์ดแวร์ Bare Metal (ไม่ใช่ Virtualization ที่รันอยู่บน OS อีก Layer นึง ตัวอย่างเช่น VirtualBox )
  - ทำให้ PROXMOX ดึงประสิทธิภาพ Hardware Virtualization ได้มากที่สุด
  - รองรับ Virtualization แบบ KVM และแบบ Containers ( LXC )
  - ระบบจัดการผ่านหน้าเวบ ( Web UI ) ทำให้ควบคุมได้ง่าย
  - กำหนด Users / Permissions ได้หลายระดับ
  - มี Firewall ในตัว
  - มีระบบ Backup ในตัว
  - ทำ Snapshot ได้ ( ไม่จำเป็นต้อง Shutdown VM ก่อน Backup )
  - รองรับ Storage ที่หลากหลาย  ( รองรับมากที่สุดในกลุ่ม Virtualization ด้วยกัน )
  - รองรับ VirtIO
  - รองรับ Monitoring
  - รองรับ ZFS
  - รองรับ Bridge / NAT
  - รองรับ Ceph ( กรณีทำ Cluster )
  - รองรับ Migration ( กรณีทำ Cluster )
  - รองรับ Replication ( กรณีทำ Cluster )
  - รองรับ High Availibity ( กรณีทำ Cluster )
  - Feature ที่พัฒนา  เปิดให้เราใช้ได้หมด  ไม่มีกั๊ก
  - เป็น Opensource ใช้ฟรีงาน อัพเดทฟรี ตลอดไป
- ข้อเสีย PROXMOX
  - จะต้องแบ่ง Ram ไว้ให้ Proxmox อย่างน้อย 4-8GB
  - ยังมี Bug ให้เห็นอยู่บ้าง  ( สั่งงานบางอย่างแล้วมี error )
  - ในบาง error อาจจะต้องใช้ความรู้เบื้องต้น Linux ในการแก้ไขปัญหา
  - บาง Feature ไม่สามารถทำผ่านหน้า Web UI ได้โดยตรง  ต้องทำผ่าน Cli  เช่นการ Attach Disk เข้า VM  หรือการจัดการ Cluster ระดับสูง

อ้างอิง: [quickserv.co.th/](https://www.quickserv.co.th/knowledge-base/technology/VMware-vSphere-%e0%b8%81%e0%b8%b1%e0%b8%9a-Proxmox-%e0%b8%aa%e0%b8%b3%e0%b8%ab%e0%b8%a3%e0%b8%b1%e0%b8%9a%e0%b8%98%e0%b8%b8%e0%b8%a3%e0%b8%81%e0%b8%b4%e0%b8%88-%e0%b9%83%e0%b8%8a%e0%b9%89%e0%b9%81%e0%b8%9a%e0%b8%9a%e0%b9%84%e0%b8%ab%e0%b8%99%e0%b8%94%e0%b8%b5%e0%b8%97%e0%b8%b5%e0%b9%88%e0%b8%aa%e0%b8%b8%e0%b8%94/) และ
[blog.limitrack.com](https://blog.limitrack.com/proxmox-basic/)

**CEPH**

- Ceph เป็นซอฟต์แวร์ทำ Software-Defined Storage ที่เป็น Open Source ได้รับความนิยมติดตั้งเป็น Backend การเก็บข้อมูลในระบบ OpenStack และมีขนาดของ community ที่ใหญ่ขึ้นเรื่อย ๆ
- Ceph จะประกอบด้วยส่วนประกอบหลัก ๆ 3 ส่วน คือ
  - MON (Monitor Node)ทำหน้าที่ดูแลสถานะของ Ceph cluster
  - OSD (Object Storage Node) เป็น Node ทำหน้าที่เก็บข้อมูล ของระบบ หากต้องการใช้ CephFS จะต้องมี
  - MDS (Metadata Node) ทำหน้าที่ดูแลสถานะของ file hierarchy (สำหรับ CephFS เท่านั้น)
- ข้อดีของ Ceph
  - เป็น Open source ไม่มีค่าใช้จ่ายสำหรับตัวซอฟต์แวร์ แต่หากต้องการ Support ก็จะมี subscription ของ Vender หลาย ๆ ค่าย เช่น RedHat, SuSe ขายอยู่เช่นกัน
  - สามารถให้บริการได้หลากหลายรูปแบบ (Block, Object, Filesystem)
  - สามารถขยายระบบได้ง่าย เพียงเติมเครื่องเข้าระบบ
  - ใช้ Hardware ทั่ว ๆ ไป ไม่จำเป็นต้องเป็น Hardware เฉพาะแต่ละส่วนมีความคงทนของระบบ (High Availability) ไม่ว่าจะเป็น MON, MDS หรือ OSD
- ข้อเสียของ Ceph
  - จะเปลืองดิสก์กว่า Storage แบบปกติ เนื่องจากเทคโนโลยีในการเก็บ ข้อมูลของ Ceph ที่จะเก็บสำเนาของข้อมูลไว้ 2–3 ชุด สำหรับ High Availablity

อ้างอิง: [clusterkit.co.th](https://www.clusterkit.co.th/blogs/ceph-storage/)

**NFS**

- NFS ย่อมาจาก Network File System คือบริการที่ทำให้เครื่องคอมพิวเตอร์สามารถเข้าถึงไฟล์และไดเรกทอรี บนเครื่องคอมพิวเตอร์เครื่องอื่นได้เหมือนกับใช้งานเครื่องของตัวเอง โดยสามารถใช้บริการได้อย่างสะดวก ง่ายและมีประสิทธิภาพที่ดีผ่านระบบเครือข่ายเน็ตเวิรค โดยระบบปฏิบัติการของเครื่องเหล่านั้นไม่จำเป็นต้องเป็นระบบปฏิบัติการเดียวกันกับเครื่องแม่ข่ายที่ให้บริการ NFS (เครื่อง NFS Server)  การทํางานของ NFS จะมีลักษณะเป็น Client Server โดยที่เราอาจต้องมีการกําหนดค่าสําหรับ Client แต?ละตัวในกรณีที่ต้องการกําหนดสิทธิในการเข?าถึงข?อมูลที่แตกต?างกัน 
ซึ่งปัจจุบัน NFS ได้มีออกมา 3 เวอร์ชั่น โดยเวอร์ชั่น 3 เป็นแบบที่อาศัย RPC (Remote Procedure Call) โดยป็นโปรโตคอลที่ไม่มีสถานะ (Stateless Protocol) หรือหมายถึงเป็นโปรโตคอลที่ทำงานแบบถามมา-ตอบไป เมื่อได้มีการส่งหรือรับคำตอบกลับไปแล้วก็เสมือนจบการติดต่อไปเลย คือไม่ต้องมีการรอคอยดำเนินการใดๆ จากอีกด้านหนึ่งต่อไป

อ้างอิง: [mindphp.com](https://www.mindphp.com/%E0%B8%84%E0%B8%B9%E0%B9%88%E0%B8%A1%E0%B8%B7%E0%B8%AD/73-%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3/2170-nfs-%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3.html)


