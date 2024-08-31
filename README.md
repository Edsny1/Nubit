<h1 align="center"> Nubit Light Node


![nubit](https://github.com/user-attachments/assets/ed341c73-2f2c-47b0-8980-a13298b9d84b)


</h1>


 * [Nubit Website](https://alpha.nubit.org/#/)<br>
 * [Discord](https://discord.gg/nubit)<br>
 * [Twitter](https://x.com/Nubit_org)<br>



## 💻 Sistem Gereksinimleri
| Bileşenler | Minimum Gereksinimler | 
| ------------ | ------------ |
| CPU |	2|
| RAM	| 4 GB |
| Storage	| 40++ GB SSD |

```
sudo apt-get update && sudo apt-get upgrade -y 
```
```
sudo apt-get install curl screen git-all build-essential glibc-source pkg-config libssl-dev clang git-lfs -y
```
```
curl -sL1 https://nubit.sh | bash
```

Not: hersey yuklenince başlar sonra ctrl c ile durdurun.

### Eğer daha önce görevleri yaptığınız keplr cüzdanı import edicekseniz kelimeleri alın alttaki kodla  import edin. Üzerine yazılsın mı sorusuna evet diyoruz.

```
/root/nubit-node/bin/nkey add my_nubit_key --recover --p2p.network nubit-alphatestnet-1 --node.type light
```

### Servis Oluşturma

```
sudo tee /etc/systemd/system/nubitd.service > /dev/null <<EOF
[Unit]
Description=nubitd node
After=network-online.target
[Service]
User=$USER
ExecStart=/root/nubit-node/bin/nubit light start \
--p2p.network nubit-alphatestnet-1 \
--core.ip validator.nubit-alphatestnet-1.com \
--metrics.endpoint otel.nubit-alphatestnet-1.com:4318 \
--rpc.skip-auth
Restart=on-failure
RestartSec=5
LimitNOFILE=65535
[Install]
WantedBy=multi-user.target
EOF
```
### Başlatalım
```
sudo systemctl daemon-reload
sudo systemctl enable nubitd
sudo systemctl restart nubitd
```
### Log bakalım
```
sudo journalctl -u nubitd -fo cat
```

### eğer yeni girecekseniz.
Not: burda kelimeleriniz yazar. bunları keplr ekleyin sonra platforma bağlanın en başta linkler var zaten sonra görevleri yapın sizi yonlendiriyor.
```
nano /root/nubit-node/mnemonic.txt
```
### Pubkey öğrenme
NOT: cüzdan listelenecek burda pubkey kısmı var burdaki "key":"A/WJPVhPe8jYghfhgfhfgOEdfdfdbiD7ojC6thn4r1C"  2 tırnak arasında yazan kısım A/WJPVhPe8jYghfhgfhfgOEdfdfdbiD7ojC6thn4r1C kod sizin pubkey onu yazacaksınız 3k puanı kapacaksınız.
```
/root/nubit-node/bin/nkey list --p2p.network nubit-alphatestnet-1 --node.type light
```











