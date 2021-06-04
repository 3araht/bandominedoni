<p align=center>
<img width="700" alt="bandoMIneDonI overview" src="https://github.com/3araht/bandominedoni/blob/main/pictures/bandoMIneDonI.jpg">
</p>

# bandoMIneDonI キーボード
bandoMIneDonI （バンドミネドーニ）キーボードは蛇腹の無いバンドネオンの MIDI キーボードです。  
Makiko S さんにバンドネオンのイロハを教えていただいたおかげで bandoMIneDonI が出来上がりました。感謝致します。

幅は左右のキーボードともに約 20 cm。奥行きは約 10 cm です。
左手側キーボードには、33 鍵 ＋ 1 鍵、右手側キーボードには、38 鍵 ＋ 2 鍵 あり、音階を割り当てることが可能です。
さらに、モード切り替え用に右手側に 1鍵 あります（押しボタン機能付きロータリーエンコーダーを使う場合は省略可能。別の言い方をすれば、押しボタン機能の無いロータリーエンコーダもキースイッチと組み合わせて使うことで押しボタン機能を代用可能）。
また、バンドネオンは押した時と引い時に音階の配列が変わります。それを表現するために以下の2通りの方法で切り替えが可能です。
1、 上の余剰鍵をトグルスイッチとして用いる方法
2、 サスティンペダルを流用し、開閉ペダルとして使う方法

キースイッチは Kailh Mid-height スイッチを使っています。
バンドネオンの配列を再現するために、Cherry MXのひとまわり小さいキースイッチを使っているため、Cherry MX キースイッチは使えません。
必ず Kailh Mid-Height スイッチをお使いください。

キーキャップもキースイッチ同様、かなり小さめのタイプが必要です。
バンドネオンのキーレイアウトをできるだけ忠実に再現するため、Kailh Mid-Height スイッチをかなり密に配置しています。
そのため、通常のCherry MX用の1Uキーキャップは大きすぎて使えません。nekoka さんの「OYKキーキャップ1Ux80個(MidHeightスイッチ 13x13mmキーピッチ用) https://make.dmm.com/item/1317194/ 」など、13 mm 角に収まるサイズのキーキャップが必要になります。
こちらもご注意ください。  

左右のキーボードの接続には、LANケーブルを使います。細身タイプのケーブルがお勧めです。  

ロータリーエンコーダは長押しでモード切り替えレイヤーへ。短押しでミュート切り替え、回転させるとシステム音量の調整に使用することが可能です。  

蛇腹の開閉代わりに使うサスティンペダルの接続にはミニジャックを使います。  
そのため、サスティンペダルのジャックをミニジャックに変換するアダプターが必要です。  

オプションにより、LED を搭載すれば写真のようにバックライト点灯させることが可能です（LEDのハンダ付けは難易度が高いので、ご注意ください。キースイッチが小さいため、SK6812mini-Eにのみ対応しています）。
全部で左手側に34個、右手側に 42個（上記のキースイッチの分 40個 + 機能切り替えスイッチ（ロータリーエンコーダーかキースイッチのいずれかが選択可能）とペダル用に一つずつ）、合計76個取り付け可能です。
蛇腹の閉じる／開くの状態表示を兼任しているペダル用のLED一つだけつける事も可能です。

bandoMIneDonI は PC / Mac / iPad / iPhone / Android などで動作します。  

コネクタが Lightning タイプの iPad や iPhone で使う場合、下記に示すアダプターを使って電源供給しながら使えることを確認しています。
iPad や iPhone で bandoMIneDonI を使う場合には電源が必要ですので、必ず "[Lightning - USB 3カメラアダプタ](https://www.apple.com/jp/shop/product/MK0W2AM/A/)" をお使いください。
"Lightning - USBカメラアダプタ" では電源供給ができません。

なお、USB-C タイプの iPad Air 4th Gen で試したところ、電源供給なしに問題なく動作させることができました。

なんとQWERTY配列のキーボードとしても使用可能です。実は究極のレイアウトだったりして。。。  
<p align=center>
<img width="700" alt="bandoMIneDonI overview" src="https://github.com/3araht/bandominedoni/blob/main/pictures/QWERTY_on_bandoMIneDonI.png">
</p>

