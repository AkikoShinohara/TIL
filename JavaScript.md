## Java Script 
「ドロップダウンリスト」や画像を切り替える「スライドショー」など、ページのちょっとした動きのあるパーツなどJavaScriptで作られている(Twitter, Face Book, Instagramなどページが無限にスクロールされるものはJavaScript)

JavaScriptとは、、、プログラミング用語である
- ブラウザで実行され、ブラウザを操作することができる
- HTMLやCSS にはできないことをするために使う
- HTMLやCSS をリアルタイムで置き換えることができる
- UTF-8 文字式コード形式 JavaScriptはこの形式でないと正しく動作しない場合がある



## consoleを無理やり日本語にしてみたら


console　◯◯は　‘こんにちは’ を log ××しなさい
Console.log(‘こんにちは’);
↓
ブラウザに何かを実行させたいときには、「〇〇は××しなさい」（○◯は△△を××しなさい）とプログラムで書く
▼「◯◯は」→ オブジェクト
▼「××は」 → メソッド
▼「△△は」→ パラメーター　　　となる

———————————————————————————

**consoleは「オブジェクト」~指示を出す相手**
- window オブジェクトとは→ ウィンドウの中で操作をさせる（ex. Window.aleart(‘hello,world’);ウィンドウにアラートダイアログを表示させる）
- history オブジェクトとは→ ブラウザの履歴（訪問済みのURLの記憶）を管理しているオブジェクト プログラム側から履歴に沿って、前後に表示したページへ移動させたい場合に使用

**logは「メソッド」→ オブジェクトに対して「××しなさい」と具体的な実行内容を指示する部分**

## （）は「パラメーター」→ 指示を出す上で必要な情報
パラメーターを記述しないと「何」を指示すれば良いか分からないので、その「何」という部分がパラメーターに当たります

**’’ シングルクォートの役割**
→ ‘’ が囲まれている時は文字列として認識される
　　シングルクォートがない場合は、数式として認識される
    * 文字列に（””）ダブルクォートが含まれている場合は、全体をシングルクォートで囲まないといけない
　　JavaScriptがどこからどこまでが、本当の文字列なのかを判断することができなくなってしまうからということもある
  
- [‘use strict’] → 新しくJavaScriptを実行するモードは「スクリプトモード（Strict Mode）」と呼ばれている・実行モードをスクリプトモードにするには、プログラムの冒頭に「’’use strict」と書く
　　　　　　　　　 ブラウザは、10年20年前に書かれたマークアップ言語でも、正しく表示・実行できるように作られている・ブラウザは非常に高い互換性（コンポネート（構成要素）などを置き換えても同様に動作する）
　　　　　　　　　 を持ったアプリケーションである
                            この高い互換性を確保するためにブラウザには「古いJSを実行するモード」と「新しいJSを実行するモード」の2つ搭載されている、今回は新しいJSを実行したいため
　　　　　　　　　※ 新しい使用のES6を準拠したプログラムは、ストリクトモードでなくても動作するが、スクリプトモードにしておかないとミスを防ぐためのエラー検出機能などが一部働かないくなることもある


