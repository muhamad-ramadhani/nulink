<p style="font-size:14px" align="right">
<a href="https://t.me/PemulungAirdropID" target="_blank">Join our telegram <img src="https://user-images.githubusercontent.com/72949170/194228482-0f875615-e155-4b12-8716-8111addd6cba.jpg" width="30"/></a>
</p>

<p align="center">
  <img height="400" height="auto" src="https://user-images.githubusercontent.com/72949170/194742001-b870950c-e9d3-48bf-ae0b-5a3942c7ef79.png">
</p>

# NULINK TESTNET TUTORIAL 

*Dokumen Official*
> [Testnet](https://docs.nulink.org/products/testnet)

**LESGO!!**

## 1. Jadi Root User dulu
```
sudo ufw allow 22
```
```
sudo ufw allow 9151
```
```
sudo ufw enable -y
```

## 2. Run Script

*Thanks buat NodeX Capital*
```
wget -O nulink.sh https://raw.githubusercontent.com/nodesxploit/testnet/main/nulink/nulink.sh && chmod +x nulink.sh && ./nulink.sh
```

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194742377-37ebb105-98ef-4dbf-a415-9bb2c8b5575c.png">
</p>

Disini kalian akan disuruh masukin nama + password, dan setelah itu ada KEY yang harus disimpan jgn sampe hilang

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194742483-294e09a2-97f8-49eb-a487-d9fd246760a9.png">
</p>

## 3. Restart system variable
```
source $HOME/.bash_profile
```

Setelah run command terserbut, keystore kalian akan disimpan di 
```/root/geth-linux-amd64-1.10.24-972007a5/keystore/UTC-XXXXX```

sekarang ke directory tersebut
```
cd /root/geth-linux-amd64-1.10.24-972007a5/keystore/
```

Ubah nama keystore UTC-XXXX jadi ```key```

Misal
```
mv UTC--2022-09-17T05-27-00.315775527Z--b045627fd6c57577bba32192d8XXXXXXXX key
```

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194742811-f3378f88-d939-41b8-b8d8-44103d1d5bc5.png">
</p>

## 4. Copy keystore ke directory Nulink
```
cp <keystore path> /root/nulink
```

Sekarang ke directory Nulink
```
cd /root/nulink
```

## 5. Jadikan Folder Nulink sebagai root 
```
chmod -R 777 /root/nulink
```

## 6. Set variabel
*Gak pake tanda kurung <>*
```
export NULINK_KEYSTORE_PASSWORD=<YOUR PASSWORD>
```
```
export NULINK_OPERATOR_ETH_PASSWORD=<YOUR PASSWORD>
```

## 7. Konfigurasi Docker
```
docker run -it --rm \
-p 9151:9151 \
-v /root/nulink:/code \
-v /root/nulink:/home/circleci/.local/share/nulink \
-e NULINK_KEYSTORE_PASSWORD \
nulink/nulink nulink ursula init \
--signer keystore:///code/key \
--eth-provider https://data-seed-prebsc-2-s2.binance.org:8545  \
--network horus \
--payment-provider https://data-seed-prebsc-2-s2.binance.org:8545 \
--payment-network bsc_testnet \
--operator-address <YOUR PUBLIC ADDRESS> \
--max-gas-price 100
```

*Ganti ```YOUR PUBLIC ADDRESS``` jadi address kalian yang tadi udah backup, ga pake tanda kurung <>*
<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194743231-fe1241ad-c61e-4187-abd8-7d0a3a45c11b.png">
</p>

## BACKUP PHRASE NYA, NTAR ILANG NANGIS

## 8. Run Node ny
```
docker run --restart on-failure -d \
--name ursula \
-p 9151:9151 \
-v /root/nulink:/code \
-v /root/nulink:/home/circleci/.local/share/nulink \
-e NULINK_KEYSTORE_PASSWORD \
-e NULINK_OPERATOR_ETH_PASSWORD \
nulink/nulink nulink ursula run --no-block-until-ready
```

## 9. Cek Node kalian
```
apt install screen
```
```
screen -S nulog
```
```
docker logs -f ursula
```
<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194743457-e12ad1c5-4856-4ac1-9776-d58b090973df.png">
</p>

## 10. Stake (EZ INI MAH)
- Buka https://test-staking.nulink.org/faucet
- Connect Metamask
- Ambil BSC Testnet token di https://testnet.binance.org/faucet-smart
- Ambil faucet Nulink nya
- Ke Staking Page dan Stake Nulink 
<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194743567-07242a21-7b26-4433-8d80-3388e2264c32.png">
</p>
- Scroll ke bawah, klik ```Bond Worker```

- Isi form sesuai data kalian
    
    - Worker Adress = Address kalian (yg di node)
    
    - Node Url = https://IPkalian:9151/ 
      *Contoh :*
      https://123.45.67.890:9151/
    - Klik ```Bond```
<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194743852-3742752b-bad4-4185-abda-abfe14464bc7.png">
</p>

## DONE


## JANGAN LUPA JOIN TELEGRAM
## HTTPS://T.ME/PEMULUNGAIRDROPID
