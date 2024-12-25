### Minimum sistem gereksinimleri 

| CPU  | RAM | SSD |
| ---- |:---:| ---:|
| 4+   | 6+  | 50+ | 

#  Docker Kurulumu

``` 
sudo apt-get update
```
``` 
sudo apt-get install ca-certificates curl
```
``` 
sudo install -m 0755 -d /etc/apt/keyrings
```
``` 
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```
``` 
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

#  Docker-Compose Kurulumu
```
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)
```
```
curl -L "https://github.com/docker/compose/releases/download/"$VER"/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```
chmod +x /usr/local/bin/docker-compose
```
```
docker-compose --version
```
# Docker Kullanıcı İzinleri
```
sudo groupadd docker
```
```
sudo usermod -aG docker $USER
```

# SixGPT Kurulumu

### Create SixGPT folder
```
mkdir
```
```
cd sixgpt
```

# Değişkenleri Ayarlıyoruz
.env dosyası da kuruyoruz

```
nano .env
```
private key kısmına burner cüzdanınızın private keyini giriyorsunuz, yapıştırma sağ tık
```
VANA_PRIVATE_KEY=privatekey
VANA_NETWORK=mainnet
OLLAMA_API_URL=http://ollama:11434/api
```

CTRL X + CTRL Y + ENTER 

# Artık başlatmaya hazırız
Önce çalıştır
```
docker-compose up -d
```
Sonra durdur
```
docker-compose down
```
Logları kontrol et
```
docker-compose logs -f
```
Her şey tamamsa artık çalıştırabilirsiniz
```
chmod +x run_sixgpt.sh
./run_sixgpt.sh
```

Buradan dil tercihi ve bir kaç güncellemeleri yapabiliyorsunuz. Sayılara basarak seçim yapabilirsiniz.

## Önemli not

Cüzdanda en az 0.1den fazla Vana olmadan çalışmayacaktır, siz yine de cüzdanda 0.3-0.4 bulundurun.

Ara sıra [vanascan](https://vanascan.io/)'a cüzdan adresinizi girip tx atıp atmadığını kontrol edin, eğer bot çalıştırmayı durdurduysa şu kodları yazarak tekrar çalıştırın
```
cd miner
```
```
chmod +x run_sixgpt.sh
./run_sixgpt.sh
```
### Loglar için

```
docker compose logs -fn 100
```