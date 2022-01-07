## Laporan Hasil Pratikum Modul 4  - Sistem Administrasi Server 

Nadila Chusnul K - 1202190020 \
Anastasya Rahma Juniarti - 120219058\
Kelompok 10 

## Ubuntu PHP 
1. Siapkan LXC untuk ubuntu7.4\
Clone LXC ubuntu_php7.4 menjadi ubuntu_php7.4_2 dan ubuntu_php7.4_3

    ```bash
    sudo lxc-stop -n ubuntu_php7.4
    sudo lxc-copy -n ubuntu_php7.4 -N ubuntu_php7.4_2 -sKD
    sudo lxc-copy -n ubuntu_php7.4 -N ubuntu_php7.4_3 -sKD
     ```
        ![A1](aset/G1.jpg)
        ![A1](aset/G2.jpg)

2. Start LXC
    ```bash
    sudo lxc-start -n ubuntu_php7.4
    sudo lxc-start -n ubuntu_php7.4_2
    sudo lxc-start -n ubuntu_php7.4_3
    ```
        ![A1](aset/G3.jpg)

    ### Masuk ubuntu php7.4_2 dan kemudian Configurasi IP dan nginx ubuntu_php7.4_2
    ```bash
    sudo lxc-attach -n ubuntu_php7.4_2
    nano /etc/netplan/10-lxc.yaml
    ```
        ![A1](aset/G4.jpg)

    ganti ip menjadi 10.0.3.111
        ![A1](aset/G5.jpg)

     ```bash
    netplan apply
    ip addr show eth0
    ```
    ![A1](aset/G6.jpg)

    Daftarkan domain lxc_php7_2.dev di hosts file
 
    ```bash
     nano /etc/hosts
     ```
    ![A1](aset/G8.jpg)
    Konfigurasi nginx untuk lxc_php7.4_2.dev
     ```bash
    nano /etc/nginx/sites-available/lxc_php7.dev
     ```
    ![A1](aset/G9.jpg)
    ![A1](aset/G10.jpg)

    Check configurasi nginx dan start nginx
    ```bash
     nginx -t
     service nginx restart
     curl -i http://lxc_php7_2.dev
     ```
    ![A1](aset/G11.jpg)
    ![A1](aset/G12.jpg)
    
        kemuduian exit 
    ![A1](aset/G13.jpg)

     ### Masuk ubuntu php7.4_3
    ```bash
     sudo lxc-attach -n ubuntu_php7.4_3
    ```
    ![A1](aset/G14.jpg)

    Configurasi IP dan nginx ubuntu_php7.4_3
      ```bash
     nano /etc/netplan/10-lxc.yaml
     ```
    ![A1](aset/G15.jpg)

    ganti ip menjadi 10.0.3.121
    ![A1](aset/G16.jpg)

    Konfig dan kemudain check Ip 
    ```bash
     netplan apply
    ip addr show eth0
     ```
    ![A1](aset/G17.jpg)

    Daftarkan domain lxc_php7.4_3.dev di hosts file
     ```bash
     nano /etc/hosts
     ```
    ![A1](aset/G18.jpg)
    ![A1](aset/G19.jpg)

    Konfigurasi nginx untuk lxc_php7_3.dev
     ```bash
    nano /etc/nginx/sites-available/lxc_php7.dev
     ```
    ![A1](aset/G20.jpg)
    ![A1](aset/G21.jpg)

    Configurasi nginx dan start nginx dan akses
    
     ```bash
    nginx -t
    service nginx restart
    curl -i http://lxc_php7_3.dev
    ```
    ![A1](aset/G22.jpg)
    ![A1](aset/G23.jpg)

    kemudian exit

    ### Debian PHP

    1. Siapkan LXC untuk debian_php5.6/

        Clone LXC debian_php5.6 menjadi debian_php5.6_2 dan debian_php5.6_3
    ```bash
    sudo lxc-stop -n debian_php5.6
    sudo lxc-copy -n debian_php5.6 -N debian_php5.6_2 -sKD
    sudo lxc-copy -n debian_php5.6 -N debian_php5.6_3 -sKD
     ```

    ![A1](aset/G24.jpg)
    Start LXC
    ```bash
    sudo lxc-start -n debian_php5.6
    sudo lxc-start -n debian_php5.6_2
    sudo lxc-start -n debian_php5.6_3
     ```
    ![A1](aset/G25.jpg)

    Masuk ke lxc debian_php5.6_2
    ```bash
    sudo lxc-attach -n debian_php5.6_2
     ```
    ![A1](aset/G26.jpg)
    Configurasi IP dan nginx debian_php5.6_2
      ```bash
     nano /etc/network/interfaces
     ```
     ![A1](aset/G27.jpg)

     ganti ip menjadi 10.0.3.112
    ![A1](aset/G28.jpg)

      ```bash
     service nerworking restart
     ```
    ![A1](aset/G29.jpg)

    Daftarkan domain lxc_php5_2.dev di hosts file
    ```bash
     nano /etc/hosts
     ```
   ![A1](aset/G30.jpg)
   ![A1](aset/G31.jpg)

    Konfigurasi nginx untuk lxc_php5.6_2.dev


     ```bash 
        nano /etc/nginx/sites-available/lxc_php5.dev
     ```
    ![A1](aset/G32.jpg)
    ![A1](aset/G33.jpg)

    kemudian keluar 

    ![A1](aset/G34.jpg)

    ### Masuk debian_php5.6_3
     ```bash
     sudo lxc-attach -n debian_php5.6_3
    ```
    ![A1](aset/G35.jpg)

    Configurasi IP dan nginx debian_php5.6_3
    ```bash
     nano /etc/network/interfaces
    ```
    ![A1](aset/G36.jpg)
    ganti ip menjadi 10.0.3.122
    ![A1](aset/G37.jpg)

     ```bash
     service networking restart
    ```
    ![A1](aset/G38.jpg)

    Daftarkan domain lxc_php5_3.dev di hosts file
    ```bash
    nano /etc/hosts
    ```
    ![A1](aset/G39.jpg)
    ![A1](aset/G40.jpg)

    Konfigurasi nginx untuk lxc_php5.6_3.dev
    ```bash
    nano /etc/nginx/sites-available/lxc_php5.dev
    ```
    ![A1](aset/G41.jpg)

    kemudian exit 

    ![A1](aset/G42.jpg)

    ### Masuk vm
    ![A1](aset/G43.jpg)
    ![A1](aset/G44.jpg)

    ### Load balancer menggunakan Round robin
    ![A1](aset/G45.jpg)

    Jalankan jmeter. Ganti angka pada box (number of threads) dari menu user access menjadi 50, 100, 150\
    - number of threads 50

    ![A1](aset/G46.jpg)
    ![A1](aset/G47.jpg)
    ![A1](aset/G48.jpg)

    pada step ini terdapat eror :) dengan pesan eror seperti berikut
    
    ![A1](aset/G49.jpg)
    ![A1](aset/G50.jpg)


