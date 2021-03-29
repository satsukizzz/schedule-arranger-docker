# N予備校Web入門第4章16節の再現
このリポジトリの目的はWeb入門の最後に作る予定調整くんプロジェクトの完遂。

# なぜDockerのファイル群なのか
N予備校のWeb入門はVagrantで構成されている。

一方でWindows 10 Homeでも20H2のアップデートにより可能になったDocker for Desktop. これをWSL 2上で動かす。

つまりは、VagrantからDockerへの移行にかかる設定を試している。

# 構成
## リポジトリ
- docker用リポジトリ(schedule-arranger-docker)
- プロジェクト用リポジトリ(schedule-arranger)

## リポジトリを用意する
1. 好きなプロジェクト名のフォルダを作る
1. そこにdocker用リポジトリ、プロジェクト用リポジトリをそれぞれcloneする
1. schedule-arrangerリポジトリで`yarn install`をする…これはホスト環境で行う

注意：プロジェクト用リポジトリのフォルダ名の変更をしてはいけない(docker-composeが上手くいかなくなる)

## コンテナを立ち上げる
1. Git Bashを開く
1. dockerリポジトリ内で次のコマンドを実行する
`docker-compose up -d`
1. `http://localhost:8000`へアクセスして、サイトが表示されるのを確認する

## node/yarnのあるコンテナで作業したいとき
dockerリポジトリで
`docker-compose exec -u node appnode [command]`
を行えばコマンドが実行される。

もしくはコンテナ内に入るなら
`docker-compose exec -u node appnode bash`
とする。これは`node`ユーザーでbashを起動することに相当する。

間違っても`-u root`で入って作業してはいけない。root権限でファイルが作られると、windows側から編集ができなくなってしまう。


