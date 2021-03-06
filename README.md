py_ocr
====

画像ファイルの中にある文字を抽出します。OCRです。  
TesseractというオープンソースのOCRソフトウェアと、それをPython上で使えるようラップするライブラリ、pyocrを用いました。  

## Demo
画像ファイルを読み込み文字認識を行っています。  
文字認識を行う際に画像上の座標もともに取得し、出力場所を合わせています。  
![TestPngImg](https://github.com/zashio/py_ocr/blob/master/tesseracttest.png)

今回は手書き文字認識については行っておりません。

## Usage
### Tesseractのインストール
まずはTesseractをインストールしてください。  
ここでインストールしたTesseractを、pyocrでラップして利用します。  

[インストール方法](https://github.com/tesseract-ocr/tesseract/wiki)  
日本語版は[このあたり](https://www.kunihikokaneko.com/dblab/licenseplate/tesseract.html)が参考になるでしょう。  
  
### ソースコードのコピー
- コンソールを開き、任意の場所で以下を実行し、全てのファイルをダウンロードしてください。  
`git clone https://github.com/zashio/py_ocr.git`  
- py_ocrフォルダ内に移動し、コンソール上で以下を実行し、必要なライブラリをインストールしてください。  
`pip install -r requirements.txt`   

### .ipynbを使う場合
- 任意の環境で"image2text.ipynb"を開き、上から実行してください。  
- 引数`file_name`に文字認識を行う画像ファイルを指定してください。  
  
### .pyを使う場合
- コマンドライン上で、以下を実行してください。  
`image2text.py ***.jpg`  
- `***.jpg`の部分に、文字認識を行う画像ファイルを指定してください。  

## エラーについて(2019/2/4追記)
[このようなエラー](https://github.com/openpaperwork/pyocr/issues/99)がしばしば見受けられます。  
エラーメッセージはこのような感じです↓  
  
`pyocr.error.TesseractError: (1, b"Error, unknown command line argument '-psm'\n")`  
  
これは、tesseractをコマンドライン上から呼び出すときに、--psmと書かなければいけないところを、-psmと書いていることが原因です。  
tesseractに問題があるわけではなく、pyocr中の記述が原因です。
僕はpyocrライブラリを2019/1/29にインストールしましたが、このエラーが起こりました。  
  
解決方法としては、pyocrライブラリの、"tesseract.py"中の167行目の"-psm"を"--psm"に変更することです。  
(要するに、"--psm"がreturnされればよい)  
その他のエラーの指摘もお待ちしております。  
どうぞよしなに。

## Explain
[ソースコードに説明をつけたhtmlファイル](https://github.com/zashio/py_ocr/blob/master/image2text_note.html)があるので、ブラウザで開いて、ソースの内容理解にお使いください。

## Contribution  
お待ちしております。  
フォークして、新しいブランチを作ってそこに変更点をプッシュしておいてください。  
プルリクエストもお願いします。  

## Licence  
This source is licensed under the Apache License, Version2.0

## Author
zashio
