การติดตั้ง Docker บน Ubuntu สามารถทำได้โดยทำตามขั้นตอนดังนี้:
1. อัปเดตแพ็กเกจของระบบ

เริ่มต้นด้วยการอัปเดตแพ็กเกจของ Ubuntu โดยใช้คำสั่งนี้ใน Terminal:

bash

sudo apt update

2. ติดตั้งแพ็กเกจที่จำเป็น

ติดตั้งแพ็กเกจที่จำเป็นสำหรับ Docker:

bash

sudo apt install apt-transport-https ca-certificates curl software-properties-common

3. เพิ่ม GPG key สำหรับ Docker repository

ใช้คำสั่งนี้เพื่อเพิ่ม Docker GPG key:

bash

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

4. เพิ่ม Docker repository

เพิ่ม Docker repository สำหรับ Ubuntu:

bash

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

5. อัปเดตและติดตั้ง Docker

อัปเดตแพ็กเกจและติดตั้ง Docker:

bash

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io

6. ตรวจสอบการติดตั้ง

ตรวจสอบว่า Docker ติดตั้งเรียบร้อยแล้วโดยใช้คำสั่งนี้:

bash

sudo docker --version

7. ตั้งค่าให้ Docker ทำงานโดยไม่ต้องใช้ sudo

ถ้าคุณต้องการใช้ Docker โดยไม่ต้องพิมพ์ sudo ทุกครั้ง ให้เพิ่มผู้ใช้ของคุณในกลุ่ม docker:

bash

sudo usermod -aG docker ${USER}

แล้วให้ Logout และ Login เข้ามาใหม่ หรือใช้คำสั่ง:

bash

su - ${USER}

8. ทดสอบ Docker

ลองทดสอบด้วยการรันคอนเทนเนอร์ตัวอย่าง:

bash

docker run hello-world

หากติดตั้งสำเร็จ คอนเทนเนอร์ทดสอบจะรันและแสดงข้อความยืนยันบนหน้าจอ
