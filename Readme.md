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



## Insntalasi
1. Pre-Install Docker
   ```sh
   sudo apt-get update

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
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose
    ```
   Manage docker as  non-root user
   ```sh
   sudo usermod -aG docker $USER
   ```

3. Docker Swarm

4. Portainer