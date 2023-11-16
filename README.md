# Muhammad-Fakhri_09011282126079_Pemrosesan-pararel
Tugas MPI 
# MPI-Bubblesort menggunakan Python
Tugas Pemrosesan Paralel MPI Numerik

# Sebelum Pengerjaan
### 1.Memastikan bahwa setiap PC/Laptop dalam satu jaringan yang sama 
### 2.Menentukan Server dan Slave/worker
### 3.Melakukan penginstallan net-tools untuk mengecek IP dan vim untuk teks editor

# Konfigurasi IP Server dan Slave didalam file /etc/hosts
### 1.Untuk server, buka file /etc/hosts menggunakan perintah sudo nano /etc/hosts
### 2.Didalam file /etc/hosts tambahkan IP master dan Slave/worker,kemudian save file dan keluar dari file dengan ctrl+x ![WhatsApp Image 2023-11-16 at 08 49 58_084586db](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/7f46e243-b231-4f4a-a839-d2b0f33ab841)


### 3.untuk worker/slave, sama seperti master buka file /etc/hosts kemudian masukkan cukup masukkan IP dari master dan worker pemegang file ![WhatsApp Image 2023-11-16 at 08 58 01_de917a6b](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/f66dbc8a-724e-421a-9462-bff2e77a0905)



# Membuat user baru
### 1.Untuk Server dan Worker/slave,Nama user harus sama.Untuk menambahkan User dapat digunakkan perintah sudo adduser (nama user baru)
![WhatsApp Image 2023-11-16 at 08 53 55_08999692](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/8fb6f487-de29-440b-bee9-ceaf0d05e2f5)



### 2.Kemudian berikan akses root kepada user yang telah dibuat dengan perintah sudo usermod -aG sudo (nama user baru)
### 3.Terakhir kita masuk sebagai user baru yang telah dibuat dengan perintah su – (nama user baru) ![WhatsApp Image 2023-11-16 at 08 53 55_f8a8c36d](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/79b06346-b3d7-466f-9c64-415541664595)



# Konfigurasi SSH
### 1.Pertama lakukan penginstalan ssh diserver dan slave dengan perintah sudo apt install openssh-server ![WhatsApp Image 2023-11-16 at 09 00 21_71c3425c](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/c18a3ce2-7217-4660-8a9f-4117aefea399) Kemudian lakukan pengecekan ssh dengan perintah ssh (nama user)@(host) ![WhatsApp Image 2023-11-16 at 09 05 55_8e4898b6](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/54d2e9e5-f182-4399-a955-1fa43ec16501)

### 2.Setelahnya lakukan generate keygen diserver dengan perintah ssh-keygen -t rsa ![WhatsApp Image 2023-11-16 at 09 07 43_05fff11e](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/0ff7e020-005d-4b54-88e7-438c918d549b)

### 3.Kemudian lakukan copy key publik ke client dengan perintah cd .ssh
cat id_rsa.pub | ssh <nama user>@<host> "mkdir .ssh; cat >> .ssh/authorized_keys".lakukan berkali-kali sesuai dengan jumlah dan host dari setiap slave. ![WhatsApp Image 2023-11-16 at 09 11 24_4e3f0112](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/9362173f-1fe8-42fe-a76f-451257c991fa)


# Pengkonfigurasian NFS
### 1.Didalam server dan slave buat sebuah folder dengan nama bebas,gunakan perintah mkdir.Folder setiap pc harus memiliki nama yang sama (nama folder yang ingin dibuat) ![WhatsApp Image 2023-11-16 at 09 12 40_8fe68108](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/92bf7b34-37dc-47c9-8ec9-a6a8799b277b)

### 2.lakukan penginstalan NFS server perintahnnya ialah sudo apt install nfs-kernel-server ![WhatsApp Image 2023-11-16 at 09 13 42_9ba5b558](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/c1e4da1b-8cab-48ec-bed9-46c257d38b68)

### 3.lakukan konfigurasi file /etc/exports server,dengan perintah sudo vim /etc/exports
Kemudian masukkan kalimat berikut:
<lokasi shared folder> *(rw,sync,no_root_squash,no_subtree_check)![WhatsApp Image 2023-11-16 at 09 14 21_6a7be28d](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/85ae8fb3-fd0b-4e36-98a6-ce3a1a7b5e35)

Sesuaikan lokasi shared folder dengan folder yang telah dibuat sebelumnya. Kemudian masukkan perintah sudo exportfs -a dan sudo systemctl restart nfs-kernel-server ![WhatsApp Image 2023-11-16 at 09 14 21_f8e5afb3](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/49f96ed4-6423-4403-92a6-8665cac4fc40)

### 4.kemudian install nfs pada client dengan perintah sudo apt install nfs-common ![WhatsApp Image 2023-11-16 at 09 16 12_5b6d1b12](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/fa67c12d-be8b-4660-8f4f-2aaf5b6c59e9)


### 5.Kemudian Mounting dengan perintah sudo mount <server host>:<lokasi shared folder di server> <lokasi shared folder di client> pada slave.![WhatsApp Image 2023-11-16 at 09 17 39_31fbbb76](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/eef53abd-25f5-47b4-8497-bc9fac375df7)

# MPI
### Install MPI dengan perintah sudo apt install openmpi-bin libopenmpi-dev pada server dan slave ![WhatsApp Image 2023-11-16 at 09 18 22_f63f10b2](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/2dde9d92-a8c1-4777-b83f-94bdd7ba1ca1)

# Menjalankan program bubblesort dan numerik
### 1.Lakukan penginstallan python dan mpi4py dengan perintah sudo apt install python3-pip dan pip install mpi4py ![WhatsApp Image 2023-11-16 at 09 21 34_148fc08e](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/389ffea6-b6a2-4352-91e8-ce9a535e300b)

### 2.Pertama buat 2 buah file python yang pertama bernama bubblesort.py untuk file bubblesort dan yang kedua bernama numeric.py untuk file numeric
### 3.kemudian masuk kemasing-masing file dan didalam file tersebut masukkan program sesuai dengan jenis nama file.
### Program bubblesort ![WhatsApp Image 2023-11-16 at 09 21 55_1f938f51](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/159f7b27-bfeb-4b22-88d1-bc52e501eaa3)

### Program numeric ![WhatsApp Image 2023-11-16 at 10 44 38_69fb880c](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/2b08c632-0417-421a-b6ad-28b286014244)

### 4.Jalankan file menggunakan MPI dengan perintah mpirun -np <jumlah prosesor> -host <daftar host> python3 test.py.
###  Hasil program bubblesort ![WhatsApp Image 2023-11-16 at 10 44 18_d318a7f4](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/154ba8bd-aca5-40bd-9070-7891424925ab)

### Hasil program numeric ![WhatsApp Image 2023-11-16 at 10 49 49_859b7935](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/0210a7d2-7b21-4063-bc29-6fd758daec44)
