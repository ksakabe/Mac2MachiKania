# Mac2MachiKania

[ケンケンのホームページ](http://www.ze.em-net.ne.jp/~kenken/index.html)で公開されている[PCのターミナルソフトからキー入力](http://www.ze.em-net.ne.jp/~kenken/machikania/typepu.html#uartkb)をUSキーボドのMacで実現するための方法を掲載しています。

# 必要なハードウェアとソフトウェア

ケンケンのホームページの[PCのターミナルソフトからキー入力](http://www.ze.em-net.ne.jp/~kenken/machikania/typepu.html#uartkb)に示されているハードウェアとソフトウェアが必要です。

- ハードウェア
  - RP2040-ZeroやRP2040-Tinyなどのマイコン
  - USB-シリアル変換ケーブル（FT-232R）
  - Mac
- ソフトウェア
  - iTerm2
  - picocom
  - 使用するマイコン用のCircuitPython
  - adafruitのライブラリ(adafruit_hid)
  - RP2040マイコンをキーボードとして機能させるプログラム（code.py）
  

# 検証した環境

- macOS Tahoe 26.5.1
- iTerm2 Build 3.7.0beta4（iTerm2のウェブサイトからダウンロード）
- picocom v3.1（homebrewでインストール）

# iTerm2の設定

ケンケンのホームページの[PCのターミナルソフトからキー入力](http://www.ze.em-net.ne.jp/~kenken/machikania/typepu.html#uartkb)で公開されているTera Term用のキー定義と同等のキー定義を実現できるソフトウェアとしてターミナルエミュレータのiTerm2を使います。通常と異なるキーコードを定義するのでMachiKaniaとの接続用のプロファイルを作成し、そのプロファイルでキー定義ファイルをインポートします。

手順は次のとおりです。

1. iTerm2のメニュー**iTerm2**を開き、**Settings...** を選択します。ショートカット **⌘,** でも開きます。
2. 表示されたウィンドウ内の**Profiles**を選択し、ウィンドウ下部の**＋**ボタンを押します。
3. カーソルがName:の右側の入力フォームに移動するのでプロファイルの名前を入力します。
4. プロファイルのメニューの**Keys**を選択し、**Key Bindings**を選択します。
5. ウィンドウ下部の**Presets**を開き、**Import**を選択し、ダウンロードしたiTerm2用のキー定義ファイル`MachiKania-Serial-iTerm2.itermkeymap`を指定して読み込みます。

# 定義したプロファイルを使用する

iTerm2のメニューの**Profiles**を開き、定義したプロファイル名を選択すると選択したプロファイルでタブが開きます。このタブでpicocomを起動してMachiKaniaと接続すれば定義したキーコードが送信されます。

# iTerm2固有のキー割り当て

Macのキーボードにない`Pause`キー（MachiKaniaではプログラムの強制終了）キーを`Ctrl`+`Option`+`Delete`キーに割り当てました。

BS（BackSpace）キーもMacのキーボードにありませんが`Ctrl`+`H`でカーソールの左側の文字を削除できます。このキー操作はmacOSで定義されたものです。

| キー  | Macのキーボードでの割り当て |
|:-----:|-----------------------------|
| Pause | Ctrl+Option+Delete          |
|  BS   | Ctrl+H                      |


