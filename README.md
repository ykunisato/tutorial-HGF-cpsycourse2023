# CPSYコース東京2023 HGFチュートリアル

## はじめに

このリポジトリは、「CPSYコース東京2023」のHGFチュートリアル資料置き場です。

- [HGFモデルの基礎（Mathys et al., 2014）](equations_HGF.md)
- [必要なJuliaパッケージがインストールされているか確認する](01_check_HGF.ipynb)
- [入力が連続の場合のHGF](02_continuous.ipynb)
- [入力が２値の場合のHGF](03_binary.ipynb)

## このリポジトリにあるコードの実行方法

このリポジトリの実行方法としては、(1)GithubのCodespaces上での実行、(2)ご自身のPCでDockerを使って環境を構築して実行、(3)ご自身のPCでJulia環境とパッケージを手動で構築して実行の３つがあります。再現性のある実行環境の準備は難しいので、(1)を推奨しますが、Dockerに慣れている方は(2)の方がマシンパワーが強いと思われるので、良いかもしれません。

### (1)GithubのCodespaces上で実行する
#### このリポジトリをご自身のリポジトリにコピーする
「Use this template」をクリックして、このリポジトリをご自身のGithubリポジトリにおいてください（名前は自由に変更ください）。

<図の挿入>

#### Codespacesを立ち上げる

このリポジトリ内の.devcontainer内に使用するDockerイメージなどの情報が入っており、Codespacesを立ち上げれば自動的にそれらが反映されます。

＜図の挿入＞



### (2)ローカルPCで実行する
#### Dockerの用意

ご自身のPCにDockerを用意ください。Windowsの場合は、少し工夫が必要になります。普段からDockerを使っておられない場合は、Codespacesの利用をお勧めします。

#### hgfイメージを準備して実行

[hgf用イメージ](https://github.com/ykunisato/ghcr-hgf/pkgs/container/hgf)を用意しています。それぞれのローカルPCに合わせて以下のコマンドを実行ください。

- Mac(Intel)の場合

Terminalで以下を実行します。

```
docker run -d --name notebook -v `pwd`:/home/jovyan/work -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes ghcr.io/ykunisato/hgf:1.8.5 start-notebook.sh --NotebookApp.token="token that you set"
```

- Mac(Apple Silicon)の場合

Terminalで以下を実行します。

```
docker run -d --name notebook -v `pwd`:/home/jovyan/work -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes ghcr.io/ykunisato/hgf:1.8.5.arm start-notebook.sh --NotebookApp.token="token that you set"
```

- Windowsの場合

コマンドプロンプトで以下を実行します。

```
docker run -d --name notebook -v "%cd%":/home/jovyan/work -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes ghcr.io/ykunisato/hgf:1.8.5 start-notebook.sh --NotebookApp.token="token that you set"
```

イメージのプルや実行が済んだら、ブラウザに "http://localhost:8888/" を打ち込んで必要パッケージの用意されたJupyter環境にアクセスください。


