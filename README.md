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
### 2.Didalam file /etc/hosts tambahkan IP master dan Slave/worker,kemudian save file dan keluar dari file dengan ctrl+x ![WhatsApp Image 2023-11-16 at 19 14 06_41ac349f](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/d22ba468-a8a9-4a56-a891-992da5e80d9e)

### 3.untuk worker/slave, sama seperti master buka file /etc/hosts kemudian masukkan cukup masukkan IP dari master dan worker pemegang file ![WhatsApp Image 2023-11-16 at 08 58 01_f7b157f8](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/62835e01-5af3-462d-ab41-3d307aea15c9)



#•	Membuat user baru
### 1.Untuk Server dan Worker/slave,Nama user harus sama.Untuk menambahkan User dapat digunakkan perintah sudo adduser (nama user baru)
![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/ebd273d6-303d-431f-9a93-87f361dbd795)

### 2.Kemudian berikan akses root kepada user yang telah dibuat dengan perintah sudo usermod -aG sudo (nama user baru)
### 3.Terakhir kita masuk sebagai user baru yang telah dibuat dengan perintah su – (nama user baru)
![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/21f23ff5-8530-4588-93dc-99aba2ec6f85)


# Konfigurasi SSH
### 1.Pertama lakukan penginstalan ssh diserver dan slave dengan perintah sudo apt install openssh-server ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/023ce009-b665-4887-a59d-2dc2151cad6b)Kemudian lakukan pengecekan ssh dengan perintah ssh (nama user)@(host) ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/403b89a5-6e4d-49ce-baa9-a738b0b172ee)
### 2.Setelahnya lakukan generate keygen diserver dengan perintah ssh-keygen -t rsa ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/00d0a2c5-e6c0-4a4f-b27a-1e0763e0eb81)
### 3.Kemudian lakukan copy key publik ke client dengan perintah cd .ssh
cat id_rsa.pub | ssh <nama user>@<host> "mkdir .ssh; cat >> .ssh/authorized_keys".lakukan berkali-kali sesuai dengan jumlah dan host dari setiap slave.![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/593b01ac-007b-4651-af10-8673747d8c5b)

# Pengkonfigurasian NFS
### 1.Didalam server dan slave buat sebuah folder dengan nama bebas,gunakan perintah mkdir.Folder setiap pc harus memiliki nama yang sama (nama folder yang ingin dibuat) 
### 2.lakukan penginstalan NFS server perintahnnya ialah sudo apt install nfs-kernel-server
### 3.lakukan konfigurasi file /etc/exports server,dengan perintah sudo vim /etc/exports
Kemudian masukkan kalimat berikut:
<lokasi shared folder> *(rw,sync,no_root_squash,no_subtree_check)
Sesuaikan lokasi shared folder dengan folder yang telah dibuat sebelumnya.
![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/9b8f2bdf-b3c1-403b-b35c-d0f185088487) Kemudian masukkan perintah sudo exportfs -a dan sudo systemctl restart nfs-kernel-server ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/0e251775-cd67-4ac2-a27a-d3c0d0744c92)
### 4.kemudian install nfs pada client dengan perintah sudo apt install nfs-common ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/bedfed23-0a52-4e4d-a5c3-0004cff5de96)
### 5.Kemudian Mounting dengan perintah sudo mount <server host>:<lokasi shared folder di server> <lokasi shared folder di client> pada slave.![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/327c7109-ed4a-442e-bd74-0cd4873bc526)
# MPI
### Install MPI dengan perintah sudo apt install openmpi-bin libopenmpi-dev pada server dan slave ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/5103c56a-0b27-4ce9-9f87-227f40f52b51)
# Menjalankan program bubblesort dan numerik
### 1.Lakukan penginstallan python dan mpi4py dengan perintah sudo apt install python3-pip dan pip install mpi4py ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/c1b41722-4f4c-40a2-94d6-11f790e1b4b8)
### 2.Pertama buat 2 buah file python yang pertama bernama bubblesort.py untuk file bubblesort dan yang kedua bernama numeric.py untuk file numeric
### 3.kemudian masuk kemasing-masing file dan didalam file tersebut masukkan program sesuai dengan jenis nama file.
### Program bubblesort ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/e0affe47-af16-4471-9d21-135df34eae1a)
### Program numeric ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/913b93c6-4135-4797-8b18-a58ebc4e7791)
### 4.Jalankan file menggunakan MPI dengan perintah mpirun -np <jumlah prosesor> -host <daftar host> python3 test.py.
###  Hasil program bubblesort ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/647f3f1e-0a37-4dc9-a050-1c1b5d49cee9)
### Hasil program numeric ![image](https://github.com/Bubuskwi/Muhammad-Fakhri_09011282126079_Pemrosesan-pararel/assets/150929648/3d03d1ce-a24e-42e0-b736-44b85a995913)
