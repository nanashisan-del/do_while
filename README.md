## Automatic Angkor Watt
--- 編集中 / now writing ---

#### What we need
- マイコン本体 ATmega32u4 など [example](https://www.amazon.co.jp/dp/B07GKR9J4N/)
- micro USBケーブル [example](https://www.amazon.co.jp/dp/B0711PVX6Z/)

#### How to use
1. このレポジトリを clone download する
2. [lufa](https://github.com/abcminiuser/lufa/) を lufa フォルダに入れる
3. avr-gcc avr-dude をインストール
4. makefile 設定する
5. make コマンド
6. マイコンに書き込み （dfu-programmer など）
7. ニンテンドースイッチとマイコンを繋げる
8. Done

#### Note
- fork元にゴリ押しでDO WHILE的なものを実装
    - WHILEのdurationで指定した回数ループが実行される感じにした
    - DO WHILEのコマンド時は一旦NOTHING扱いになる(はず)ので注意

    - 入れ子には一応対応するが入れ子の最大数は"#define MAX_NEST"で定義された値以下にすること
    - デフォルトは5段まで
    - それ以上の入れ子を作った場合は知らない
    - DOとWHILEが対になってない場合も知らない
- 初期状態のマクロは意味のあるものは入ってないので注意

#### Compiling and Flashing onto the Teensy 2.0++
Go to the Teensy website and download/install the [Teensy Loader application](https://www.pjrc.com/teensy/loader.html). For Linux, follow their instructions for installing the [GCC Compiler and Tools](https://www.pjrc.com/teensy/gcc.html). For Windows, you will need the [latest AVR toolchain](http://www.atmel.com/tools/atmelavrtoolchainforwindows.aspx) from the Atmel site. See [this issue](https://github.com/LightningStalker/Splatmeme-Printer/issues/10) and [this thread](http://gbatemp.net/threads/how-to-use-shinyquagsires-splatoon-2-post-printer.479497/) on GBAtemp for more information. (Note for Mac users - the AVR MacPack is now called AVR CrossPack. If that does not work, you can try installing `avr-gcc` with `brew`.)

LUFA has been included as a git submodule, so cloning the repo like this:

```
git clone --recursive git@github.com:john-ditto/timewalk-with-watt.git
```

will put LUFA in the right directory.

Now you should be ready to rock. Open a terminal window in the `timewalk-with-watt` directory, type `make`, and hit enter to compile. If all goes well, the printout in the terminal will let you know it finished the build! Follow the directions on flashing `Joystick.hex` onto your Teensy, which can be found page where you downloaded the Teensy Loader application.

#### Thanks

Thanks [snowball-thrower](https://github.com/bertrandom/snowball-thrower)

Thanks to Shiny Quagsire for his [Splatoon post printer](https://github.com/shinyquagsire23/Switch-Fightstick) and progmem for his [original discovery](https://github.com/progmem/Switch-Fightstick).

Thanks to [exsilium](https://github.com/bertrandom/snowball-thrower/pull/1) for improving the command structure, optimizing the waiting times, and handling the failure scenarios. It can now run indefinitely!
