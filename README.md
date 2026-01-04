Dockerfile-Ubuntu-24.04 を追加しました。
これが、ubuntu24.04 に対応しています。
手順としては、patchを当てたあと、Dockerfile-Ubuntu-24.04を
imx-docker直下にコピーして使用してください。

また、docker build でubuntu24.04の際、以下のエラーに遭遇しました。
--------------------
  41 |         host_gid
  42 | >>> RUN groupadd -g $host_gid nxp && \
  43 | >>>     useradd -g $host_gid -m -s /bin/bash -u $host_uid $USER
  44 |
--------------------
これについては、dockerを実行する環境において、adduserにて以下のようにユーザー追加
することで回避できました。
sudo useradd user3
sudo usermod -aG sudo user3
以降user1でログインして実行。
2025.1.4 追記

note+の記事のためのパッチをgithubに公開しています。
https://note.com/lucky_ixia591/n/nc7b5c8438e7b
これは、imx-dockerのpatchです。
WSLかつubuntu22.04 でビルドするためのパッチです。
以下のサイトの情報からubuntu22.04にて確認しています。

imx-docker build fails under WSL2
https://community.nxp.com/t5/i-MX-Processors/imx-docker-build-fails-under-WSL2/m-p/1762318?profile.language=ja
https://github.com/nxp-imx/imx-docker/pull/3
