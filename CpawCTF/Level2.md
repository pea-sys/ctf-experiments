# Level 2

## Q13.[Stego]隠されたフラグ

画像に記された記号を解析する課題です。  
画像の左上と右下には拡大するとドットとハイフンで記載された記号が書き込まれています。  
モールス信号なので復号して提出。  
https://morse.ariafloat.com/en/

## Q15.[Web] Redirect

リダイレクト方法を調べる課題です。  
指定の URL に GET リクエストした際の応答を確認すると X-Flag ヘッダーに答えがあります。

## Q16.[Network+Forensic]HTTP Traffic

Wireshark で pcap ファイルを開き、オブジェクトを全てファイル出力する。  
html を読んで、js を適切なフォルダに再配置して html ページを表示して、ボタンを押すと答えが表示されます。

## Q17.[Recon]Who am I ?

出題者の Twitter から情報を収集する。  
Google 検索でアカウントとゲーム名を一緒に検索して、ポスト内容を見ると答えが確認できます。

## Q18.[Forensic]leaf in forest

提供されたテキストファイルから答えを探します。  
頻出ワードを置換で消していけば答えが残ります。

## Q19.[Misc]Image!

zip ファイルから答えを探します。  
解凍ファイルをいくつか眺めて見ると、office 系のファイルであることが分かります。  
zip ファイルの拡張子を doc に変えて開くと答えが確認できます。

## Q20.[Crypto]Block Cipher

与えられた暗号をプログラムで復号します。  
復号キーは与えられていないので、推測します(大文字の位置)。  
プログラムは paiza.io で実行しました。

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(){
  int i;
  int j;
  int key = 4;
  const char* flag = "ruoYced_ehpigniriks_i_llrg_stae";
  printf("cpaw{");
  for(i = key - 1; i <= strlen(flag); i+=key)
	for(j = i; j>= i - key + 1; j--)
		printf("%c", flag[j]);
  printf("}");
  return 0;
}

```

## Q21.[Reversing]reversing easy!

バイナリの可読部分を表示する strings コマンドで分かる  
たまたま静的に宣言されているから、この方法でいけるけど
本当はデバッグでメモリを覗くをやりたかった（現状やり方が分からない)

```
strings /mnt/c/Users/user/Downloads/rev100
```

### Q28.[Network] Can you login？

キャプチャデータから ftp サーバにログインするための id とパスワードを得る  
passive モードでアクセスしてファイルを get して、中身を見ます
