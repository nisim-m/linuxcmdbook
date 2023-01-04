
[Linux+コマンド入門 サポートページ](https://nisim-m.github.io/linuxcmdbook/) ～学習用環境（VirtualBox + Ubuntu）～
# VirtualBox + Ubuntu

<!-- TOC -->

1. [ファイルのダウンロード](#ファイルのダウンロード)
    1. [VirtualBox](#virtualbox)
    2. [UbunutuのISOイメージ](#ubunutuのisoイメージ)
2. [VirtualBoxのインストール](#virtualboxのインストール)
    1. [<a name="extpack">拡張パック</a>のインストール](#a-nameextpack拡張パックaのインストール)
2. [仮想マシンの作成（Ubuntu/CentOS共通）](#仮想マシンの作成ubuntucentos共通)
    1. [名前とオペレーションシステムの選択](#名前とオペレーションシステムの選択)
    2. [メモリーサイズの入力](#メモリーサイズの入力)
    3. [ハードディスクの入力](#ハードディスクの入力)
    4. [<a name="portforwarding">ホストOSから接続するための設定（任意）</a>](#a-nameportforwardingホストosから接続するための設定任意a)
    5. [USBの設定（任意）](#usbの設定任意)
2. [<a name="ubuntuinstall">ゲストOS（Ubuntu）のインストール</a>](#a-nameubuntuinstallゲストosubuntuのインストールa)
    1. [言語の選択](#言語の選択)
    2. [インストール用の設定](#インストール用の設定)
    3. [再起動](#再起動)
    4. [再起動後の設定](#再起動後の設定)
    5. [追加のインストールと更新](#追加のインストールと更新)
    6. [更新後の再起動](#更新後の再起動)
2. [Guest Additionsのインストール](#guest-additionsのインストール)
3. [Ubuntuの設定](#ubuntuの設定)
    1. [画面の解像度変更](#画面の解像度変更)
    2. [クリップボードの共有](#クリップボードの共有)
2. [スナップショットの活用](#スナップショットの活用)
    1. [スナップショットの作成](#スナップショットの作成)
    2. [スナップショットの復元](#スナップショットの復元)

<!-- /TOC -->

## ファイルのダウンロード

### VirtualBox
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
**VirtualBox xx.xx.xx platform packages**にOS別のダウンロードリンクがあるので、
VistualBoxをインストールするOS（ホストOS）に合ったインストーラーをダウンロードしてください。

- Windows … Windows hosts
- macOS … OS X hosts
- Linux … Linux distributions

※ここでは、Windows版を使用。

### UbunutuのISOイメージ

インストール用のイメージファイルは下記のURLからダウンロードできます。

[https://jp.ubuntu.com/download](https://jp.ubuntu.com/download) 

※ここでは、Ubuntu Desktop 20.04.2.0 LTS（`ubuntu-20.04.2.0-desktop-amd64.iso`）を使用。

## VirtualBoxのインストール

VirtualBoxのインストーラーを実行し、画面に従ってインストールを行ってください。

<small>*※<a href="images\2023-01-02-17-16-54.png">“Oracle VM VirtualBox 7.x.x needs the Microsoft Visual C++ 2019 Redistributable Packaging being installed first.”のようなメッセージ</a>が表示された場合、Microsoftのサイトからダウンロードしてインストールしてください。（<a href="https://visualstudio.microsoft.com/ja/downloads/">https://visualstudio.microsoft.com/ja/downloads/</a> “Microsoft Visual C++ Redistributable for Visual Studio 2022” [画面例](install-vcpp.md)）*</small>

<div class="imgtitle"></div>
<a href="images\2021-04-11-23-29-45.png"><img src="images\2021-04-11-23-29-45.png" width="250"/></a>
<div class="imgtitle"></div>
<a href="images\2021-04-11-23-30-16.png"><img src="images\2021-04-11-23-30-16.png" width="250"/></a>
<div class="imgtitle"></div>
<a href="images\2021-04-11-23-30-58.png"><img src="images\2021-04-11-23-30-58.png" width="250"/></a>
<div class="imgtitle"></div>
<a href="images\2021-04-11-23-31-30.png"><img src="images\2021-04-11-23-31-30.png" width="250"/></a>
<div class="imgtitle"></div>
<a href="images\2021-04-11-23-31-55.png"><img src="images\2021-04-11-23-31-55.png" width="250"/></a>

### <a name="extpack">拡張パック</a>のインストール

<small>*※VirtualBox バージョン7.0（2022年10月リリース）以降、USB 3.xアクセス用に拡張パックをインストールする必要がなくなりました。*</small>

仮想マシンで外部ストレージへの接続が必要になることはあまりありませんが、外部メディアへのアクセスを試してみたい場合にUSBメモリー等を接続して使用することがあります。
この場合、ホストOSのUSBポートに外部メディアを接続してゲストOSから使用することになりますが、USB 3.x の利用には拡張パックが必要です。

**VirtualBox xx.xx.xx Oracle VM VirtualBox Extension Pack**のダウンロードリンク（All supported platforms）で拡張パック（Oracle_VM_VirtualBox_Extension_Pack-xx.xx.xx.vbox-extpack）をダウンロードしてください。

Windows環境の場合、ダブルクリックで追加できます。メニューから追加する場合、VirtualBoxを起動し、`ファイル(F)`メニューの`環境設定(P)`にある`拡張機能`で拡張パックを追加します。

<div class="imgtitle">環境設定</div>
<a href="images\2021-04-11-23-48-57.png"><img src="images\2021-04-11-23-48-57.png" width="300"/></a>
<div class="imgtitle">インストールの確認メッセージ</div>
<a href="images\2021-04-11-23-49-23.png"><img src="images\2021-04-11-23-49-23.png" width="300"/></a>

（VirtualBoxライセンスの確認メッセージが表示されるのでメッセージを最後まで表示して［同意します］をクリック）

<div class="imgtitle">ライセンスの確認メッセージ</div>
<a href="images\2021-04-12-00-20-31.png"><img src="images\2021-04-12-00-20-31.png" width="300"/></a>

## 仮想マシンの作成（Ubuntu/CentOS共通）

VirtualBoxを実行し、`仮想マシン(M)`→`新規(N)`で仮想マシンを作成します（作成および設定後、仮想マシンにゲストOSをインストールします）。

### 名前とオペレーションシステムの選択

- 名前 … 任意
- マシンフォルダー … 仮想マシンを保存する場所（任意）
- タイプ … Linux
- バージョン … Ubuntu (64-bit) 

※仮想マシンに`Ubuntu`を含んだ名前を付けると、タイプとバージョンが自動で設定される。

<div class="imgtitle">Ubuntuの例</div>
<a href="images\2021-04-11-23-54-20.png"><img src="images\2021-04-11-23-54-20.png" width="250"/></a>

<small>*※VirtualBox 7.0では自動インストールが可能になっていますが本ページでは6.1.xでの手動インストールで解説しています（[画面例](using_vbox7.md)）。*</small>

###  メモリーサイズの入力

ゲストOSに割り当てるメモリーのサイズを入力します。たくさん割り当てることでゲストOSが快適に動作するようになりますが、その分、ホストOSの動作が犠牲になります。  
本書のサンプルを実行する場合、1024～2048MB程度で問題ありません。

<div class="imgtitle">メモリーサイズ</div>
<a href="images\2021-04-12-00-00-16.png"><img src="images\2021-04-12-00-00-16.png" width="250"/></a>

###  ハードディスクの入力

1. `仮想ハードディスクを作成する(C)`（デフォルト）を選んで`作成`をクリック
1. `VDI(VirtualBox Disk Image)`（デフォルト）を選んで`次へ(N)`をクリック
1. `可変サイズ(D)`（デフォルト）を選んで`次へ(N)`をクリック
1. サイズを入力して`作成`をクリック
本書のサンプル程度であれば、デフォルトの10GBで十分実行できますが、他の操作なども試してみたい場合はもう少し大きくしておく方が扱いやすいでしょう。なお、「可変サイズ」を選択している場合、ホストOSのディスクを消費するのはゲストOSで実際に使用した分のみです。

<div class="imgtitle">ハードディスク</div>
<a href="images\2021-04-12-00-04-27.png"><img src="images\2021-04-12-00-04-27.png" width="250"/></a>
<div class="imgtitle">ハードディスクのタイプ</div>
<a href="images\2021-04-12-00-04-37.png"><img src="images\2021-04-12-00-04-37.png" width="250"/></a>
<div class="imgtitle">物理ハードディスクにあるストレージ</div>
<a href="images\2021-04-12-00-05-28.png"><img src="images\2021-04-12-00-05-28.png" width="250"/></a>
<div class="imgtitle">ファイルの場所とサイズ</div>
<a href="images\2021-04-12-00-06-45.png"><img src="images\2021-04-12-00-06-45.png" width="250"/></a>

###  <a name="portforwarding">ホストOSから接続するための設定（任意）</a>

ホストOSからゲストOSのWebサーバーやSSHサーバーに接続してみたい場合は、下記を設定しておきます。
ゲストOS（Ubuntu/CentOS）をインストールした後で設定することも可能です。

ネットワーク：NAT（デフォルト）  
ネットワークアダプターを有効化にチェックマーク（デフォルト）  

`高度`→`ポートフォワーディング(P)`で以下を設定
- Webブラウザ用（http）… ホストポート 50080、ゲストポート 80
- コマンドライン用（ssh）… ホストポート 50022、ゲストポート 22

※ホストポートの番号はに任意（1024から49451の範囲で指定）。
※名前は任意、プロトコルはTCP、ホストIPとゲストIPは空欄。
※複数のゲストOSをインストールしてみたい場合は、ゲストOS毎に異なるポート番号を設定する。

<div class="imgtitle">ゲストOSの設定</div>
<a href="images\2021-04-12-00-25-55.png"><img src="images\2021-04-12-00-25-55.png" height="250"/></a>
<div class="imgtitle">ネットワーク</div>
<a href="images\2021-04-12-00-34-33.png"><img src="images\2021-04-12-00-34-33.png" height="250"/></a>
<div class="imgtitle">ポートフォワーディング</div>
<a href="images\2021-04-12-00-33-26.png"><img src="images\2021-04-12-00-33-26.png" height="250"/></a>

※ゲストOS同士の通信をしたい場合は、「ブリッジ」または「NATネットワーク」（`ファイル(F)`→`環境設定(P)`の`ネットワーク`で作成）を使用する。

<div class="imgtitle">ファイル→環境設定</div>
<a href="images\2021-04-12-00-37-00.png"><img src="images\2021-04-12-00-37-00.png" height="250"/></a>
<div class="imgtitle">NATネットワークの設定</div>
<a href="images\2021-04-12-00-37-52.png"><img src="images\2021-04-12-00-37-52.png" width="250"/></a>

### USBの設定（任意）

USB 3.x を使用する場合、ゲストOSの設定でUSB 3.0コントローラーを有効にします（<a href="extpack">拡張パック</a>が必要です *※バージョン7.0以降不要*）。
ゲストOS（Ubuntu/CentOS）をインストールした後で設定することも可能です。この場合、この場合、ゲストOSをシャットダウンしてから設定してください。

<div class="imgtitle">ゲストOSの設定</div>
<a href="images\2021-04-12-00-40-16.png"><img src="images\2021-04-12-00-40-16.png" width="300"/></a>
<div class="imgtitle">USB 3.0コントローラーを使用可能にする</div>
<a href="images\2021-04-12-00-41-12.png"><img src="images\2021-04-12-00-41-12.png" width="300"/></a>

## <a name="ubuntu_install">ゲストOS（Ubuntu）のインストール</a>

<!-- <span style="font-size: 80%; align: right;"><a href="ubuntu_install">Ubuntuのインストール</a></span> -->

ゲストOSを起動し、UbuntuのISOイメージを選択して`起動`をクリックするとUbuntuのインストーラーが起動します。

<div class="imgtitle">ゲストOSを起動する</div>
<a href="images\2021-04-12-00-55-04.png"><img src="images\2021-04-12-00-55-04.png" width="300"/></a>
<div class="imgtitle">インストールディスクを選択する</div>
<a href="images\2021-04-12-00-55-46.png"><img src="images\2021-04-12-00-55-46.png" width="200"/></a>
<div class="imgtitle">光学ディスクを選択する</div>
<a href="images\2021-04-12-00-56-30.png"><img src="images\2021-04-12-00-56-30.png" width="250"/></a>
<div class="imgtitle">ISOイメージを選択して開く</div>
<a href="images\2021-04-12-00-57-12.png"><img src="images\2021-04-12-00-57-12.png" width="250"/></a>
<div class="imgtitle">起動に使用するISOイメージを選択</div>
<a href="images\2021-04-12-00-58-20.png"><img src="images\2021-04-12-00-58-20.png" width="250"/></a>
<div class="imgtitle">起動をクリック</div>
<a href="images\2021-04-12-00-59-22.png"><img src="images\2021-04-12-00-59-22.png" width="200"/></a>

### 言語の選択

Ubuntuのインストーラが起動するので、言語を選択して「Ubuntuのインストール」をクリックします。

<div class="imgtitle">UbuntuのISOイメージから起動</div>
<a href="images\2021-04-12-01-00-14.png"><img src="images\2021-04-12-01-00-14.png" height="250"/></a>
<div class="imgtitle">言語を探す</div>
<a href="images\2021-04-12-01-01-22.png"><img src="images\2021-04-12-01-01-22.png" height="250"/></a>
<div class="imgtitle">言語をクリック</div>
<a href="images\2021-04-12-01-01-53.png"><img src="images\2021-04-12-01-01-53.png" height="250"/></a>
<div class="imgtitle">インストール開始</div>
<a href="images\2021-04-12-01-02-51.png"><img src="images\2021-04-12-01-02-51.png" height="250"/></a>

### インストール用の設定

画面に従ってインストールを進めます。［続ける］というボタンは画面の右下に表示されています。
*※ボタンが画面上に表示されない場合はAlt+F7でスクロール（[画面例](altf7.md)）*

<div class="imgtitle">キーボードレイアウトの選択</div>
<a href="images\2021-04-12-01-05-18.png"><img src="images\2021-04-12-01-05-18.png" height="250"/></a>
<div class="imgtitle">アップデートと他のソフトウェア</div>
<a href="images\2021-04-12-01-08-13.png"><img src="images\2021-04-12-01-08-13.png" height="250"/></a>
<div class="imgtitle">インストールの種類</div>
<a href="images\2021-04-12-01-12-39.png"><img src="images\2021-04-12-01-12-39.png" height="250"/></a>
<div class="imgtitle">インストールの種類（確認）</div>
<a href="images\2021-04-12-01-13-44.png"><img src="images\2021-04-12-01-13-44.png" height="250"/></a>
<div class="imgtitle">地域の選択</div>
<a href="images\2021-04-12-01-14-18.png"><img src="images\2021-04-12-01-14-18.png" height="250"/></a>
<div class="imgtitle">ユーザー名、コンピューター名およびパスワードの設定</div>
<a href="images\2021-04-12-01-15-36.png"><img src="images\2021-04-12-01-15-36.png" height="250"/></a>
<div class="imgtitle">（インストール中）</div>
<a href="images\2021-04-12-01-19-11.png"><img src="images\2021-04-12-01-19-11.png" height="250"/></a>

### 再起動

再起動を促すメッセージが表示されるので、［今すぐ再起動する］をクリックし、起動画面でEnterキーを押して再起動します。

<div class="imgtitle">今すぐ再起動するをクリック</div>
<a href="images\2021-04-12-01-21-54.png"><img src="images\2021-04-12-01-21-54.png" height="250"/></a>
<div class="imgtitle">ゲストOSの画面をクリックしてEnter</div>
<a href="images\2021-04-12-01-37-55.png"><img src="images\2021-04-12-01-37-55.png" height="250"/></a>

ゲストOSの画面をクリックすると、キー操作やマウス入力をゲストOSが受け取る状態（キャプチャーされた状態）となります。ホストOS側を操作したい場合は、右側のCtrlキーを押します。このキーを**ホストキー**と言い、VirtualBoxの右下にも表示されています。
なお、ゲストOSでGuest Additionsをインストールすると自動切替えになります。

### 再起動後の設定

再起動するとGUI画面が表示されるのでインストールを完了させます。

<div class="imgtitle">ユーザーを選択してパスワードを入力</div>
<a href="images\2021-04-12-01-27-19.png"><img src="images\2021-04-12-01-27-19.png" height="250"/></a>
<div class="imgtitle">オンラインアカウントへの接続（任意）</div>
<a href="images\2021-04-12-01-39-07.png"><img src="images\2021-04-12-01-39-07.png" height="250"/></a>
<div class="imgtitle">Livepatchの有効化（任意）</div>
<a href="images\2021-04-12-01-39-33.png"><img src="images\2021-04-12-01-39-33.png" height="250"/></a>
<div class="imgtitle">エラーリポートの送信（任意）</div>
<a href="images\2021-04-12-01-40-50.png"><img src="images\2021-04-12-01-40-50.png" height="250"/></a>
<div class="imgtitle">位置情報サービスの設定（任意）</div>
<a href="images\2021-04-12-01-41-23.png"><img src="images\2021-04-12-01-41-23.png" height="250"/></a>
<div class="imgtitle">完了</div>
<a href="images\2021-04-12-01-42-13.png"><img src="images\2021-04-12-01-42-13.png" height="250"/></a>

### 追加のインストールと更新

完了後「不完全な言語サポート」および「ソフトウェアの更新」メッセージが表示されることがあります。先に出た方を完了させてから、次を実行するようにしてください。それぞれ、「認証が必要です」というメッセージが表示されたらログインしているユーザーのパスワードを入力し、「認証」をクリックします。

<div class="imgtitle">不完全な言語サポート</div>
<a href="images\2021-04-12-01-49-42.png"><img src="images\2021-04-12-01-49-42.png" height="250"/></a>
<div class="imgtitle">ソフトウェアの更新</div>
<a href="images\2021-04-12-01-50-56.png"><img src="images\2021-04-12-01-50-56.png" height="250"/></a>
<div class="imgtitle">認証</div>
<a href="images\2021-04-12-01-53-38.png"><img src="images\2021-04-12-01-53-38.png" height="250"/></a>

### 更新後の再起動

ソフトウェアの更新が終わると再起動を促すメッセージが表示されます。他の操作を行ったなどでメッセージが表示されない場合があるので、画面左のDockで更新のアイコンををクリックして確認し、再起動してください。

<div class="imgtitle">ソフトウェア更新後の再起動</div>
<a href="images\2021-04-12-01-57-20.png"><img src="images\2021-04-12-01-57-20.png" height="250"/></a>

## Guest Additionsのインストール

再起動したらログインし、Guest Additions のインストールを行います。
Guest AdditionsはVirtualBoxのゲストOS専用のソフトウェアで、インストールすることでゲストOSの画面が見やすくなったり、ゲストOSとホストOSでコピー＆ペーストができるようになるなど、操作性が向上します。

VirtualBoxの`デバイス`メニューで`Guest Additions CDイメージの挿入`を選択すると、ゲストOS画面で自動実行のメッセージが表示されます。`実行(R)`をクリックすると認証画面が開くのでログインしているユーザーのパスワードを入力します。認証に成功すると端末が開き、Guest Additionsインストーラーが実行されます。

※表示されない場合は<code>sudo /media/ユーザー名/VBox_GAs_バージョン/VBoxLinuxAdditions.run</code>を実行。

`Press Return to close this window...`というメッセージが表示されたらEnterキーを押して終了します。

<div class="imgtitle">デバイス→Guest Additions CDイメージの挿入</div>
<a href="images\2021-04-12-02-21-57.png"><img src="images\2021-04-12-02-21-57.png" height="250"/></a>
<div class="imgtitle">自動起動ソフトウェアの実行</div>
<a href="images\2021-04-12-02-04-47.png"><img src="images\2021-04-12-02-04-47.png" height="250"/></a>
<div class="imgtitle">認証</div>
<a href="images\2021-04-12-02-06-04.png"><img src="images\2021-04-12-02-06-04.png" height="250"/></a>
<div class="imgtitle">Guest Additions</div>
<a href="images\2021-04-12-02-07-15.png"><img src="images\2021-04-12-02-07-15.png" height="250"/></a>

再起動すると、ゲストOSとホストOSの操作が自動切替えになる他、ゲストOSでの画面解像度の変更や、ゲストOSとホストOSクリップボードの共有設定が有効になります。

<div class="imgtitle">CDを取り出して大起動</div>
<a href="images\2021-04-12-02-37-40.png"><img src="images\2021-04-12-02-37-40.png" height="250"/></a>


※再起動してもゲストOSとホストOSの自動切替えやクリップボードの共有ができない場合、現在のカーネル用にGuest Additionsを再構築する必要があります。

`sudo apt install gcc make perl`で構築に使用するコマンドをインストールしてから、改めて`デバイス`→`Guest Additions CDイメージの挿入`を実行してください（aptコマンドについては第5章、makeコマンドについては章末コラムで解説）。

## Ubuntuの設定

Guest Additions をインストールして再起動したら、必要に応じ、画面のサイズなどを設定してください。

### 画面の解像度変更

画面の解像度は`設定`→`ディスプレイ`で変更できます。

<div class="imgtitle">設定</div>
<a href="images\2021-04-12-02-54-38.png"><img src="images\2021-04-12-02-54-38.png" height="250"/></a>
<div class="imgtitle">ディスプレイ</div>
<a href="images\2021-04-12-02-51-39.png"><img src="images\2021-04-12-02-51-39.png" height="250"/></a>

### クリップボードの共有

たとえば、ホストOSのWebブラウザで本ページを表示している場合、「ホストOSからゲストOSへ」（または「双方向」）を設定することで、Webブラウザに表示されているコマンド文字列を、端末に貼り付ける（端末で右クリック→貼り付け）ことができるようになります。  
端末に表示されているエラーメッセージなどを検索したい場合は、「ゲストOSからホストOSSへ」（または「双方向」）を設定しておくことで、マウスで端末の文字列を範囲選択して右クリック→コピーでコピーし、ホストOSのWebブラウザで検索するようなことができるようになります。

<div class="imgtitle">クリップボードの共有</div>
<a href="images\2021-04-12-02-57-54.png"><img src="images\2021-04-12-02-57-54.png" height="250"/></a>

## スナップショットの活用

VirtualBoxでは、任意のタイミングでゲストOSの**スナップショット**を作成しておくことができます。

### スナップショットの作成

<div class="imgtitle">仮想マシン→スナップショットの作成</div>
<a href="images\2021-04-12-03-05-47.png"><img src="images\2021-04-12-03-05-47.png" height="250"/></a>

### スナップショットの復元

仮想マシンの画面を閉じる際に現在の状態を保存するか、直前のスナップショットに戻すか選択できます。スナップショットが複数ある場合は、仮想マシンを終了させてからVirtualBoxの画面でスナップショットを選択します。

<div class="imgtitle">終了時の選択</div>
<a href="images\2021-04-12-03-13-18.png"><img src="images\2021-04-12-03-13-18.png" height="250"/></a>
<div class="imgtitle">起動時の選択</div>
<a href="images\2021-04-12-03-18-11.png"><img src="images\2021-04-12-03-18-11.png" width="300"/></a>

----
[Linux+コマンド入門 サポートページ](https://nisim-m.github.io/linuxcmdbook/)
