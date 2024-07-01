# RG35xxSPのstockOSでpyxelをビルドする手順

## 前提条件
- wifi接続が完了していること
- ssh接続が可能になっていること
- 下記のスクリプトをRoms/APPSに配置してAppCenterなどから実行しておく(ユーザ名はroot パスワードはroot)
```
#!/bin/sh
systemctl restart ssh
```

# 手順
## 中国語のLANGを英語に変更
```
export LANG=C
```

## パッケージのインストール
```
apt install -y zip curl libclang-dev cmake build-essential libbz2-dev libdb-dev libreadline-dev libffi-dev libgdbm-dev liblzma-dev libncursesw5-dev libsqlite3-dev libssl-dev zlib1g-dev uuid-dev tk-dev
```

## python3.8.19の配置
```
cd /tmp
wget https://github.com/game-de-it/rg35xx/releases/download/python3.8.19_pyxel2.0.11_StockOS/python3.8.19_RG35xxH700.zip
unzip python3.8.19_RG35xxH700.zip
mv python3.8.19 /mnt/mmc/python3.8.19
rm python3.8.19_RG35xxH700.zip
```

## rustのインストール
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
```

## pyxelのソースをダウンロード
```
cd /mnt/mmc/
git clone --depth=1 https://github.com/kitao/pyxel
cd /mnt/mmc/pyxel
```

## 環境変数をセット
```
source ~/.cargo/env
export PATH=/mnt/mmc/python3.8.19/bin:$PATH
```

## rustup nightlyツールチェーンをインストール
```
rustup install nightly
```

## pyxelに必要なpythonパッケージをインストール
```
/mnt/mmc/python3.8.19/bin/pip3 install -r python/requirements.txt
```

## インクルードパスの変更
```
vi rust/pyxel-platform/build.rs
## 下記に書き換える
            include_flags.push("-I/usr/include/SDL2".to_string());
            include_flags.push("-I/usr/lib/llvm-6.0/lib/clang/6.0.0/include".to_string());
```

## ビルドを実行
```
make clean build
cd dist
unzip <ビルドで生成された.whlファイル>
```

## pyxelの更新
```
rm -rf /mnt/mmc/python3.8.19/lib/python3.8/site-packages/pyxel*
rsync -av pyxel /mnt/mmc/python3.8.19/lib/python3.8/site-packages/
rsync -av pyxel-2.1.1.dist-info /mnt/mmc/python3.8.19/lib/python3.8/site-packages/
※ビルドしたpyxelのバージョンによってディレクトリ名は異なります
```

## pythonディレクトリのzip化
```
cd /mnt/mmc/
zip -r python3.8.19_pyxel-2.1.1_RG35xxH700.zip python3.8.19/
※ビルドしたpyxelのバージョンによってファイル名は異なります
```

以上
