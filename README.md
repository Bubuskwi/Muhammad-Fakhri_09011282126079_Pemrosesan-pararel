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
### 2.Didalam file /etc/hosts tambahkan IP master dan Slave/worker,kemudian save file dan keluar dari file dengan ctrl+x
### ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/3db48426-0523-4c02-ab37-dae30545f8b6)
### 3.untuk worker/slave, sama seperti master buka file /etc/hosts kemudian masukkan cukup masukkan IP dari master dan worker pemegang file ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/3d18d877-aeda-41f6-97b4-6a5cbea5cdc2)

#•	Membuat user baru
### 1.Untuk Server dan Worker/slave,Nama user harus sama.Untuk menambahkan User dapat digunakkan perintah sudo adduser (nama user baru)
### 2.Kemudian berikan akses root kepada user yang telah dibuat dengan perintah sudo usermod -aG sudo (nama user baru)
### 3.Terakhir kita masuk sebagai user baru yang telah dibuat dengan perintah su – (nama user baru)

# Konfigurasi SSH
### 1.Pertama lakukan penginstalan ssh diserver dan slave dengan perintah sudo apt install openssh-server ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/023ce009-b665-4887-a59d-2dc2151cad6b)Kemudian lakukan pengecekan ssh dengan perintah ssh (nama user)@(host) ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/403b89a5-6e4d-49ce-baa9-a738b0b172ee)
### 2.Setelahnya lakukan generate keygen diserver dengan perintah ssh-keygen -t rsa ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/00d0a2c5-e6c0-4a4f-b27a-1e0763e0eb81)
### 




