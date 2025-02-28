# ยินดีต้อนรับสู่ขั้นตอนการติดตั้ง Windows ผ่าน Docker
Docker เป็นแพลตฟอร์มที่ใช้สำหรับการพัฒนาและรันแอปพลิเคชันโดยใช้คอนเทนเนอร์ (Container) ซึ่งช่วยให้แอปพลิเคชันทำงานได้อย่างเสถียรในทุกสภาพแวดล้อม ไม่ว่าจะเป็นเครื่องของนักพัฒนา, เซิร์ฟเวอร์หรือบนคลาวด์ รวมถึงการใช้สภาพแวดล้อมในการทำงานเพื่อเรียกใช้ระบบปฏิบัติการ Windows ซึ่งในวิธีการใช้คำสั่งจะต้องเพิ่ม [Github Codespaces](https://github.com/codespaces) สามารถมีอย่างน้อยในหนึ่ง Repository ที่ต้องสร้าง แนะนำตั้งค่าประมาณ 2 Core RAM 8 - 32 GB

ขั้นตอนติดตั้งผ่านคำสั่ง
```js
sudo su
sudo apt update
sudo apt install -y docker.io docker-compose
mkdir cloudpc && cd cloudpc
wget -O windows.yml https://raw.githubusercontent.com/MCFirsting/Windows-Docker-Install-TH/main/windows.yml
sudo docker-compose -f windows.yml up
```
เมื่อทำงานจะเชื่อมต่อเซิร์ฟเวอร์ลิ้งค์ที่แสดงพอร์ตให้เราเข้าไป
ถ้าสังเกตว่ามีอยู่สองพอร์ต แนะนำไปที่พอร์ต 8006 เพื่อดูระหว่างการติดตั้ง Windows

หากเข้าการใช้งานได้แต่ประสิทธิภาพไม่ลื่นบนมือถือ
แนะนำติดตั้งโปรแกรม AnyDesk ได้ทั้งมือถือและคอม

สามารถเลือกเวอร์ชั่น [Windows](https://github.com/dockur/windows/?tab=readme-ov-file#how-do-i-select-the-windows-version) ตามต้องการระหว่างติดตั้งครั้งแรก โดยค่าตั้งต้นจะเป็น Windows 10 Enterprise LTSC รุ่นนี้เหมาะสำหรับการประหยัดทรัพยากรหรือโปรแกรมที่ไม่จำเป็นเมื่อติดตั้ง Windows

# เรื่องสำคัญ
อย่าลืมหยุดงาน GitHub Codespaces ตลอดเพื่อไม่เกินจำนวนโควต้า
สามารถตรวจสอบ[โควต้า](https://github.com/settings/billing/summary)ได้ที่นี่

# การกลับมาใช้งานใหม่ในคำสั่ง
```js
cd cloudpc && sudo docker-compose -f windows.yml start
```

# 🚫คำเตือน
หากทุกคนได้ทำการซื้อโปรแกรมหรือเกมเพื่อไปจำลอง Windows ส่งผลให้บางโปรแกรมอาจไม่รองรับได้ ทางผมจะไม่รับผิดชอบในการกระทำเหล่านี้ ที่สำคัญอย่าสำรองข้อมูลเช่น รูปภาพ,วีดีโอ บางครั้งหากการทำงานใน Codespaces เกิดข้อผิดพลาดจะสูญเสียข้อมูลสำคัญได้ แนะนำไห้สำรองผ่าน Cloud ตลอดเพื่อความปลอดภัย เนื่องจากส่งผลทำให้กินพื้นที่ทำให้คอนเทนเนอร์เสียหาย ข้อมูล Windows ทั้งหมดจะศูนย์เปล่าทันที ดังนั้นหากใช้พื้นที่ข้อมูลควรเหลืออยู่ 3GB ขึ้นไป

# Q&A
Q:ลงโปรแกรมและเกมได้ไหม?

A:ลงได้บางโปรแกรมและเกมที่ทรัพยากรน้อย ถ้าต้องการลงเกมที่มีกราฟฟิกจริงๆ แนะนำแอป [Winlator](https://github.com/brunodev85/Winlator/releases) เป็นหนึ่งทางเลือกที่ดี แต่จะรองรับได้แค่บางอุปกรณ์ที่สเปคพอประมาณ

Q:ทำไมตอนติดตั้ง Windows ถึงไม่มีเสียง?

A:ส่วนใหญ่ถ้าลงเป็น RDP จะไม่มีไดร์เวอร์เสียงอยู่แล้ว แนะนำติดตั้ง [VB-Cable](https://vb-audio.com/Cable/index.htm) เพื่อให้ไดเวอร์เสียงทำงาน จากนั้นรีสตาร์ท เสียงที่ได้ยินส่วนใหญ่จะมาจาก Remote Desktop เท่านั้น

Q:ระยะเวลาใช้งานจำกัดไหม?

A:โดยปกติ Codespaces จะทำงานสิ้นสุดใน 4 ชั่วโมงและข้อมูลในคอนเทนเนอร์จะไม่หาย หากใช้ระยะเวลานานเกินความจำเป็นอาจจะทำให้หมดโควต้าเร็ว แนะนำวิธีประหยัดโควต้าภายใน 120 ชั่วโมง = 5 วัน ควรใช้งานวันละ 2 ชั่วโมง (หากยิ่งเร็วยิ่งประหยัดขึ้น)

Q:จะเกิดอะไรขึ้นหากโควต้าหมด?

A:Codespaces จะยังไม่สามารถเข้าใช้งานจนกว่ารอรอบบิลรีเซ็ตต่อผู้ใช้งานในเดือนถัดไป แต่ก็ระวังเรื่องการเก็บรักษา Codespaces หากไม่มีการเข้าใช้งานเป็นเวลา 30 วันจะถูกลบโดยอัตโนมัติ
