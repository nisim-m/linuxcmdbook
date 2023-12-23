# Linux+コマンド入門
——シェルとコマンドライン、基本の力

[技術評論社](https://gihyo.jp/book/2021/978-4-297-12024-5)<br/>
[Amazon](https://www.amazon.co.jp/dp/4297120240/)  
2021.4.19

[Linux［基本］コマンドQuickリファレンス（配布版）](https://gihyo.jp/assets/pdf/book/2021/978-4-297-12024-5/LinuxCmdQuickReference.pdf)<br/>
読者の方向けのQuickリファレンスです。具体的な使い方は本文を参照してください。
ここに掲載されているコマンドとオプションは、すべて索引から検索できます。

## テスト環境

[VirtualBox+Ubuntu](howto/install-ubuntu.md)<br/>
[VirtualBox+CentOS](howto/install-centos.md)

## 正誤表

|ページ|内容|
|-|-|
|6.5 (p.196)|<small>1.太字部分を追加</small><br>&nbsp;systemctl**はsystemdを操作するのに使うコマンドです。systemd**はシステム全体の初期化などを担っている、すべてのプロセスの親となるプロセスです。最初に実行されるためプロセスIDは1になることから、`ps 1`で表示できます。<br><small>2.systemctlをsystemdに訂正</small><br>&nbsp;Ubuntu環境の場合、`ps 1`で`init`が表示されますが、`init`は`systemd`へのシンボリックリンクです。<br>|

## 履歴

- 2021.4 サポートページ公開
- 2021.6.17 正誤表(p.196) 追加
- 2023.1 VirtualBox 7.0 について追記 <small>（[Oracle VM VirtualBox 7.x.x needs the Microsoft Visual C++ 2019 Redistributable Packaging being installed first.”のようなメッセージが表示された場合](howto/install-vcpp.md)）, 解説はバージョン本書発売当時の6.1.18を使用していますが、基本的な表示や操作方法は共通です。</small>

----
[Linux+コマンド入門 サポートページ](https://nisim-m.github.io/linuxcmdbook/)
