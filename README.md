# ros2のパッケージ

これらのノードは授業により製作したものです。  
また、これらのノードは下の「**このパッケージのビルド方法について**」を行った上で実行してください。  

<br>

![test](https://github.com/moritaddaiki/ros2_ws/actions/workflows/test.yml/badge.svg)  
これは`./github/workflows/test.yml`のテストプログラムに通過しているか示すものです。
<br>


## 内容について

* **package.xml**  
モジュールの登録に用いたファイルです。  

* **setup.py**  
スクリプトの登録や`launch/talk_listen.launch.py`でノードを纏める時に使ったファイルです。  

* **.github/workflow/test.yml**  
テストバッジのプログラムです。

* **test/test.bash**  
`talker.py`と`listener.py`が正常に通信できているかについてのテストプログラムです。  

* **launch/talk_listen.launch.py**  
`talker.py`と`listener.py`の２つのノードを同時に実行できるノードです。  
また、実行するには以下のコマンドを実行してください。終了には`Ctrl+C`を入力してください。  
(数字はここに出している例と異なる場合がありますが、正常に作動します。)   
```
$ ros2 launch mypkg talk_listen.launch.py
[INFO] [launch]: All log files can be found below /home/moritadaiki/.ros/log/2022-12-17-14-11-17-935573-DESKTOP-KVQ8IC6-1508
[INFO] [launch]: Default logging verbosity is set to INFO
[INFO] [talker-1]: process started with pid [1509]
[INFO] [listener-2]: process started with pid [1511]
[listener-2] [INFO] [1671253878.884025200] [listener]: Listen: 0
[listener-2] [INFO] [1671253879.374483100] [listener]: Listen: 1
[listener-2] [INFO] [1671253879.874501800] [listener]: Listen: 2
[listener-2] [INFO] [1671253880.374409100] [listener]: Listen: 3
```

* **mypkg/talker.py**  
数字をカウントして送信するノードです。基本的に後述の`listener.py`と一緒に使います。  
また、実行するには以下のコマンドを入力してください。

```
$ ros2 run mypkg talker
<ここでは何も出力されません。>
```  

* **mypkg/listener.py**  
`talker.py`からメッセージを貰って表示するノードです。  
これを実行するには、もう1つを開いた上で以下のコマンドを実行してください。  
また、このノードを使用する場合は`talker.py`を実行しているターミナルではなく、新しいターミナルを開いて実行してください。  
その場合、新しいターミナルでも下に記述されている「**このパッケージのビルド方法について**」を行ってから実行してください。  
(数字はここに出している例と異なる場合がありますが、正常に作動します。) 

```
$ ros2 run mypkg listener.py
[INFO] [1671253843.712072100] [listener]: Listen: 42
[INFO] [1671253844.203989300] [listener]: Listen: 43
[INFO] [1671253844.704709000] [listener]: Listen: 44
[INFO] [1671253845.204017400] [listener]: Listen: 45
```



## 必要なソフトウェア
* Python  
テスト済み: 3.7～3.10

## テスト環境
* ubuntu
(作者はubuntu22.04.1 LTS を使っています。)


## このパッケージのコピー方法について

1.ubuntu22.04.1 LTSを開いて、任意の名前のディレクトリを作成します。ディレクトリを作成しなかった場合は現在開かれている場所にクローンしてきたリポジトリが作成されます。  
__(対応しているPythonのバージョンを一度確認してください。)__  
<br>

2.リポジトリの各種プログラムをみることができる画面の右くらいにある緑色の`<>Code`というボタンをクリックします。
<br>
<br>

３．`clone`という文字の下に`HTTPS` `SSH` `GitHub CLI`と書いてある部分のリポジトリパスをコピーします。  
githubアカウントを持っている人は`SSH`を、持っていない人は`HTTPS`のリポジトリパスをコピーしてください。
<br>
<br>

４．（１.）で作成したディレクトリで先程の手順でコピーしたリポジトリパス>を下のように実行します。  
<br>
**・githubアカウントを持っている人**
```
$ git clone git@github.com:moritaddaiki/ros2_ws.git
```
**・githubアカウントを持っていない人**
```
$ git clone https://github.com/moritaddaiki/ros2_ws.git
```
<br>
<br>

５．これでリポジトリのクローンが完了しました。後は各コードを実行すれば動きます。
<br>
<br>

## このパッケージのビルド方法について

1.コピーしたディレクトリの一番上に移動してください。  
(これらのノードは上の「**このパッケージのコピー方法について**」を行った上で実行してください。)  
<br>
<br>

2.以下のコマンドを実行してください。これでパッケージ内容がビルドされます。  
```
$ colcon build
``` 
<br>
<br> 

3.次に`ros2_ws`下のパッケージを利用可能にするため、以下のコマンドを実行します。  
```
$ source ~/ros2_ws/install/setup.bash
$ source ~/ros2_ws/install/local_setup.bash
```  
<br>
<br>

4.次に、設定周りを読み込ませてそのパッケージが動作するか確認します。
```
$ source ~/.bashrc
$ ros2 pkg list | grep mypkg
mypkg
```  
<br>
<br>

5.以上でビルド作業は完了です。後は各プログラムを実行すれば結果が出ます。  



## ライセンスについて

このソフトウェアパッケージは、3条項BSDライセンスの下、再頒布および使用が許可されます。

詳しい内容は「LICENSE」をご確認ください。

 © 2022 Daiki Morita
