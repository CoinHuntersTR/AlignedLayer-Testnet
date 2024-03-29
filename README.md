# AlignedLayer-Testnet

# Kurulum

## Go Setup
```
sudo apt -q update
sudo apt -qy install curl git jq lz4 build-essential
sudo apt -qy upgrade
```
```
wget https://raw.githubusercontent.com/CoinHuntersTR/AlignedLayer-Testnet/main/go.sh && chmod +x go.sh && ./go.sh -v 1.22.0 && rm -rf go.sh
```

```
. /etc/profile && . $HOME/.bashrc
```
## Run Node setup

```
wget https://raw.githubusercontent.com/Staketab/cosmos-tools/main/node-installer/install.sh
chmod +x install.sh
./install.sh -g yetanotherco -f aligned_layer_tendermint -b alignedlayerd -c .alignedlayer -v v0.1.0
rm -rf install.sh && . $HOME/.profile
```

> Burada 2 seçeneğini seçip enter basıyoruz.


![Ekran görüntüsü 2024-03-26 233346](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/365e6a1a-f9f1-4bca-9f8d-0c590f6925c1)

## Data for start the chain

> Binary: İstediği linki aşağıdaki komut satırından kopyalayıp devam ediyoruz.

```
https://services.staketab.org/aligned-testnet/alignedlayerd
```

![Ekran görüntüsü 2024-03-26 233601](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/85898d22-2165-41d4-853f-9099a8023172)

> Buraya bir değer girmenize gerek yok. Enter yapıp geçebilirsiniz.

> Chain-id Aşağıdaki komutu girebilirsiniz.

![Ekran görüntüsü 2024-03-26 233653](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/9202bf88-ca76-43fa-9f46-2a7ed1d6aef0)

```
alignedlayer
```

> MONIKER Node için istediğiniz bir ismi veriyoruz.

![Ekran görüntüsü 2024-03-26 233736](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/faf82127-8964-426e-af8f-34e215c8f89c)
 

> Genesis file

![Ekran görüntüsü 2024-03-26 233839](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/5fe75545-8cac-4b99-add8-2ac7a8af2ec9) 

```
https://services.staketab.org/aligned-testnet/genesis.json
```

> Peers


```
a1a98d9caf27c3363fab07a8e57ee0927d8c7eec@128.140.3.188:26656,1beca410dba8907a61552554b242b4200788201c@91.107.239.79:26656,f9000461b5f535f0c13a543898cc7ac1cd10f945@88.99.174.203:26656,ca2f644f3f47521ff8245f7a5183e9bbb762c09d@116.203.81.174:26656
```

> Peers Aşağıdaki Peer'ları komut satırına giriyoruz.

![Ekran görüntüsü 2024-03-26 233919](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/d064ddc2-0e3c-4974-877a-6d5b3f7a889c)

```
a1a98d9caf27c3363fab07a8e57ee0927d8c7eec@128.140.3.188:26656,1beca410dba8907a61552554b242b4200788201c@91.107.239.79:26656,f9000461b5f535f0c13a543898cc7ac1cd10f945@88.99.174.203:26656,ca2f644f3f47521ff8245f7a5183e9bbb762c09d@116.203.81.174:26656
```

> Seed istediğinde alttaki komutu giriyoruz.

```
None
```

> minimum-gas-prices 

```
0stake
```
>  1 - If you want to configure STATESYNC. 2 - If you don't want to configure STATESYNC. seçeneklerinden 2 seçip devam ediyoruz.

![Ekran görüntüsü 2024-03-26 234056](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/27debbb2-4997-4c4e-ae07-899ce553aebd)

> Don't install Cosmosvisor seçeneği içi 2 ye basıp devam ediyoruz.

![Ekran görüntüsü 2024-03-26 234153](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/458b256f-7178-4919-837c-03f8bcc32265)

## Start Node

```
sudo systemctl enable alignedlayerd.service
```
```
sudo systemctl start alignedlayerd.service
```
```
sudo journalctl -u alignedlayerd.service -f
```



> Exit code hatası alırsanız. Aşağıdaki komutları kullanabilirsiniz.

![Ekran görüntüsü 2024-03-26 234347](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/f6541038-beee-4e0c-9dc6-c60e560594ec)


```
SEEDS=
PEERS=a1a98d9caf27c3363fab07a8e57ee0927d8c7eec@128.140.3.188:26656,1beca410dba8907a61552554b242b4200788201c@91.107.239.79:26656,f9000461b5f535f0c13a543898cc7ac1cd10f945@88.99.174.203:26656,ca2f644f3f47521ff8245f7a5183e9bbb762c09d@116.203.81.174:26656
STAKETAB_PEER=dc2011a64fc5f888a3e575f84ecb680194307b56@148.251.235.130:20656
sed -i -e 's|^persistent_peers *=.*|persistent_peers = "'$STAKETAB_PEER','$PEERS'"|' $HOME/.alignedlayer/config/config.toml
sed -i -e 's|^seeds *=.*|seeds = "'$SEEDS'"|' $HOME/.alignedlayer/config/config.toml
```

```
sudo systemctl restart alignedlayerd.service
```
```
sudo journalctl -u alignedlayerd.service -f
```
## Aşağıdakine benzer çıktı alıyorsanız. İşlem tamamdır.
![Ekran görüntüsü 2024-03-26 234452](https://github.com/CoinHuntersTR/AlignedLayer-Testnet/assets/111747226/4d6e505f-697a-420a-acb3-02b22dd82fa8)

# Validator Oluşturma

> Öncelikle ağ ile senkronize olmanız gerekiyor. Yani Node'daki blok sayınız ile Ağdaki blok sayınız aynı olana kadar bekleyin.

> Exlporerdan kontrol edebilirsiniz. [BURADAN](https://testnet.alignedlayer.explorers.guru/) explorer ulaşabilirsiniz.

## Cüzdan Oluşturma

> wallet yerine bir isim verin. Sonrasında sizden şifre isteyecek, istediğiniz bir şifre oluşturun. (Sonraki işlemlerde işinize yarayacağı için unutmayın)

```
alignedlayerd keys add wallet
```

## Faucet

> Cüzdanınızı oluşturduktan sonra [BURADAN](https://faucet.alignedlayer.com/) faucete gidip cüzdanınıza token talep edin.

> PubKeyimizi öğreniyoruz.

>  `{"@type":"/cosmos.crypto.ed25519.PubKey","key":"keynumbersss"}` buna benzer bir çıktı alıyoruz.

```
alignedlayerd tendermint show-validator --home /root/.alignedlayer
```

```
cd $HOME
```
```
nano validator.json
```

> Aşağıdaki komutu kendinize göre düzenlemeniz gerekiyor.

```
{
"pubkey": {"@type":"/cosmos.crypto.ed25519.PubKey","key":"keynumbersss"}, 
"amount": "1000000stake",
"moniker": "MONIKER",
"identity": "KEY ID",
"website": "",
"security": "",
"details": "",
"commission-rate": "0.1",
"commission-max-rate": "0.2",
"commission-max-change-rate": "0.01",
"min-self-delegation": "1"
}
```

> Bunları düzenledikten sonra terminale kopyalayıp ekliyoruz. Sonrasında CTRL X Y enter ile çıkıyoruz.

> Sonrasında aşağıdaki komutu çalıştırıyoruz.


```
sudo systemctl restart alignedlayerd.service
```

> wallet yerine kendi cüzdan adınızı girmeyi unutmayın.

```
alignedlayerd --home /root/.alignedlayer tx staking create-validator $HOME/validator.json --from wallet  --chain-id alignedlayer --fees 5000stake -y
```
