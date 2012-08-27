vssGetDiff
======================
VSSから、指定日時から現在日時で変更のあったファイルの最新版を、  
一括で取得するためのツールです。  

VSS 2005向けのツールです。  
diffコマンドの結果文字列をパースして処理するため、
他のバージョンではたぶん動きません。

ファイルの説明
--------------
・getDiff.wsf	：本体  
・getDiff.xml	：設定ファイル  
・getFiles	：取得ファイル格納ディレクトリ  
・tempFiles	：差分の比較元プロジェクト格納ディレクトリ  
・diffLog.txt	：tempFilesとVSS上の最新を比較した結果ログ  
・report.csv	：追加・更新・削除されたファイルの一覧  
・log.txt	：getDiff.wsfのログ(主にデバッグ用途)  

設定ファイルの説明
------------------
XML形式で記述し、本体と同じディテクトりに配置する。  

・/getDiff/vss/ssUser		：VSSのログインユーザー  
・/getDiff/vss/ssPwd		：VSSのログインパスワード  
・/getDiff/vss/ssDir		：VSSのDB初期化ファイル配置ディレクトリ  
・/getDiff/vss/instDir		：ss.exeの配置ディレクトリ  
・/getDiff/vss/projectNm	：プロジェクト名  
・/getDiff/dir/outDir		：ファイルの出力先のルートディレクトリ  
・/getDiff/dir/tempOutDir	：一時取得ファイルの出力先ディレクトり  
・/getDiff/dir/fileOutDir	：取得ファイルの出力先ディテクトリ  
・/getDiff/dir/diffLog		：diff結果ログの出力ファイル名  
・/getDiff/dir/getDiffLog	：本体ログの出力ファイル名  
・/getDiff/dir/report		：追加・更新・削除されたファイル一覧の出力ファイル名  
・/getDiff/getDate		：比較元の日付  

使用方法
--------
(1)設定ファイルを記述する。  
(2)以下のように実行する。  
  $>CScript getDiff.wsf

コマンドの説明
--------------
いくつかの値は、実行時に引数で指定することもできる。  

使い方 : getDiff.wsf [/ssUser:値] [/ssPwd:値] [/ssDir:値] [/Date:値]  

オプション :  
  ssUser : VSSのユーザー  
  ssPwd  : VSSのパスワード  
  ssDir  : VSSのDB初期化ファイル配置ディレクトリ  
  Date   : 差分の比較元日付(YY/MM/DD;HH:MM)  
  Example: getDiff.wsf /ssUser:foo /ssPwd:bar /ssDir:C:\VSS\ /Date:10/04/01;00:00  

(例) ログインユーザー「hisataka」、パスワード「hisataka」で、  
  2010/4/21 00:00以降に更新のあったファイルを取得する。  
  $>getDiff.wsf /ssUser:hisataka /ssPwd:hisataka /Date:10/4/21;00:00  