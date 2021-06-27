# bandoMIneDonI Build Guide

**一度すべて読んでから組み立てることをお勧めします。**

## 0 ##
## パーツの確認、各部品の実装面の整理 ###
### キット付属品

| パーツ名 |  個数  |  備考  |
|--------|-------|-------|  
|基板|2枚||
|ボトムプレート|2枚||
|M2 スペーサー |26個||
|M2 ネジ|52個||
|クッションシール|10個||
|リセットスイッチ|2個|ファームウェアを書き込むときに使います。|
|ダイオード 1N4148|77個|左手側 33鍵 + 1鍵 + 1（左右認識用）+ 右手側38鍵 + 2鍵 + 2（開閉ペダル用＋機能切り替えボタン用 )|
|TRRS コネクタ|1個|開閉ペダル接続用|
|LAN コネクタ|2個|左右キーボード接続用|


### 別途用意いただく必要のあるもの

| パーツ名 |  個数  |  備考  |
|--------|-------|--------|  
|[Pro Micro （コンスルー付き）](https://yushakobo.jp/shop/promicro-spring-pinheader/)|2個|ファームウェア なし をお選びください（別途書き込みます）。|
|Kailh mid-height スイッチ|71 〜76個|Cherry MX系は使えません！！！|
|13 mm 角のキーキャップ|71〜76個|（Cherry MXと同じステムなのですが、普通の1Uサイズのキーキャップは隣接するキーキャップと干渉してしまうため、使えません！！！）デモ機では、nekoka さんの「OYKキーキャップ1Ux80個(MidHeightスイッチ 13x13mmキーピッチ用)　https://make.dmm.com/item/1317194/」を使っています。|
|MicroUSBケーブル|1本|Pro Micro 側のコネクタの耐久性が低いためマグネット式を推奨。Pro Micro にファームウェア書き込むときにとても便利です。また、データ通信ができるケーブルである必要がありますので、充電用のケーブルは使えません。Hex ファイルが書き込みできなかったらケーブルを確認してみてください。|
|LANケーブル|1本|左右のキーボード接続用に使います。細身タイプがおすすめ。|

### [Optional]別途用意いただく必要のあるもの

| パーツ名 |  個数  |  備考  |
|--------|-------|-------|
|LED: SK6812mini-E|1個 or 76個|内訳：開閉ペダル用 1 個だけ光らせる場合、もしくは、全てのLEDを光らせる場合は上に加えて音階キー33 + 38 個+追加ボタン（左側1個＋右側2個。LEDのデータ伝送の都合上、追加ボタンを使わない場合でも実装する必要があります）+ 機能切り替えボタン 1 個|
|[ロータリーエンコーダ(ノブ付き)](https://yushakobo.jp/shop/pec12r-4222f-s0024/)|1個|[押しボタンがないタイプ](https://akizukidenshi.com/catalog/goods/search.aspx?search=x&keyword=EC12E24)の場合、ロータリーエンコーダーの下にキースイッチを付けることで、押しボタン機能部分の代用が可能です。ロータリーエンコーダーがなくても、このキースイッチを付けることでミュートON/OFF、長押しでモード切り替えが可能です。なお、実装可能なロータリーエンコーダーは EC11 EC12 の2タイプです。|
|サスティンペダル|1台|サスティンペダルを使わなかった場合を想定し、その時をOpen状態（蛇腹を広げた時の状態）にするため、デフォルトはノーマリオフタイプ（KORG）を想定しています。ソースを1行書き換えることでノーマリーオンタイプ（主にYAMAHA、ROLAND）にも対応します。 極性切り替えタイプのペダルもあるのでそちらをおすすめします。|
|3.5 mm ミニジャック変換ケーブル|1本|サスティンペダルのモノラルジャックを TRRS コネクタに刺さるように変換します。|

### オモテ面、裏面の実装物

**※ 部品の実装には順番があります。特に、Pro Micro、キースイッチ、エンコーダ、の実装は最後になりますので先に実装しないよう注意ください。
実装の順番はこの後の手順に従ってください。**

右手側 オモテ面  
<img width="700" alt="PCB" src="https://github.com/3araht/bandominedoni/blob/main/pictures/right_pcb_front_r02.jpg">

右手側 裏面  
基板の裏面には、ダイオードの実装場所やキーボード名が印字されています。  
<img width="700" alt="PCB" src="https://github.com/3araht/bandominedoni/blob/main/pictures/right_pcb_rear_r02.jpg">

左手側 オモテ面  
<img width="700" alt="PCB" src="https://github.com/3araht/bandominedoni/blob/main/pictures/left_pcb_front_r01.jpg">

左手側 裏面  
基板の裏面には、ダイオードの実装場所やキーボード名が印字されています。  
<img width="700" alt="PCB" src="https://github.com/3araht/bandominedoni/blob/main/pictures/left_pcb_rear_r01.jpg">


#### 裏面には次の部品を実装します
 - ダイオード
 - リセットスイッチ
 - Pro Micro
 - TRRS コネクタ
 - LED[Optional]

#### オモテ面には次の部品を実装します
 - キースイッチ
 - LAN コネクタ
 - エンコーダ


## 1
## ダイオードの取付け ##
キーの数が多いキーボードではMatrixという手法を使ってキーが押されたかどうか判断します。
キーが必ず1個ずつしか押されないと保証されているのであれば、このダイオードは不要なのですが、
和音を弾くことがあるので複数のキーを同時に押す場面が出てきます。
このとき、Matrixという手法で複数同時押しを正しく判断するためにこのダイオードが必要になります。
詳しい説明については、[こちら](https://docs.qmk.fm/#/how_a_matrix_works)などをご覧ください。

ダイオードには向きがあります。また、図のように足を曲げておきます。
ダイオードをつまんで両端の足を同時に曲げると図の右のように比較的ちょうどいい形になります。  
<img width="700" alt="diode" src="https://github.com/3araht/bandominedoni/blob/main/pictures/diode_bend.jpg">

キースイッチと干渉しないように、ダイオードは基板の裏面に実装します。
ダイオードの黒い線のほうが四角いフットプリント（Kと印字されている方, K はKathode（独）の頭文字らしいですが、黒（Kuro) の K で。）に合うように配置します。  
<img width="700" alt="diode" src="https://github.com/3araht/bandominedoni/blob/main/pictures/diode_align.jpg">

足を曲げて基板に這わせてダイオードを仮止めします。  
<img width="700" alt="diode" src="https://github.com/3araht/bandominedoni/blob/main/pictures/diode_flatten.jpg">

オモテ面から見た図  
<img width="700" alt="diode" src="https://github.com/3araht/bandominedoni/blob/main/pictures/diode_flatten2.jpg">

オモテ面から半田付けします(あ、ピンボケ。。。)。  
<img width="700" alt="diode" src="https://github.com/3araht/bandominedoni/blob/main/pictures/diode_soldered.jpg">

足をニッパでカットします。足は勢いよく飛んで行くので、足を押さえながら切ると良いです。  
<img width="700" alt="diode" src="https://github.com/3araht/bandominedoni/blob/main/pictures/diode_feet_cut.jpg">

これを右手側は D01 〜 D42 の42箇所、左手側は D01 〜 D35 の35箇所、半田付けします。  

~~左手側基板の D35 にもダイオードを実装します。このダイオードは、右手側基板か左手側基板かを Pro Micro が判断するのに用います。~~  
ケーブルをゆっくり接続する分にはよかったのですが、素早く抜き差しをすると、右手側基板が間違って左手側と誤認識することがしばしば発生しました。そのため、この機能を使うのはやめました。MASTER_RIGHT を定義したので、USBケーブルが刺さっている方を右手側基板と認識します。  
⇨ 左手基板の D35 は実装不要です。  
<img width="700" alt="diode" src="https://github.com/3araht/bandominedoni/blob/main/pictures/handedness.jpg">


## 2 ##
## リセットスイッチ、TRRS コネクタの取り付け ##
白い四角い枠のシルクに沿って裏側に取り付けます。浮いたり曲がった状態で実装しないようにマスキングテープなどで予め仮止めしてから半田付けするとミスが少なくなります。  

TRRS コネクタを図のように実装します。  
<img width="700" alt="TRRS" src="https://github.com/3araht/bandominedoni/blob/main/pictures/TRRS_RESETsw_soldering.jpg">  

また、ジャンパー2箇所に半田を盛って導通するようにします。  
<img width="700" alt="TRRS" src="https://github.com/3araht/bandominedoni/blob/main/pictures/right_jumper_SJ2.jpg">  
<img width="700" alt="TRRS" src="https://github.com/3araht/bandominedoni/blob/main/pictures/right_jumper_SJ3.jpg">  

右手側のリセットボタンの足が、あとで実装する LAN コネクタと干渉するため、リセットボタンの足を切ってから半田付けします。  
<img width="700" alt="ResetSW" src="https://github.com/3araht/bandominedoni/blob/main/pictures/RESETsw_soldering_right1.jpg">  
<img width="700" alt="ResetSW" src="https://github.com/3araht/bandominedoni/blob/main/pictures/RESETsw_soldering_right2.jpg">  
<img width="700" alt="ResetSW" src="https://github.com/3araht/bandominedoni/blob/main/pictures/RESETsw_soldering_right3.jpg">  


左手側基板のリセットスイッチも裏面に実装します。
<img width="700" alt="ResetSW" src="https://github.com/3araht/bandominedoni/blob/main/pictures/RESETsw_soldering_left.jpg">  


## 3 ##
## LANコネクタの取付け ##
左右の基板のオモテ面にそれぞれLANコネクタを実装します。  
<img width="700" alt="ResetSW" src="https://github.com/3araht/bandominedoni/blob/main/pictures/LAN_connector.jpg">  

## 4 ##
## Pro Micro の仮り取付け ##
**ここでは Pro Micro をコンスルー（別名 スプリングピンヘッダー ＝ Pro Micro を基板から着脱可能にするコネクタ）を使うことを前提とし、コンスルーと Pro Micro を半田付けして Pro Micro にファームウェアを書き込みます。あとで Pro Micro を取り外す必要がありますので、（おすすめしませんが）コンスルーを使われない方はキースイッチ実装したあとでProMicroを実装してください。**

※コンスルーを使う場合は Pro Micro 側のみを半田付けします。  
コンスルーの役割： 基板側を半田付けしないことにより、 Pro Micro を基板から外せるようにします。
これにより、万が一 Pro Micro の microUSB コネクタがもげても交換が容易になります。  

<img width="700" alt="CT" src="https://github.com/3araht/bandominedoni/blob/main/pictures/Con_through.jpg">

コンスルーを斜めに半田付けしないように、基板の**裏面から**コンスルーを差しておいてピンが垂直になるようにします。
下図のように、Pro Micro 側(側面に空いている小さな穴が近い方)を上にして基板にコンスルーを差し込みます。
このとき、図のように、コンスルーの向きを揃えておきます（＝2つとも側面の小さな穴が空いている方向を揃えます）。  
<img width="700" alt="CT" src="https://github.com/3araht/bandominedoni/blob/main/pictures/Con_through_onPCB.jpg">

*Pro Micro の上下の向きに注意。Pro Micro の TxD ピンが基板の TxD に刺さるように向きが合っているか確認します。  
<img width="700" alt="CT" src="https://github.com/3araht/bandominedoni/blob/main/pictures/ProMicroPinAlignment.jpg">  

コンスルーを基板の裏面から差し、TxD の位置を見て向きが揃っていることを確認したら、コンスルーと Pro Micro を半田付けします。  
**Pro Micro が浮きやすいので、Pro Micro をしっかり押さえながら最初に四隅を半田付けすると作業が楽になります。**  
**一度半田付けしたコンスルーを外すのは困難を極めますので、十分注意してください。**

コンスルーを Pro Micro に実装した様子  
<img width="700" alt="CT" src="https://github.com/3araht/bandominedoni/blob/main/pictures/ProMicro_TxD_r02.jpg">    
<img width="700" alt="CT" src="https://github.com/3araht/bandominedoni/blob/main/pictures/ProMicro_front_r02.jpg">      

### (2021/06/27 追記) ProMicro を基板に実装する際に、コネクタ部を絶縁します。

これは、コネクタ部が基板と当たり、使っているうちに擦れて基板のレジストに穴が空き、そこからショートしてしまった場合に電源が入らなくなる、という問題を回避するためです( chromatonemini で発生しました)。  
（下に紹介する写真は chromatonemini のものになります。ご了承ください。）  
<img width="700" alt="SnakeBite" src="https://github.com/3araht/bandominedoni/blob/main/pictures/SnakeBite_failure.jpg">  

このように、スネークバイトのような跡がつき、そこからProMicro のコネクタと基板の 5V がショートしてしまっていました。  
<img width="700" alt="SnakeBite" src="https://github.com/3araht/bandominedoni/blob/main/pictures/SnakeBite.jpg">  

基板にカプトンテープを貼って絶縁します。  
<img width="700" alt="SnakeBite" src="https://github.com/3araht/bandominedoni/blob/main/pictures/SnakeBiteInsulated.jpg">  

ProMicro の方にもカプトンテープを貼って絶縁します。  
<img width="700" alt="SnakeBite" src="https://github.com/3araht/bandominedoni/blob/main/pictures/ProMicroInsulated.jpg">  


## 5 ##
## Firmwareの書き込み ##
とりあえず動作確認用にファームを書き込みます。
LEDが光るHEXファイル(bandominedoni_led.hex)は[こちら](https://github.com/3araht/bandominedoni/blob/main/bandominedoni_led_hex.zip)からダウンロードできます。  

初めての方はHEXファイルの書き込みに以下のツールを使うことをお勧めします。  

普通の Pro Micro をお使いの場合は Pro Micro Web Updater  
https://sekigon-gonnoc.github.io/promicro-web-updater/index.html
※ どうやら、 Pro Micro を書き込む際に、素早くやらないと、Verify の完了まで行かないようです。  
必ず、ログを確認し、書き込みのみならず Verify まで完了していることを確認しておいてください。

Elite-C をお使いの場合は QMK Toolbox  
https://github.com/qmk/qmk_toolbox

これらの使い方は サリチル酸さんの[記事](https://salicylic-acid3.hatenablog.com/entry/qmk-toolbox)がとても参考になります(サリチル酸さん、どうもありがとうございます)。


## 6 ##
## Backlight RGB LEDの取付け[Optional] ##
以下を使うことが成功の鍵となります。  
- 温度調整機能付き半田ごてで温度を220℃〜250℃に設定する
- 融点の低い 鉛入り半田（共晶半田）を使う
- 電源ラインはランドが広く熱を奪われてしまうので、しっかり基板側を温める。
- 数珠繋ぎのLEDを順番に実装して光るか確認しながらすこしずつ進める。LED は 5V と GND の電源ラインに並列に実装するため、どれか1つが壊れているときにどこが壊れているかを特定するのが難しいです。⇨ 一気に全部 LED を実装しない。

バックライト用のチップ LED(SK6812mini-E) は PCB の裏面から実装します。向きに注意して穴に入れてください。
LED の裏から見て、切り欠きのある端子（GND）と基板のシルク（印字の事）の三角マークが同じ位置になります。
LED はデータを直列に伝送する都合上、行によって LED の向きが異なります。  
LEDの情報は直列に伝送されますので、接続が途切れてしまうと正しくLEDが光らなくなります。  
左手側の基板は、右手側からの電源供給およびデータ線の信号が無いと動作しませんので、左手側のLEDの動作確認をする場合にはLANケーブルを接続して、右手側の基板のPro Micro にUSBケーブルを接続してください。  
<img width="700" alt="RGB_LED" src="https://github.com/3araht/bandominedoni/blob/main/pictures/LED_serial.jpg">

半田付けが軌道に乗った矢先に向きを間違えがちです。
その時のショックと言ったら。。。（経験者談）。  
LED を穴にいれたら、端子の上に半田を盛って半田付けしていきます。このとき、基板とLEDの足の裏に半田を入れようと意識する必要はありません。基板のランドの方が LED の足よりもひとまわり大きいので、そこが半田付けされるイメージで実装していってください。  
<img width="700" alt="RGB_LED" src="https://github.com/3araht/bandominedoni/blob/main/pictures/LED_PIN_Layout.jpg">

半田付けしてしまうと、端子の切り欠きは見えなくなります。実装後は、オモテ面から、パッケージの切り欠きをご確認ください。  
<img width="700" alt="RGB_LED" src="https://github.com/3araht/bandominedoni/blob/main/pictures/SK6812mini-E.jpg">

温調半田ごてを使い、約220℃ 〜 250℃ で半田付けします。温度が高いとLEDが壊れますので注意してください。
温調できない半田ごてではすぐに焦げます＆壊れます（これも経験者談）。逆に、温度調節をしていれば、LEDを熱で殺すことはほとんど無いので、ご安心ください。  

右手側基板の下図の位置を半田でジャンパします。  
<img width="700" alt="Jumper" src="https://github.com/3araht/bandominedoni/blob/main/pictures/jumper_right_LED.jpg">  

左手側基板はここを半田でジャンパします。  
<img width="700" alt="Jumper" src="https://github.com/3araht/bandominedoni/blob/main/pictures/jumper_left_LED.jpg">  




## 7 ##
## 基板へのスペーサーのネジ止め ##
スペーサーを基板の裏面にネジで左右の基板それぞれ 13 箇所固定します（ネジをオモテ面に挿し、スペーサーが裏面にくるようにします）。  
キースイッチを半田付けした後にはネジを挿入することが難しい箇所があるため、キースイッチを半田付けする前に基板にネジを固定します。  
ただし、半田ごてがスペーサーに触れてしまうとスペーサーが溶けてしまうので、半田付けする際には十分ご注意ください。  

左手基板裏面  
<img width="700" alt="switch" src="https://github.com/3araht/bandominedoni/blob/main/pictures/left_pcb_rear_r01_Spacer.jpg">  

右手基板裏面  
<img width="700" alt="switch" src="https://github.com/3araht/bandominedoni/blob/main/pictures/right_pcb_rear_r02_Spacer.jpg">  


## 8 ##
## キースイッチの取付けと、エンコーダの取付け ##
**スイッチを取り付ける前に部品の取付けや半田付けができているか確認します。**  
（1 のダイオードは必ず済ませておいてください。）  

*動作確認する際には、①HEXファイル書き込み済の Pro Micro を実装し、②USBケーブルをPro Micro に挿して実施してください。**  
<img width="700" alt="switch" src="https://github.com/3araht/bandominedoni/blob/main/pictures/Keysw_test.jpg">

キースイッチをオモテ側からしっかり奥まで差し込みます。かなり固めですが、ピンが皆穴に入っていることに注意しながら押し込みます。このとき、端子が曲がっていると実装穴に端子が入らないので注意してください。1行ずつキースイッチをしっかり差し込んでから半田付けしていった方が差し込み不良は減らせると思います。  

ロータリーエンコーダーを実装します。  
<img width="700" alt="RotaryEncorder" src="https://github.com/3araht/bandominedoni/blob/main/pictures/rotary_encoder_only.jpg">

こちらは押しボタン機能の無いロータリーエンコーダー(EC12E24シリーズ)と、キースイッチを実装した場合です。
<img width="700" alt="RotaryEncorderWithoutPushButtonFuncWithKeyswitch" src="https://github.com/3araht/bandominedoni/blob/main/pictures/rotary_encorder_with_keyswitch.jpg">


## 9 ##
## Firmwareの書き込み ##
4 で書き込みが完了していなかった場合にはここでファームウェアを書き込みます。


### 9.1 ###
### コーディングはちょっと自信がない／とりあえず動作させたい、という方 ###

LEDが光るHEXファイル(bandominedoni_led.hex)は[こちら](https://github.com/3araht/bandominedoni/blob/main/bandominedoni_led_hex.zip)からダウンロードできます。  

初めての方はHEXファイルの書き込みに以下のツールを使うことをお勧めします。  

普通の Pro Micro をお使いの場合は Pro Micro Web Updater  
https://sekigon-gonnoc.github.io/promicro-web-updater/index.html
※ どうやら、 Pro Micro を書き込む際に、素早くやらないと、Verify の完了まで行かないようです。  
必ず、ログを確認し、書き込みのみならず Verify まで完了していることを確認しておいてください。

Elite-C をお使いの場合は QMK Toolbox  
https://github.com/qmk/qmk_toolbox

これらの使い方は サリチル酸さんの[記事](https://salicylic-acid3.hatenablog.com/entry/qmk-toolbox)がとても参考になります(サリチル酸さん、どうもありがとうございます)。

### 9.2 ###
### コーディングに慣れている方、チャレンジされる方 ###

以下を参考に書き込んでください。または、QMKで検索すると書き込み方がすぐに出てくるはずです。  
https://docs.qmk.fm/#/getting_started_build_tools

bandoMIneDonI の Firmware は以下にUPされるよう push request 中です(まだリンク切れ状態です)。  
https://github.com/qmk/qmk_firmware/tree/main/keyboards/bandominedoni

それまで、暫定的に[こちら](https://github.com/3araht/bandominedoni/blob/main/temp/qmk_firmware/keyboards/bandominedoni)のソースコードをお使いください。

#### 9.2.1 ####
#### 暫定的にUPしたソースの使い方 ####
1. まず、qmk_firmware を clone してきます。
https://github.com/qmk/qmk_firmware

2. qmk_firmware/util/new_keyboard.sh を使って bandoMIneDonI キーボード を新規登録します。以下のコマンドでスクリプトを実行します。  
このコマンドは qmk_firmware フォルダで実行します。  
```
./util/new_keyboard.sh
```
下図の赤い文字にしたがって進めて行きます。こうすると、正式な手続きでbandoMIneDonI キーボードのフォルダが qmk_firmware/keyboards に出来上がります。  
<img width="700" alt="new_keyboard" src="https://github.com/3araht/bandominedoni/blob/main/pictures/new_keyboard_bandominedoni.jpg">  

また、これにより、qmk_firmware フォルダで  

```
make bandominedoni:default
```

などのコンパイルも通るようになります。


3. 暫定的に UP している[こちら](https://github.com/3araht/bandominedoni/blob/main/temp/qmk_firmware/keyboards/bandominedoni)のソースコードを qmk_firmware/keyboards/bandominedoni に上書き保存します。


##### 開閉ペダルの極性がノーマリオンタイプの場合 #####
デフォルトではノーマリオフタイプのペダルを想定していますが、ノーマリオンタイプ（ヤマハやローランド製のものなど）を使用する場合、
chromatonimini.h の 以下の1行をコメントアウトしてコンパイルしてください。
これにより、ノーマリオンタイプのペダルが使えるようになります。

```
#define PEDAL_NORMALLY_CLOSED
```


#### layers ####
REMAP さまさまですが、REMAPで生成したレイヤー情報は以下の通りです。

<img width="700" alt="Layer" src="https://github.com/3araht/bandominedoni/blob/main/pictures/keymap_cheatsheet_bandominedoni.png">    


Function(FN) Layer は、エンコーダボタン長押しで遷移します。  
<img width="700" alt="Layer" src="https://github.com/3araht/bandominedoni/blob/main/pictures/20210606_bandominedoni_FN_layer.png">    


## 10 ##
## チェックポイント ##
簡単なチェック項目を挙げます。参考になれば幸いです。

【全体】
- Pro Micro はしっかり基板に刺さっている。
- Pro Micro のピンと基板のピンは一致させた状態で接続できている（Pro Micro の上下の向き確認）。
- USB ケーブルは通信可能なものを使っている（充電器の付属品などは要注意）。
- Pro Micro にファームウェアを書き込んである。
- MIDI機器に対応したソフトを起動している。
- 半田付けに問題はないか（ダイオードの向き、赤目、富士山、など）。

【Backlight RGB LED編】  
以下、チェック項目です。
- テスター（マルチメータ）をお持ちの場合は、基板からProMicro、ケーブル類を全て外した状態で、＋端子を5Vに、−端子をGND に当てて 抵抗測定してみてください。
  ~~もしも 1 MΩ以上の高抵抗値であれば正常。数十 kΩ程度かそれ以下の場合はLEDが一部破損 or LEDの向きが間違っている可能性があります。~~  
  嘘つきました。LED の 5V - GND 端子間の抵抗値が 100 kΩ 程度しか無いので、数十個の LED を並列繋ぎにしているため、抵抗値は 1 kΩ 程度しかありませんでした。  
  ⇨ 基板からProMicro、ケーブル類を全て外した状態で、テスターで 5V - GND 間の抵抗を測定して、1kΩ 未満ならどこかの LED がショート破損している可能性があります。 LED は並列接続されているので、どれが原因か特定するのが至難の技なのですが。。。
  それもあって、数珠繋ぎのLEDを順番に実装して光るか確認しながら進めることをおすすめします。

- LEDの向きが正しいか(切り欠きと三角マーク（GND）が同じ位置か確認)。
- 4つの端子が基板にしっかり半田付けできているか。数が多いので、数個半田が甘かった、ということはよくあります。
　特に、電源ラインのランドが大きくて熱を奪われるので、半田不良になりやすいです。十分ご注意ください。
- あるところから先の LED が全く光らない場合は、その境界のLEDの信号線で半田不良 or LED 破損の可能性があります。
  LED の並びについては、上記 2 Backlight RGB LEDの取付け[Optional] をご覧ください。
- あるところから先の LED の光り方が変な場合は、その境界の LED の電源線（5V か GND）の半田不良 or LED 破損の可能性があります。
- LED は光るものの、他のLEDに比べて暗い場合は、その LED が半田ごてに熱でやられている可能性があります。
- ボトムプレートをねじ止めしたら点灯していたはずのLEDが光らなくなった⇨半田不良の箇所が基板のたわみ方が変わった兼ね合いで端子が基板に接触しなくなった⇨半田ゴテで当たり直す。

また、遊舎工房さんの[サポートサイト](https://yushakobo.zendesk.com/hc/ja)が参考になると思います。併せてご覧ください。

## 11 ##
## ボトムプレートの組み立て ##
全てのキースイッチが正しく動作するのを確認したら、基板に取り付けたスペーサーにボトムプレートを固定します。
ボトムプレートの図の黄色丸の位置 13 箇所に M2 のねじでを挿入して固定します。  
ボトムプレートは、左右どちらの基板にも裏表を変えることで使用可能です。
<img width="700" alt="spacer" src="https://github.com/3araht/bandominedoni/blob/main/pictures/BottomPlate_r01_left.jpg">  
<img width="700" alt="spacer" src="https://github.com/3araht/bandominedoni/blob/main/pictures/BottomPlate_r01_right.jpg">  

ネジ止めは、たすき掛けで均一に締めつけますが、強く締めつけすぎないようにします。

左右それぞれ、黄色丸の位置 5 箇所にクッションシールを取り付けます。  
<img width="700" alt="feet" src="https://github.com/3araht/bandominedoni/blob/main/pictures/Cushion_r01_left.jpg">
<img width="700" alt="feet" src="https://github.com/3araht/bandominedoni/blob/main/pictures/Cushion_r01_right.jpg">

#### お疲れ様でした。以上で bandoMIneDonI キーボードの完成です！
