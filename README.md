# ยินดีต้อนรับสู่ขั้นตอนการติดตั้ง OS ผ่าน Docker
Docker เป็นแพลตฟอร์มที่ใช้สำหรับการพัฒนาและรันแอปพลิเคชันโดยใช้คอนเทนเนอร์ (Container) ซึ่งช่วยให้แอปพลิเคชันทำงานได้อย่างเสถียรในทุกสภาพแวดล้อม ไม่ว่าจะเป็นเครื่องของนักพัฒนา,เซิร์ฟเวอร์หรือบนคลาวด์ รวมถึงการใช้สภาพแวดล้อมในการทำงานเพื่อเรียกใช้ระบบปฏิบัติการ Windows/MacOS ซึ่งในวิธีการใช้คำสั่งจะต้องเพิ่ม [Github Codespaces](https://github.com/codespaces) สามารถสร้างให้มีอย่างน้อยหนึ่ง Repository ระหว่างนั้นแนะนำตั้งค่า Machine type ประมาณ 2 Core RAM 8 - 32 GB โดยไม่ส่งผลกระทบ CPU ในทุกอุปกรณ์ เนื่องจากสามารถรัน Image ผ่านเซิร์ฟเวอร์ของบราวเซอร์โดยตรง

# ส่วนเนื้อหา
1:[ขั้นตอนติดตั้ง](https://github.com/MCFirsting/Windows-Docker-Install-TH/tree/main?tab=readme-ov-file#%E0%B8%82%E0%B8%B1%E0%B9%89%E0%B8%99%E0%B8%95%E0%B8%AD%E0%B8%99%E0%B8%95%E0%B8%B4%E0%B8%94%E0%B8%95%E0%B8%B1%E0%B9%89%E0%B8%87%E0%B8%9C%E0%B9%88%E0%B8%B2%E0%B8%99%E0%B8%84%E0%B8%B3%E0%B8%AA%E0%B8%B1%E0%B9%88%E0%B8%87)

2:[คำเตือน](https://github.com/MCFirsting/Windows-Docker-Install-TH/tree/main?tab=readme-ov-file#%E0%B8%84%E0%B8%B3%E0%B9%80%E0%B8%95%E0%B8%B7%E0%B8%AD%E0%B8%99)

3:[Q&A](https://github.com/MCFirsting/Windows-Docker-Install-TH/tree/main?tab=readme-ov-file#qa)

# ขั้นตอนติดตั้งผ่านคำสั่ง (Windows)
```js
sudo su
sudo apt update
sudo apt install -y docker.io docker-compose
mkdir user && cd user
wget -O windows.yml https://raw.githubusercontent.com/MCFirsting/OS-Docker-Install-TH/refs/heads/main/windows.yml
sudo docker-compose -f windows.yml up
```
# ขั้นตอนติดตั้งผ่านคำสั่ง (MacOS)
```js
sudo su
sudo apt update
sudo apt install -y docker.io docker-compose
mkdir user && cd user
wget -O macos.yml https://raw.githubusercontent.com/MCFirsting/OS-Docker-Install-TH/refs/heads/main/macos.yml
sudo docker-compose -f windows.yml up
```
เมื่อทำงานจะเชื่อมต่อเซิร์ฟเวอร์ลิ้งค์ที่แสดงพอร์ตให้เราเข้าไป
ถ้าสังเกตว่ามีอยู่สองพอร์ต แนะนำไปที่พอร์ต 8006 เพื่อดูระหว่างการติดตั้ง Windows

หากเข้าการใช้งานได้แต่ประสิทธิภาพไม่ลื่นบนมือถือ
แนะนำติดตั้งโปรแกรม AnyDesk ได้ทั้งมือถือและคอม

สามารถเลือกเวอร์ชั่น [Windows](https://github.com/dockur/windows/?tab=readme-ov-file#how-do-i-select-the-windows-version) ตามต้องการระหว่างติดตั้งครั้งแรก โดยค่าตั้งต้นจะเป็น Windows 10 Enterprise LTSC รุ่นนี้เหมาะสำหรับการประหยัดทรัพยากรหรือโปรแกรมที่ไม่จำเป็นเมื่อติดตั้ง Windows หากต้องการติดตั้งไฟล์ ISO ที่กำหนดเองสามารถใส่ลิ้งค์โหลดโดยตรงได้ แต่จะใช้เวลาการดาวน์โหลดขึ้นอยู่กับไฟล์ ISO

นี่คือตัวอย่างการนำไฟล์จาก Tiny10

```
environment:
  VERSION: "https://archive.org/download/tiny-10_202301/tiny10%2023h1%20x64.iso"
```

# เรื่องสำคัญ
อย่าลืมหยุดงาน GitHub Codespaces ตลอดเพื่อไม่เกินจำนวนโควต้า
สามารถตรวจสอบ[โควต้า](https://github.com/settings/billing/summary)ได้ที่นี่ (เป็นผลเฉพาะบัญชี Microsoft เท่านั้น)

หากต้องการลับมาใช้งานไหม่ให้ใช้คำสั่ง
```js
cd user && sudo docker-compose -f windows.yml start
```
หากเกิดข้อผิดพลาดกระทันหันระหว่างใช้งานไห้ใช้คำสั่งเพื่อหยุดการทำงาน
```js
sudo docker-compose -f windows.yml stop
```

# 🚫คำเตือน
หากทุกคนได้ทำการซื้อโปรแกรมหรือเกมเพื่อไปจำลอง Windows/MacOS ส่งผลให้บางโปรแกรมอาจไม่รองรับได้ ทางผมจะไม่รับผิดชอบในการกระทำเหล่านี้ ที่สำคัญอย่าสำรองข้อมูลเช่น รูปภาพ,วีดีโอ บางครั้งหากการทำงานใน Codespaces เกิดข้อผิดพลาดจะสูญเสียข้อมูลสำคัญได้ แนะนำไห้สำรองผ่าน Cloud ตลอดเพื่อความปลอดภัย เนื่องจากส่งผลให้กินพื้นที่ข้อมูลทำให้คอนเทนเนอร์เสียหาย ข้อมูล Windows/MacOS ทั้งหมดจะศูนย์เปล่าทันที ดังนั้นหากใช้พื้นที่ข้อมูลควรเหลือ 3GB ขึ้นไป

# Q&A
Q:ลงโปรแกรมและเกมได้ไหม?

A:ลงได้บางโปรแกรมและเกมที่ทรัพยากรน้อย ถ้าต้องการลงเกมที่มีกราฟฟิกจริงๆ แนะนำแอป [Winlator](https://github.com/brunodev85/Winlator/releases) เป็นหนึ่งทางเลือกที่ดี แต่จะรองรับได้แค่บางอุปกรณ์ที่สเปคพอประมาณ

Q:ทำไมตอนติดตั้ง Windows ถึงไม่มีเสียง?

A:ส่วนใหญ่ถ้าลงเป็น RDP จะไม่มีไดร์เวอร์เสียงอยู่แล้ว แนะนำติดตั้ง [VB-Cable](https://vb-audio.com/Cable/index.htm) เพื่อให้ไดเวอร์เสียงทำงาน จากนั้นรีสตาร์ท เสียงที่ได้ยินส่วนใหญ่จะมาจาก Remote Desktop เท่านั้น

Q:ระยะเวลาใช้งานจำกัดไหม?

A:โดยปกติ Codespaces จะทำงานสิ้นสุดใน 4 ชั่วโมงและข้อมูลในคอนเทนเนอร์จะไม่หาย หากใช้ระยะเวลานานเกินความจำเป็นอาจจะทำให้หมดโควต้าเร็ว แนะนำวิธีประหยัดโควต้าภายใน 120 ชั่วโมง = 5 วัน ควรใช้งานวันละ 2 ชั่วโมง (หากยิ่งเร็วยิ่งประหยัดขึ้น)

Q:จะเกิดอะไรขึ้นหากโควต้าหมด?

A:Codespaces จะยังไม่สามารถเข้าใช้งานจนกว่ารอรอบบิลรีเซ็ตต่อผู้ใช้งานทั้งหมดในเดือนถัดไป แต่ก็ระวังเรื่องการเก็บรักษา Codespaces หากไม่มีการเข้าใช้งานเป็นเวลา 30 วันจะถูกลบโดยอัตโนมัติ
