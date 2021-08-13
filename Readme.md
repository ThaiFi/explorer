# Deploy blockscout

## 1. Download blockscout
> https://github.com/blockscout/blockscout/releases
```
# curl -L -o blockscout-3.7.0-beta.zip https://codeload.github.com/blockscout/blockscout/zip/refs/tags/v3.7.0-beta
# unzip blockscout-3.7.0-beta.zip
# cp logo.png blockscout-3.7.0-beta/apps/block_scout_web/assets/static/images/.
```

## 2. Build blockscout
```
# cd blockscout-3.7.0-beta/docker
# docker build --build-arg COIN="XTH" -f ./Dockerfile -t blockscout_tbwg ../
```

## 3. Start PostgreSQL
> change password for postgres

```
# docker-compose up -d postgres
```

## 4. Migrations blockscout
Change environment 
- DATABASE_URL=postgresql
- NETWORK=TBWG
- SUBNETWORK=TBWG
- ETHEREUM_JSONRPC_HTTP_URL=https://rpc.tbwg.io
- ETHEREUM_JSONRPC_WS_URL=ws://ws.tbwg.io
- COIN=TFI
- COINGECKO_COIN_ID=dai
- LOGO=/images/TBWG-01.png
- LOGO_FOOTER=/images/TBWG-01.png

```
# docker-compose up migrations
```

## 5. Start blockscout
Change environment                             
- DATABASE_URL=postgresql                      
- NETWORK=X-Chain                                 
- SUBNETWORK=XTH                              
- ETHEREUM_JSONRPC_HTTP_URL=https://rpc.tbwg.io
- ETHEREUM_JSONRPC_WS_URL=ws://ws.tbwg.io      
- COIN=XTH                                                            
- LOGO=/images/logo-xth-02.png                     
- LOGO_FOOTER=/images/logo-xth-02-removebg-preview.png              

```
# docker-compose up -d blockscout
```

## 6. Change Coin name
```
# vim apps/block_scout_web/priv/gettext/en/LC_MESSAGES/default.po
msgid "ETH"
msgstr "XTH"

msgid "Ether"
msgstr "XTH" 
```

## 7. Change Theme
```
# vim apps/block_scout_web/assets/css/theme/_variables.scss
@import "base_variables";
// @import "neutral_variables";
@import "poa_variables";
```

## 8. Description
```
เขียนว่า: X-Chain
อ่านว่า: Cross Chain
ชื่อตัวย่อของ Chain:  XTH (Cross Chain Thailand)
Native Token:  XTH
```
