<p align="center">
<a href="https://github.com/niomictomi/uuid-for-laravel" target="_blank">
<img src="https://github.com/niomictomi/uuid-for-laravel/blob/main/file/tomslock.png" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/badge/apps-siitsa-brightgreen" alt="Apps"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>


# Installasi OpenCTI menggunnakan DOCKER
Installasi ini telah diuji pada OS Lubuntu 20


# Tahapan
1. Persiapan
2. Instalasi
3. Penggunaan

## Persiapann
Open CTI yang diinstall pada docker, membutuhkan environment sebagai berikut:
1. Docker
2. Docker Swarm
3. Docker Compose
4. Portainer



## Instalasi
1. Pre-Install Docker
   ```sh
   sudo apt-get update
   ```
   ```sh
   sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
   ```
   Add GPG 
   ```sh
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```
   Check fingerprint
   ```
   sudo apt-key fingerprint 0EBFCD88
   ```

   Add Stable Repository
   ```sh
   sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   ```
2. Install Docker dan Docker Compose
   ```sh
   sudo apt-get update
   ```
   ```
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose
    ```
   Manage docker as  non-root user
   ```sh
   sudo usermod -aG docker $USER
   ```

3. Docker Swarm
   ```
   docker swarm init --advertise-addr 192.168.99.100
   ```
   alamat IP disesuaikann dengan IP OS.
   Kemudian jalankan potongan ```code``` yang muncul pada ```terminal``` dengan format:
   ```
   docker swarm join --token <LONG-TOKEN-ID> <IP-ADDRESS-OF-MANAGER:PORT>
   ```

4. Portainer
   Install portainer untuk mempermudah dalam memanage docker via GUI.
   ```
   mkdir -p /opt/portainer && cd /opt/portainer
   ```
   ```
   curl -L https://downloads.portainer.io/portainer-agent-stack.yml -o portainer-agent-stack.yml
   ```

   Selanjutnya modifikasi pada file ```portainer-agent-stack.yml``` khususnya pada port 8000 ke 18000 dan 9000 ke 19000:
   ```
   ports:
      - "9000:9000"
      - "8000:8000"
   ```
   menjadi:
   ```
   ports:
      - "19000:9000"
      - "18000:8000"
   ```
   dan untuk membuat portainernya, jalankan:
   ```
   docker stack deploy --compose-file=portainer-agent-stack.yml portainer
   ```
   Untuk mengakses GUI Portainer, silahkan buka browser dan akses ```<alamat-IP:19000>


## INSTAL OPENCTI
1. Siapkan file docker opencti, dapat didownload melaui <a href="https://github.com/OpenCTI-Platform/docker" target="_blank">Docker OPENCTI</a>
2. Siapkan file docker-compose.yml, dapat didownload melaui <a href="https://github.com/OpenCTI-Platform/docker/blob/master/docker-compose.yml" target="_blank">Docker-Compose.yml</a>
3. Siapkan file environment ```.env``` dapat di-copas dari file ```.env.sample``` pada <a href="https://github.com/OpenCTI-Platform/docker/blob/master/.env.sample" target="_blank">ENV OPENCTI</a>.
   ```sh
    OPENCTI_ADMIN_EMAIL=admin@opencti.io
    OPENCTI_ADMIN_PASSWORD=ChangeMe
    OPENCTI_ADMIN_TOKEN=ChangeMe
    MINIO_ROOT_USER=ChangeMeAccess
    MINIO_ROOT_PASSWORD=ChangeMeKey
    RABBITMQ_DEFAULT_USER=guest
    RABBITMQ_DEFAULT_PASS=guest
    CONNECTOR_HISTORY_ID=ChangeMe
    CONNECTOR_EXPORT_FILE_STIX_ID=ChangeMe
    CONNECTOR_EXPORT_FILE_CSV_ID=ChangeMe
    CONNECTOR_EXPORT_FILE_TXT_ID=ChangeMe
    CONNECTOR_IMPORT_FILE_STIX_ID=ChangeMe
    CONNECTOR_IMPORT_DOCUMENT_ID=ChangeMe
    SMTP_HOSTNAME=ChangeMe.Mail.Com
   ```
   Untuk yang ```TOKEN``` dan ```CONNECTOR``` pastikan menggunakan standar dari <a href="https://www.uuidgenerator.net/version4">UUID V4</a>.

4. Bauat stack pada Portainer, dengan menggunakan file ```docker-compose.yml```.
   <p align="center">
    <a href="https://github.com/niomictomi/Opencti-Docker" target="_blank">
    <img src="https://github.com/niomictomi/uuid-for-laravel/blob/main/file/tomslock.png" width="400"></a></p>
5. Setting environment berdasarkan file ```.env```.
   <p align="center">
    <a href="https://github.com/niomictomi/Opencti-Docker" target="_blank">
    <img src="https://github.com/niomictomi/uuid-for-laravel/blob/main/file/tomslock.png" width="400"></a></p>
6. Selanjutnya, tinggal pencet ```Deploy the stack``` dan tungggu prosesnya bro.
7. Setelah proses selesai, buk browser dan akses ```alamat-ip:8080``` dan OPENCTI akan tampil pada halaman tersebut.
   <p align="center">
    <a href="https://github.com/niomictomi/Opencti-Docker" target="_blank">   
    <img src="https://github.com/niomictomi/uuid-for-laravel/blob/main/file/tomslock.png" width="400"></a></p>


## Penutup
Demikian sedikit informasi dari kami, tentang instalasi opencti pada Docker via Portainer.
Terimakasih.



   