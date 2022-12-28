# ros2_ws/src/mypkg

これらのプログラムは授業により製作したものです。  
また、これらのノードは下の「**このパッケージのビルド方法について**」を行った上で実行してください。  



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
`talker.py`と`listener.py`の２つのノードを同時に実行できるファイルです。  
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




![test](https://github.com/moritaddaiki/ros2_ws/actions/workflows/test.yml/badge.svg)
<-これは`./github/workflows`のテストプログラムに通過しているか示すものです。


## 必要なソフトウェア
* Python
  テスト済み: 3.7～3.10

## テスト環境
* ubuntu
(作者はubuntu22.04.1 LTS を使っています。)


## このパッケージのビルド方法について  
**まず、リポジトリのコピーを完了してください。  
（詳しい方法は前ページに載っています。）**  
<br>

1.`ros2_ws`のディレクトリに移動してください。  
<br>

2.以下のコマンドを実行してください。これでパッケージ内容がビルドされます。  
```
$ colcon build
``` 
<br> 

3.次に`ros2_ws`下のパッケージを利用可能にするため、以下のコマンドを実行します。  
```
$ source ~/ros2_ws/install/setup.bash
$ source ~/ros2_ws/install/local_setup.bash
```  
<br>

4.次に、設定周りを読み込ませてそのパッケージが動作するか確認します。
```
$ source ~/.bashrc
$ ros2 pkg list | grep mypkg
mypkg
```  
<br>

5.以上でビルド作業は完了です。後は各プログラムを実行すれば結果が出ます。  



## ライセンスについて

このソフトウェアパッケージは、3条項BSDライセンスの下、再頒布および使用が許可されます。

詳しい内容は「LICENSE」をご確認ください。

 © 2022 Daiki Morita
