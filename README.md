<h1 align="center"> Bundlr Network </h1> 

![image](https://user-images.githubusercontent.com/101149671/180648527-7bd924fc-c279-43fb-ad16-1b529eb13227.png)

<h1 align="center"> Bundlr Network Validator kurulum rehberi</h1> 

# Gereksinimler (Ekibin tavsiye ettiği, bence daha düşük sistem gereksinimleri yeterli olur):
```
8GB RAM
250 GB GB SSD
4 vCPU
```
# root yetkisi
```
sudo su
```

# root dizini
```
cd /root
```

# Sistem güncellemesi
```
sudo apt update && sudo apt upgrade -y
```

# Kütüphane kurulumu:
```
apt-get install git wget snapd curl jq libpq-dev libssl-dev build-essential pkg-config openssl ocl-icd-opencl-dev libopencl-clang-dev libgomp1 -y 2>/dev/null
```

# Docker kurulumu:
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

![image](https://user-images.githubusercontent.com/101149671/180648803-75af41e6-e6ba-4484-a0bc-ffdd037bad9a.png)

# Docker compose kurulumu:
```
curl -SL https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

![image](https://user-images.githubusercontent.com/101149671/180648840-f5d1450d-9877-4e25-a631-a445e4236855.png)

# İndiriyoruz:
```
git clone --recurse-submodules https://github.com/Bundlr-Network/validator-rust.git
```

# Şimdi Arweave'ye gidip cüzdan işlemlerimizi yapalım:

* Link: https://arweave.app/welcome
* Sol altta + butonuna tıklayalım
* Create new file diyelim. (12 kelimeyi not edin)
* Görselde ki gibi dowloand diyerek .json dosyasını kaydedelim cihazımıza.

![image](https://user-images.githubusercontent.com/101149671/180648960-2ecfe8fb-ca20-4c0f-a568-a2f4f9825d6b.png)

# Şimdi wincsp'ye geçelim.

* NOT: ilk defa node kuruyorsanız ve putty/termius gibi ssh arılığıyla kurulum yapıyorsanız winscp indirmelisiniz.
* Link: https://winscp.net/
* Veya mobaxterm ile işinizi görürsünüz, 23.07.22 günü yayınımda anlatmıştım sorulduğu için, bir flood gelecek zaten.

# Az önce indirdiğimiz .json dosyasını sunucumuzun içine atıyoruz.

* Bende ki örnek: RuyuUwqrf65Lvc9PIvwg... diye devam eden dosya.

![image](https://user-images.githubusercontent.com/101149671/180649082-af1b880a-b4f9-46f7-8409-97e6e70dcd25.png)

# Altta ki komutta ki komutun ismini yukarıda RuyuU... diye başlayan dosya adı ile tırnak içersini dolduralım ve tırnakları kaldırıp komutu girelim.
```
cp "json dosyanız" wallet.json
```

# Yukarıda bahsettiğim olayın örneği:

![image](https://user-images.githubusercontent.com/101149671/180649197-69ee7e94-85fd-401f-ab7f-e5b1f2be9fd1.png)

# 3 komutu giriyoruz:
```
cd validator-rust/
cp wallet.json ~/validator-rust
```

# Altta ki komutu girip wallet.json çıktısı alırsınız:
```
ls
```

![image](https://user-images.githubusercontent.com/101149671/180649728-9279c42c-4405-4b85-be39-dc8b1932ba65.png)

#  .env dosyası oluşturuyoruz

```
sudo tee <<EOF >/dev/null $HOME/validator-rust/.env
PORT="1984"
VALIDATOR_KEY="~/validator-rust/wallet.json"
BUNDLER_URL="https://testnet1.bundlr.network" 
GW_CONTRACT="RkinCLBlY4L5GZFv8gCFcrygTyd5Xm91CzKlR6qxhKA"  
GW_WALLET="~/validator-rust/wallet.json"
GW_ARWEAVE="https://arweave.testnet1.bundlr.network"
EOF
```

# Validator oluşturup çalıştırıyoruz
```
cd ~/validator-rust
docker-compose up -d
```

![image](https://user-images.githubusercontent.com/101149671/180649840-be5b64bb-1fd4-4473-ab28-793ddee8940c.png)

# Repository güncelliyoruz
```
git pull origin master
```
![image](https://user-images.githubusercontent.com/101149671/180649924-5ef7f039-8293-498d-9c4a-e58f8430c1d3.png)

# Validator oluşturuyoruz:
```
docker-compose build
```

![image](https://user-images.githubusercontent.com/101149671/180649940-27459414-8136-42d0-95e5-9830da3d7245.png)

# Validatorü tekrar çalıştırıyoruz
```
docker-compose up -d
```

# Node.js kurulumu
```
source ~/.bashrc
sudo apt-get install snapd
sudo snap install node --channel=16/stable --classic
```

# npm güncelleme
```
npm install -g npm@8.15.0
```

![image](https://user-images.githubusercontent.com/101149671/180650042-bcf50527-b414-4cff-8ce9-64a72d61a69f.png)