# キーボードキット
bandoMIneDonI キーボードキットは BOOTH でお求めいただけます。  
[BOOTH 販売ページへのリンクはこちら](https://3araht.booth.pm/)。
BOOTH では、bandoMIneDonI の他、クロマチックボタンアコーディオンを模した MIDIキーボードの giabalanai、 giabaLEnai、giabaRInai、giabaRInaix2 やクロマトーンを模した chromatonemini のキーボードキットがお求めいただけます。

# ファームウェア

bandoMIneDonI は QMK firmware を使っています。Push request が通れば下記からダウンロードできると思います:
[QMK - bandoMIneDonI directory](https://github.com/qmk/qmk_firmware/tree/main/keyboards/bandominedoni)。

暫定的に [こちら](https://github.com/3araht/bandominedoni/blob/main/temp/qmk_firmware/keyboards/bandominedoni) からベータ版をダウンロード下さい。

もしくは、こちらのコンパイル済の [hex file](https://github.com/3araht/bandominedoni/blob/main/bandominedoni_led_hex.zip) をお使いください （RGB_MATRIX 有効）.

# ビルドガイド

[日本語ビルドガイド](https://github.com/3araht/bandominedoni/blob/main/docs/build.md)

# コンタクト先:
Twitter と YouTube はじめました。  
http://twitter.com/3araht  
https://www.youtube.com/channel/UC0zYtYMoxb0P7S8DPAkl0zA/

## その他
#### bandoMIneDonI の名前の由来  
bandoneon MIDI

bando MI ne D on I

bandoMIneDonI

MIDIをbandoneonの中に散りばめているのは、バンドネオンの無秩序な配列をオマージュしています。


# bandoMIneDonI keyboard
bandoMIneDonI keyboard is a MIDI keyboard kit of bandoneon layout, without bellows.
Thanks to Makiko S, who taught me the basics of bandoneon. bandoMIneDonI couldn't be made without her support.

The width is approx. 20 cm (= 7.9") and the depth is approx. 10 cm (= 4") for both left and right side keyboards.
There are 33 keys + 1 key on the left hand side keyboard while 38 keys + 2 keys on the right hand side keyboard.
There is one more key for switching Function layer on the right side (when a rotary encoder with push-switch is used, this key switch is unnecessary. In other words, a rotary encoder without push-switch can be used with one key switch to have the full function).
Bandoneon plays different notes on the same key when the bellows are opened or closed. In order to replicate this, there are two methods to do so:
1, by using the above additional keys to toggle the open state and close state.
2, by using a sustain pedal to input close state by pressing the pedal.

Kailh Mid-height switches are available for the keyboards.
Since it is designed to replicate the same distances between the switches with the real bandoneon, swiches smaller than Cherry MX are used.
Make sure to use Kailh Mid-height switches.

As same as keyswitches, keycaps are also tiny.
Standard 1U types are not available for the keyboards.
nekoka's 13 mm x 13 mm round keycaps are used in the demo unit.  
https://make.dmm.com/item/1317194/

LAN cable is used for wiring both left and right hand side keyboards.
Thin-type LAN cables are recommended.

A rotary encoder can be used to change the settings of bandoMIneDonI by long-pressing the push-button of the encoder, mute/unmute by clicking, and adjusting the system volume of your computer by rotating the encoder.

The sustain pedal input is mini-jack connector.
In order to plug in the pedal input, an adapter from 6.35 mm standard plug to 3.5 mm mini plug is needed.

LED (SK6812mini-E only) can be mounted on the boards as an option.
Total 76 pcs can be mounted (34 on the left hand side, 42 on the right hand side).
One LED as an indicator of the Open/Close can be mounted alone, or all 76 of them has to be mounted.

bandoMIneDonI works with PC, Mac, iPad, iPhone, and Android.

When using it with an iPad or iPhone, it works when the adapter shown below is used with a power supply. The power supply is necessary to use bandoMIneDonI on iPad and iPhone. Make sure to use "[Lightning to USB 3 Camera Adapter](https://www.apple.com/shop/product/MK0W2AM/A/)", not "Lightning to USB Camera Adapter."  

Confirmed with an iPad Air 4th Gen, which has a USB-C port, it worked without the power supply.


Surprisingly, bandoMIneDonI can be used as an QWERTY typing split-keyboard!!! Could be your end game keyboard!?!?
<p align=center>
<img width="700" alt="bandoMIneDonI overview" src="https://github.com/3araht/bandominedoni/blob/main/pictures/QWERTY_on_bandoMIneDonI.png">
</p>

# Keyboard kit
The keyboard kit is available from [BOOTH](https://3araht.booth.pm/).  
There are chromatic button accordion-ish MIDI keyboard kit giabalanai, giabaLEnai, giabaRInai, and giabaRInaix2 and chromatone MIDI keyboard kit chromatonemini as well.

Click [here](https://www.tenso.com/en/static/lp_shop_booth) for BOOTH overseas shipping!

# Firmware

bandoMIneDonI uses QMK for its firmware. The codes for it will be available here as the push request is accepted:
[QMK - bandoMIneDonI directory](https://github.com/qmk/qmk_firmware/tree/main/keyboards/bandominedoni).

Temporarily, please download codes from [here](https://github.com/3araht/bandominedoni/blob/main/temp/qmk_firmware/keyboards/bandoMIneDonI) as a "beta" version.

Or, use this pre-compiled [hex file](https://github.com/3araht/bandominedoni/blob/main/bandominedoni_led_hex.zip) for your convenience (RGB_MATRIX enabled).

# Build Guide

[Japanese Build Guide](https://github.com/3araht/bandominedoni/blob/main/docs/build.md)  
Try [Google Translated guide](https://translate.google.com/translate?sl=ja&tl=en&u=https://github.com/3araht/bandominedoni/blob/main/docs/build.md) for your language preferences. Trust me, it works quite well, more than expected.


# Contact
If you need any help, you know where to find me.  
http://twitter.com/3araht  
https://www.youtube.com/channel/UC0zYtYMoxb0P7S8DPAkl0zA/

## Miscellaneous
#### Origin of the name: bandoMIneDonI
bandoneon MIDI

bando MI ne D on I

bandoMIneDonI

Chopping "MIDI" into pieces and blending them in "bandoneon" is an homage of its chaos layout.
