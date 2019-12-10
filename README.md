## timewalk-with-watt
--- 編集中 / now writing ---

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
- L stick の上下左右をホールド出来る
    - HOLD_CLEAR で解除するまで続く
    - duration（時間）は0でよい
- R stick の左右をホールド出来る
    - HOLD_CAM_C で解除するまで続く
    - duration（時間）は0でよい
- UPLEFT 他は [>>325](https://medaka.5ch.net/test/read.cgi/poke/1574816324/325)
 [>>416](https://medaka.5ch.net/test/read.cgi/poke/1574816324/416)
 との互換性を保つものである
- コントローラーを認識させるのに先頭2行を捨てている
    - どうしてそうなるかは知らん
- LOOP_START は無限ループの起点
- UP 他はスティック操作のため入力が正確でない可能性がある
- フォーク元の未使用コードについては削除した
    - ただし echo については既存のコマンドを再利用することを考慮して残した
    - （duration 時間が3倍速く動くのでズレるため）
- 月末31日を1日に変更する際には時間が戻るが、次のループでリカバリするので問題ない
    - （2月についても同様）

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