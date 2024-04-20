[Linux+コマンド入門 サポートページ](https://nisim-m.github.io/linuxcmdbook/) ～学習用環境（VirtualBox + CentOS）～
# VirtualBox + CentOS

<!-- TOC -->

1. [ファイルのダウンロード](#ファイルのダウンロード)
    1. [VirtualBox](#virtualbox)
    2. [CentOSのISOイメージ](#centosのisoイメージ)
2. [VirtualBoxのインストール](#virtualboxのインストール)
    1. [<a name="extpack">拡張パック</a>のインストール](#a-nameextpack拡張パックaのインストール)
2. [仮想マシンの作成（Ubuntu/CentOS共通）](#仮想マシンの作成ubuntucentos共通)
    1. [名前とオペレーションシステムの選択](#名前とオペレーションシステムの選択)
    2. [メモリーサイズの入力](#メモリーサイズの入力)
    3. [ハードディスクの作成](#ハードディスクの作成)
    4. [<a name="portforwarding">ホストOSから接続するための設定（任意）</a>](#a-nameportforwardingホストosから接続するための設定任意a)
    5. [USBの設定（任意）](#usbの設定任意)
2. [<a name="centosinstall">ゲストOS（CentOS）のインストール</a>](#a-namecentosinstallゲストoscentosのインストールa)
    1. [インストールの開始](#インストールの開始)
    2. [インストール用の設定](#インストール用の設定)
    3. [再起動と初期セットアップ](#再起動と初期セットアップ)
    4. [再起動後の設定](#再起動後の設定)
2. [Guest Additionsのインストール](#guest-additionsのインストール)
    1. [ネットワーク接続を有効にする](#ネットワーク接続を有効にする)
    2. [開発用のコマンドとライブラリをインストールする](#開発用のコマンドとライブラリをインストールする)
    3. [再起動](#再起動)
    4. [Guest Additionsのインストール](#guest-additionsのインストール)
2. [CentOSの設定](#centosの設定)
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

### CentOSのISOイメージ

CentOS Streamインストール用のイメージファイルは下記のURLからダウンロードできます。

[https://www.centos.org/centos-stream/](https://www.centos.org/centos-stream/)

※ここでは、CentOS-Stream-8-x86_64-20210302-dvd1.isoを使用。

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
- バージョン … Red Hat (64-bit) 

※仮想マシンに`CentOS`を含んだ名前を付けると、タイプとバージョンが自動で設定される。

<div class="imgtitle">CentOSの例</div>
<a href="images\2021-04-11-23-57-16.png"><img src="images\2021-04-11-23-57-16.png" width="250"/></a>

<small>*※VirtualBox 7.0では自動インストールが可能になっていますが本ページでは6.1.xでの手動インストールで解説しています（[画面例](using_vbox7.md)）。*</small>

###  メモリーサイズの入力

ゲストOSに割り当てるメモリーのサイズを入力します。たくさん割り当てることでゲストOSが快適に動作するようになりますが、その分、ホストOSの動作が犠牲になります。  
本書のサンプルを実行する場合、1024～2048MB程度で問題ありません。

<div class="imgtitle">メモリーサイズ</div>
<a href="images\2021-04-12-00-00-16.png"><img src="images\2021-04-12-00-00-16.png" width="250"/></a>

###  ハードディスクの作成

1. `仮想ハードディスクを作成する(C)`（デフォルト）を選んで`作成`をクリック
1. `VDI(VirtualBox Disk Image)`（デフォルト）を選んで`次へ(N)`をクリック
1. `可変サイズ(D)`（デフォルト）を選んで`次へ(N)`をクリック
1. サイズを入力して`作成`をクリック
CentOS Stream 8のインストールには9.32GiB以上必要なため**デフォルトの8GBでは不足**します。他の操作なども試すことを想定し、少し大きめにしておく方が扱いやすいでしょう。なお、「可変サイズ」を選択している場合、ホストOSのディスクを消費するのはゲストOSで実際に使用した分のみです。

<div class="imgtitle">ハードディスク</div>
<a href="images\2021-04-12-00-04-27.png"><img src="images\2021-04-12-00-04-27.png" width="250"/></a>
<div class="imgtitle">ハードディスクのタイプ</div>
<a href="images\2021-04-12-00-04-37.png"><img src="images\2021-04-12-00-04-37.png" width="250"/></a>
<div class="imgtitle">物理ハードディスクにあるストレージ</div>

<div class="imgtitle">ファイルの場所とサイズ</div>
<a href="images\2021-04-14-15-59-10.png"><img src="images\2021-04-14-15-59-10.png" width="300"/></a>

###  <a name="portforwarding">ホストOSから接続するための設定（任意）</a>

ホストOSからゲストOSのWebサーバーやSSHサーバーに接続してみたい場合は、下記を設定しておきます。
ゲストOS（Ubuntu/CentOS）をインストールした後で設定することも可能です。

ネットワーク：NAT（デフォルト）  
ネットワークアダプターを有効化にチェックマーク（デフォルト）  

`高度`→`ポートフォワーディング(P)`で以下を設定
- Webブラウザ用（http）… ホストポート 50180、ゲストポート 80
- コマンドライン用（ssh）… ホストポート 50122、ゲストポート 22

※ホストポートの番号はに任意（1024から49451の範囲で指定）。
※名前は任意、プロトコルはTCP、ホストIPとゲストIPは空欄。
※複数のゲストOSをインストールしてみたい場合は、ゲストOS毎に異なるポート番号を設定する。


<div class="imgtitle">ゲストOSの設定</div>
<a href="images\2021-04-14-16-10-08.png"><img src="images\2021-04-14-16-10-08.png" width="350"/></a>
<div class="imgtitle">ネットワーク</div>
<a href="images\2021-04-14-16-12-01.png"><img src="images\2021-04-14-16-12-01.png" width="350"/></a>

<div class="imgtitle">ポートフォワーディング</div>
<a href="images\2021-04-12-00-33-26.png"><img src="images\2021-04-12-00-33-26.png" width="250"/></a>

※ゲストOS同士の通信をしたい場合は、「ブリッジ」または「NATネットワーク」（`ファイル(F)`→`環境設定(P)`の`ネットワーク`で作成）を使用する。

<div class="imgtitle">ファイル→環境設定</div>
<a href="images\2021-04-12-00-37-00.png"><img src="images\2021-04-12-00-37-00.png" width="250"/></a>
<div class="imgtitle">NATネットワークの設定</div>
<a href="images\2021-04-12-00-37-52.png"><img src="images\2021-04-12-00-37-52.png" width="250"/></a>

### USBの設定（任意）

USB 3.x を使用する場合、ゲストOSの設定でUSB 3.0コントローラーを有効にします（<a href="extpack">拡張パック</a>が必要です *※バージョン7.0以降不要*）。
ゲストOS（Ubuntu/CentOS）をインストールした後で設定することも可能です。この場合、この場合、ゲストOSをシャットダウンしてから設定してください。

<div class="imgtitle">ゲストOSの設定</div>
<a href="images\2021-04-14-16-10-08.png"><img src="images\2021-04-14-16-10-08.png" width="350"/></a>
<div class="imgtitle">USB 3.0コントローラーを使用可能にする</div>
<a href="images\2021-04-14-16-14-02.png"><img src="images\2021-04-14-16-14-02.png" width="350"/></a>

## <a name="centos_install">ゲストOS（CentOS）のインストール</a>

ゲストOSを起動し、CentOSのISOイメージを選択して`起動`をクリックするとCentOSのインストーラーが起動します。

<div class="imgtitle">ゲストOSを起動する</div>
<a href="images\2021-04-14-16-14-57.png"><img src="images\2021-04-14-16-14-57.png" width="350"/></a>
<div class="imgtitle">インストールディスクを選択する</div>
<a href="images\2021-04-14-13-56-36.png"><img src="images\2021-04-14-13-56-36.png" width="150"/></a>
<div class="imgtitle">光学ディスクを選択する</div>
<a href="images\2021-04-14-14-00-37.png"><img src="images\2021-04-14-14-00-37.png" width="200"/></a>
<div class="imgtitle">ISOイメージを選択して開く</div>
<a href="images\2021-04-14-15-07-19.png"><img src="images\2021-04-14-15-07-19.png" width="200"/></a>
<div class="imgtitle">起動に使用するISOイメージを選択</div>
<a href="images\2021-04-14-15-29-35.png"><img src="images\2021-04-14-15-29-35.png" width="150"/></a>


### インストールの開始

起動メニュー画面が表示されるので、ゲストOSの画面をクリックして「i」と入力してInstallを選択し、［Enter］で開始します。

ゲストOSの画面をクリックすると、キー操作やマウス入力をゲストOSが受け取る状態（キャプチャーされた状態）となります。ホストOS側を操作したい場合は、右側のCtrlキーを押します。このキーをホストキーと言い、VirtualBoxの右下にも表示されています。 なお、ゲストOSでGuest Additionsをインストールすると自動切替えになります。

<div class="imgtitle">「i」でインストールを選択して起動</div>
<a href="images\2021-04-14-15-37-48.png"><img src="images\2021-04-14-15-37-48.png" height="250"/></a>

### インストール用の設定

画面に従ってインストールを進めます。言語の選択に続いて、右上の「インストール先」および左下の「ユーザーの設定」を行う必要があります。ユーザーの設定は「rootパスワード(R)」と「ユーザーの作成(U)」があり、ユーザーの作成時に**「このユーザーを管理者にする」を有効にする**ことで、sudoコマンド（本文参照）が使用可能になります。
設定が終わると右下の「インストールの開始」がクリック可能になります。

<div class="imgtitle">「日本語」を選択する</div>
<a href="images\2021-04-14-15-47-28.png"><img src="images\2021-04-14-15-47-28.png" height="250"/></a>
<div class="imgtitle">「インストール先」をクリック</div>
<a href="images\2021-04-14-15-42-35.png"><img src="images\2021-04-14-15-42-35.png" height="250"/></a>
<div class="imgtitle">「完了」をクリック（設定変更不要）</div>
<a href="images\2021-04-14-16-18-44.png"><img src="images\2021-04-14-16-18-44.png" height="250"/></a>
<div class="imgtitle">「rootパスワード(R)」をクリック」</div>
<a href="images\2021-04-14-16-20-26.png"><img src="images\2021-04-14-16-20-26.png" height="250"/></a>
<div class="imgtitle">管理者用のパスワードを設定して「完了」をクリック</div>
<a href="images\2021-04-14-16-23-29.png"><img src="images\2021-04-14-16-23-29.png" height="250"/></a>
<div class="imgtitle">「ユーザーの作成(U)をクリック」</div>
<a href="images\2021-04-14-16-24-54.png"><img src="images\2021-04-14-16-24-54.png" height="250"/></a>
<div class="imgtitle">普段使用するユーザーの名前とパスワードを設定して「完了」をクリック</div>
<a href="images\2021-04-14-16-28-38.png"><img src="images\2021-04-14-16-28-38.png" height="250"/></a>
<div class="imgtitle">「インストールの開始」をクリック</div>
<a href="images\2021-04-14-16-32-18.png"><img src="images\2021-04-14-16-32-18.png" height="250"/></a>
<div class="imgtitle">（インストール中の画面）</div>
<a href="images\2021-04-14-16-33-28.png"><img src="images\2021-04-14-16-33-28.png" height="250"/></a>

### 再起動と初期セットアップ

右下の「システムの再起動」ボタンが有効になったらクリックして再起動します。

<div class="imgtitle">「システムの再起動」をクリック</div>
<a href="images\2021-04-14-16-34-08.png"><img src="images\2021-04-14-16-34-08.png" width="300"/></a>
<div class="imgtitle">（起動中の画面）</div>
<a href="images\2021-04-14-17-27-57.png"><img src="images\2021-04-14-17-27-57.png" width="300"/></a>

起動メニューが表示されます。自動で実行されるので操作は不要ですが、起動メニューが表示されている時にゲストOS画面をクリックした場合は入力待ちの状態になります。この場合は矢印キーで上の行を選択して［Enter］で起動してください。

<div class="imgtitle">（起動メニュー）</div>
<a href="images\2021-04-14-17-28-12.png"><img src="images\2021-04-14-17-28-12.png" width="300"/></a>

起動すると「初期セットアップ」の画面が開くので、「ライセンス情報(L)」をクリックして設定を完了させ

<div class="imgtitle">「ライセンス情報(L)」をクリック</div>
<a href="images\2021-04-14-16-41-24.png"><img src="images\2021-04-14-16-41-24.png" width="300"/></a>
<div class="imgtitle">ライセンス契約に同意して「完了」をクリック</div>
<a href="images\2021-04-14-16-43-31.png"><img src="images\2021-04-14-16-43-31.png" width="300"/></a>
<div class="imgtitle">「設定の完了(F)」をクリック</div>
<a href="images\2021-04-14-16-44-18.png"><img src="images\2021-04-14-16-44-18.png" width="300"/></a>

### 再起動後の設定

「設定の完了(F)」をクリックするとログイン画面が表示されるので、インストール時に作成したユーザーでログイン（サインイン）してインストールを完了させます。
「CentOS Streamを使い始める」をクリックすると「初めて使う方へ」という画面が表示されます。GUI画面の操作を確認したい場合はそれぞれの動画を再生してください。画面を閉じるとデスクトップが表示されます。

なお、「初めて使う方へ」の画面はアクティビティの「ヘルプ」（救助浮き輪のアイコン）→「GNOMEを初めて使う方へ」で再表示できます。

<div class="imgtitle">ユーザー名をクリック</div>
<a href="images\2021-04-14-16-45-55.png"><img src="images\2021-04-14-16-45-55.png" width="300"/></a>
<div class="imgtitle">パスワードを入力してサインイン</div>
<a href="images\2021-04-14-16-48-45.png"><img src="images\2021-04-14-16-48-45.png" width="300"/></a>
<div class="imgtitle">言語を選択（日本語を選択）</div>
<a href="images\2021-04-14-16-49-29.png"><img src="images\2021-04-14-16-49-29.png" width="300"/></a>
<div class="imgtitle">入力を設定（自動選択のままでよい））</div>
<a href="images\2021-04-14-16-50-47.png"><img src="images\2021-04-14-16-50-47.png" width="300"/></a>
<div class="imgtitle">位置情報サービスの使用を選択（任意）</div>
<a href="images\2021-04-14-16-51-56.png"><img src="images\2021-04-14-16-51-56.png" width="300"/></a>
<div class="imgtitle">オンラインアカウントへの接続（任意）</div>
<a href="images\2021-04-14-16-52-51.png"><img src="images\2021-04-14-16-52-51.png" width="300"/></a>
<div class="imgtitle">「使い始める」をクリック</div>
<a href="images\2021-04-14-16-53-36.png"><img src="images\2021-04-14-16-53-36.png" width="300"/></a>
<div class="imgtitle">「初めて使う方へ」（任意で再生して閉じる）</div>
<a href="images\2021-04-14-16-54-19.png"><img src="images\2021-04-14-16-54-19.png" width="300"/></a>
<div class="imgtitle">デスクトップ</div>
<a href="images\2021-04-14-17-15-11.png"><img src="images\2021-04-14-17-15-11.png" width="300"/></a>
<div class="imgtitle">アクティビティ</div>
<a href="images\2021-04-14-17-15-55.png"><img src="images\2021-04-14-17-15-55.png" width="300"/></a>

## Guest Additionsのインストール

再起動したらログインし、Guest Additions のインストールを行います。

Guest AdditionsはVirtualBoxのゲストOS専用のソフトウェアで、インストールすることでゲストOSの画面が見やすくなったり、ゲストOSとホストOSでコピー＆ペーストができるようになるなど、操作性が向上します。

CentOSの場合、Guest Additionsのインストールに先立ち、開発用のコマンドとライブラリのインストールが必要です<small>（※VirtualBoxのバージョンおよびCentOSのバージョンの組み合わせによって異なります）</small>。

### ネットワーク接続を有効にする

コマンドのインストールにはネットワーク接続が必要です。VirtualBoxのゲストOSの場合「有線接続」扱いトナルので、画面右上の設定メニューで「有線オフ」→「接続」をクリックします。

<div class="imgtitle">ネットワーク接続を有効にする</div>
<a href="images\2021-04-14-17-46-11.png"><img src="images\2021-04-14-17-46-11.png" width="300"/></a>

※コマンドラインで有効にしたい場合は、`sudo ifup enp0s3`を実行。自動接続にしたい場合は`/etc/sysconfig/network-script/ifcfg-enp03s`の`ONBOOT`行を`NO`から`YES`に変更。

### 開発用のコマンドとライブラリをインストールする

Guest Additionsの構築には、`gcc`コマンドと`make`コマンド、およびカーネルとカーネル用のライブラリ（`kernel`、`kernel-devel`、`elfutils-libelf-devel`）が必要です。以下のコマンドでインストールできます。

```
sudo dnf install gcc make kernel kernel-devel elfutils-libelf-devel
```

パスワードの入力が求められるので、現在ログインしているユーザーのパスワードを入力して実行してください。途中、実行確認のメッセージが表示されたら「y」を入力すると先に進むことができます（`-y`オプションで確認省略可能、5.3節 p.156）。

インストール時に「このユーザーを管理者にする」を有効にしていなかった場合、「」というメッセージが表示されてコマンドが実行できません。この場合は、「su」コマンドを実行して、**rootユーザーのパスワード**を入力し、以下を実行します。

```
dnf install gcc make kernel kernel-devel elfutils-libelf-devel
```

<small>
※sudoはコマンドを別のユーザーとして実行できるというコマンドで、`sudo コマンド`でシステム管理者の権限（root権限）が必要なコマンドを実行できます。suコマンドはユーザーを切り替える（substitute user）コマンドで、suだけで実行するとrootユーザーになることができますが、実行にはrootユーザーのパスワードが必要です（p.17、6.1節 p.194）。
CentOSでsudoが実行できない場合は、いったん`su`でrootユーザーになり、`gpasswd -a ユーザー名 wheel`でユーザーをwheelグループのメンバーにしてください（コラム「CentOSでsudoが使用できない場合」）。
</small>

コマンドを入力する「端末」ウィンドウは「アクティビティ」から起動できます。
プロンプト（[ユーザー名@localhost] $）が表示されるので、上記のコマンドを入力してEnterで実行してください。

<div class="imgtitle">開発コマンドとライブラリのインストール</div>
<a href="images\2021-04-14-18-39-38.png"><img src="images\2021-04-14-18-39-38.png" width="300"/></a>

### 再起動

カーネル（kernelとkernel-devel）を更新しているため、いったん再起動します。

<div class="imgtitle">再起動</div>
<a href="images\2021-04-14-18-47-47.png"><img src="images\2021-04-14-18-47-47.png" width="300"/></a>
<div class="imgtitle">（再起動中の画面）</div>
<a href="images\2021-04-14-18-50-11.png"><img src="images\2021-04-14-18-50-11.png" width="300"/></a>

### Guest Additionsのインストール

VirtualBoxの`デバイス`メニューで`Guest Additions CDイメージの挿入`を選択すると、ゲストOS画面で自動実行のメッセージが表示されます。`実行(R)`をクリックすると認証画面が開くのでログインしているユーザーのパスワードを入力します。認証に成功すると端末が開き、Guest Additionsインストーラーが実行されます。

`Press Return to close this window...`というメッセージが表示されたらEnterキーを押して終了し、再起動します。

<div class="imgtitle">デバイス→Guest Additions CDイメージの挿入</div>
<a href="images\2021-04-14-18-52-22.png"><img src="images\2021-04-14-18-52-22.png" width="300"/></a>
<div class="imgtitle">自動起動ソフトウェアの実行</div>
<a href="images\2021-04-14-18-53-07.png"><img src="images\2021-04-14-18-53-07.png" width="300"/></a>
<div class="imgtitle">認証</div>
<a href="images\2021-04-14-18-54-02.png"><img src="images\2021-04-14-18-54-02.png" width="300"/></a>
<div class="imgtitle">Guest Additions</div>
<a href="images\2021-04-14-18-55-16.png"><img src="images\2021-04-14-18-55-16.png" width="300"/></a>

再起動すると、ゲストOSとホストOSの操作が自動切替えになる他、ゲストOSでの画面解像度の変更や、ゲストOSとホストOSクリップボードの共有設定が有効になります。

## CentOSの設定

Guest Additions をインストールして再起動したら、必要に応じ、画面のサイズなどを設定してください。

### 画面の解像度変更

画面の解像度は`設定`→`ディスプレイ`で変更できます。

<div class="imgtitle">設定を開く</div>
<a href="images\2021-04-14-19-03-21.png"><img src="images\2021-04-14-19-03-21.png" width="300"/></a>
<div class="imgtitle">設定画面</div>
<a href="images\2021-04-14-19-06-54.png"><img src="images\2021-04-14-19-06-54.png" width="300"/></a>
<div class="imgtitle">解像度の変更</div>
<a href="images\2021-04-14-19-08-46.png"><img src="images\2021-04-14-19-08-46.png" width="300"/></a>

### クリップボードの共有

たとえば、ホストOSのWebブラウザで本ページを表示している場合、「ホストOSからゲストOSへ」（または「双方向」）を設定することで、Webブラウザに表示されているコマンド文字列を、端末に貼り付ける（端末で右クリック→貼り付け）ことができるようになります。  
端末に表示されているエラーメッセージなどを検索したい場合は、「ゲストOSからホストOSSへ」（または「双方向」）を設定しておくことで、マウスで端末の文字列を範囲選択して右クリック→コピーでコピーし、ホストOSのWebブラウザで検索するようなことができるようになります。

<div class="imgtitle">クリップボードの共有</div>
<a href="images\2021-04-14-19-00-57.png"><img src="images\2021-04-14-19-00-57.png" width="300"/></a>


## スナップショットの活用

VirtualBoxでは、任意のタイミングでゲストOSの**スナップショット**を作成しておくことができます。

### スナップショットの作成

<div class="imgtitle">仮想マシン→スナップショットの作成</div>
<a href="images\2021-04-14-19-11-57.png"><img src="images\2021-04-14-19-11-57.png" width="300"/></a>

### スナップショットの復元

仮想マシンの画面を閉じる際に現在の状態を保存するか、直前のスナップショットに戻すか選択できます。スナップショットが複数ある場合は、仮想マシンを終了させてからVirtualBoxの画面でスナップショットを選択します。

<div class="imgtitle">終了時の選択</div>
<a href="images\2021-04-14-19-21-11.png"><img src="images\2021-04-14-19-21-11.png" width="300"/></a>
<div class="imgtitle">起動時の選択</div>
<a href="images\2021-04-14-19-27-17.png"><img src="images\2021-04-14-19-27-17.png" width="300"/></a>

----
[Linux+コマンド入門 サポートページ](https://nisim-m.github.io/linuxcmdbook/)
