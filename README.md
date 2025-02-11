### Minimum sistem gereksinimleri 

| CPU  | RAM | SSD |
| ---- |:---:| ---:|
| 4+   | 6+  | 50+ | 

## Docker Kurulumu

``` 
sudo apt-get update && \
sudo apt-get install -y ca-certificates curl && \
sudo install -m 0755 -d /etc/apt/keyrings && \
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc && \
sudo chmod a+r /etc/apt/keyrings/docker.asc && \
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null && \
sudo apt-get update && \
sudo apt-get install -y docker-ce docker-ce-cli containerd.io
```

## Docker-Compose Kurulumu
```
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)
curl -L "https://github.com/docker/compose/releases/download/"$VER"/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

## Docker Kullanıcı İzinleri
```
sudo groupadd docker
```
```
sudo usermod -aG docker $USER
```

## SixGPT Kurulumu

```
git clone https://github.com/sixgpt/miner.git
cd miner
```

## Değişkenleri Ayarlıyoruz
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

## Son işlemler

```
nano docker-compose.yml
```

``sixgpt/miner:latest`` kısmını ``sixgpt/miner:3.4.0`` değiştirelim son kısım vana TEE kısmında hatalı şu anlık diğer türlü çalışmıyor

## Artık başlatmaya hazırız
Çalıştırma
```
docker-compose up -d
```
Durdurmak için
```
docker-compose down
```
Loglar için 
```
docker compose logs -f
```

Diğer çok seçenekli yöntem
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
./run_sixgpt.sh
```

bu komut sonrası 5'e basarsanız logları görürsünüz, bir kaç error verebilir llama update yaparsınız.

Vanascande ve node loglarında ödül görmüyorsanız dosyalardan root/miner/docker-compose.yml içerisinden değişiklik yapmanız gerekiyor. Discordlarını kontrol edebilirsiniz veya ara sıra buradan güncelleme geçerim.
