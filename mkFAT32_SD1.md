# RG35xx StockOSのSD1側にFAT32パーティションを作成する(RG35xx Create a FAT32 partition on the SD1 side of StockOS)

## 使い方
1. リリースページから「mkFAT32_SD1.sh」ファイルをダウンロードする
2. StckOSのSDカード内の「Roms/APPS」ディレクトリに「mkFAT32_SD1.sh」ファイルをコピーする
3. SDカードをRG35xxに接続して電源をONにする
4. 「RA Game」 → 「APPS」 → 「mkFAT32_SD1」を実行する
5. RG35xxの電源をOFFにする
6. SDカードをパソコンに接続してパーティションミニツールを実行します  
無料版のDLリンク [https://jp.minitool.com/partition-manager/partition-wizard-home.html](https://jp.minitool.com/partition-manager/partition-wizard-home.html)   
7. パーティションミニツールを起動させてTFカードの項目を探します(画像は例です)  
  <img src="https://github.com/game-de-it/testrepo/blob/main/asset/SC03.png" width="500">    
8. 「(FAT32)338MB」と書かれている領域を右クリックして「移動/サイズ変更」をクリックします  
  <img src="https://github.com/game-de-it/testrepo/blob/main/asset/SC02.png" width="500">  
9. パーティションのスライダーを右端まで引っ張り、「OK」ボタンをクリックします
  <img src="https://github.com/game-de-it/testrepo/blob/main/asset/SC01.png" width="500">  
10. パーティションサイズに問題がなければ「適用」ボタンをクリックします
  <img src="https://github.com/game-de-it/testrepo/blob/main/asset/SC04.png" width="500">   

以上  

---

## How to use
1. Download the "mkFAT32_SD1.sh" file from the release page
2. Copy the "mkFAT32_SD1.sh" file to the "Roms/APPS" directory in the StckOS SD card.
3. Connect the SD card to RG35xx and turn on the power
4. Run “RA Game” → “APPS” → “mkFAT32_SD1”
5. Turn off the power of RG35xx
6. Connect SD card to computer and run Partition Mini Tool  
Free version DL link [https://jp.minitool.com/partition-manager/partition-wizard-home.html](https://jp.minitool.com/partition-manager/partition-wizard-home.html )
7. Launch the partition mini tool and search for the TF card item (the image is an example)
   <img src="https://github.com/game-de-it/testrepo/blob/main/asset/SC03.png" width="500">
8. Right-click the area that says "(FAT32)338MB" and click "Move/Resize"
   <img src="https://github.com/game-de-it/testrepo/blob/main/asset/SC02.png" width="500">
9. Pull the partition slider all the way to the right and click the "OK" button
   <img src="https://github.com/game-de-it/testrepo/blob/main/asset/SC01.png" width="500">
10. If there is no problem with the partition size, click the "Apply" button
   <img src="https://github.com/game-de-it/testrepo/blob/main/asset/SC04.png" width="500">

that's all
