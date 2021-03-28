# N予備校Web入門第4章16節の再現
このリポジトリの目的はWeb入門の最後に作る予定調整くんプロジェクトの完遂。

# なぜDockerのファイル群なのか
N予備校のWeb入門はVagrantで構成されている。

一方でWindows 10 Homeでも20H2のアップデートにより可能になったDocker for Desktop. これをWSL 2上で動かす。

つまりは、VagrantからDockerへの移行にかかる設定を試している。

# 構成
## リポジトリ
- Docker設定用リポジトリ(ここ)
- プロジェクト用リポジトリ(作成中)

## cloneするリポジトリ構成
1. 好きなプロジェクト名のフォルダを作る
1. そこにDockerリポジトリ、プロジェクトリポジトリをそれぞれcloneする
cloneしたフォルダ名の変更をしてはいけない(Dockerが上手くいかなくなる)

## コンテナを立ち上げる
1. Git Bashを開く
1. dockerリポジトリ内で次のコマンドを実行する
`docker-compose up -d`

## node/yarnのあるコンテナで作業したいとき
dockerリポジトリで
`docker-compose exec -uroot appnode [command]`
を行えばコマンドが実行される。

もしくはコンテナ内に入るなら
`docker-compose exec -uroot appnode bash`
とする。

なお、vagrantでの`PORT=8000 yarn start`に対応するコマンドは
`docker-compose exec -uroot -e PORT=8000 appnode yarn start`
である。環境変数はコンテナ`appnode`より先にかかないといけない。



