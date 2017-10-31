# condaの使い方
## インストール
https://www.anaconda.com/download/  
にアクセスして、shファイルをダウンロードする。特にこだわりがなければPython3.6の方を使う。  
＊Downloadとでかでかと書いてあるボタンをクリックするとインストーラ版がダウンロードされてしまう。shの方がおすすめ。Command-Line InstallerをクリックすればOK。

ターミナルを立ち上げて、以下のコマンドを実行。
```
bash Anaconda3-5.0.1-MacOSX-x86_64.sh
```
＊`Anaconda...`の部分はダウンロードしたファイル名に合わせて適宜変更すること。

## 基本手順
### 1. 環境の作成
```
conda create -n test python=3.6 anaconda
```
＊`test`の部分は好きに変えて良い。

### 2. 作った環境へ入る
```
source activate test
```
＊成功するとユーザ名の手前に`(test)`と出る。  
例）
```
[user@localhost ~]$ source activate test
[(test)user@localhost ~]$
```

### 3. 作った環境へTensorFlowをインストールする。
```
conda install tensorflow
```

おまけ： JupyterNotebook用に色々インストールしておくと便利
```
conda install ipykernel
conda install nb_conda
python -m ipykernel install --user
```

## 作った環境の操作
### 作った環境の一覧を表示する
```
conda env list
```

### 作った環境をexportする
```
conda env export > myenv.yaml
```
＊`myenv.yaml`の部分は好きな名前にして良い。ただし、拡張子は`yaml`の方が何かと良い。

### 作った環境をimportする
```
conda env create --file myenv.yaml
```

### 環境の名前を変更する
環境の名前を変更するコマンドはないので、別名のクローンを作ってオリジナルを消す。  
例）`old_name`環境の名前を`new_name`に変更する
```
conda create --name new_name --clone old_name
conda remove --name old_name --all
```
