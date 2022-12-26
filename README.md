# 蟹味噌 (PC-98) TAS ムービー

encode: https://www.nicovideo.jp/watch/sm41562244

## ムービーの再生

ムービーは Debian testing 上の [libTAS](https://github.com/clementgallet/libTAS) + [AZO234/NP2kai](https://github.com/AZO234/NP2kai) で作成した。

再生手順は以下の通り:

* AZO234/NP2kai のタグ `rev.22` をチェックアウトし、SDL 版をビルドする。  
  元のソースをそのまま使うとマウスがキャプチャされてしまうので、`sdl2/np2.c` 内の `mousemng_hidecursor()` 呼び出しをコメントアウトする方がよい。
* libTAS 上で SDL 版の np2kai を実行する。  
  このとき、np2kai の設定ファイルとして `np2kai.cfg` を用いる。また、引数としてディスクイメージ `kanimiso.hdm` を与える。  
  nvidia ドライバを使っている場合、ソフトウェアレンダリングを強制するため `env __GLX_VENDOR_LIBRARY_NAME=mesa LIBGL_ALWAYS_SOFTWARE=1 libTAS` として起動する必要があるかもしれない。
* libTAS 上でムービーファイル `kanimiso.ltm` を再生する。

なお、蟹味噌を NP2kai 上で動かす場合、CPUクロック倍率が大きすぎるとステージ開始時に画面が崩れてハングアップする([Neko Project 21/W のドキュメント](https://simk98.github.io/np21w/freedos98.html)を参照)。  
本ムービーではクロック倍率を 8 倍にしている。
