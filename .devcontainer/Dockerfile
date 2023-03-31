FROM amazonlinux:2

ARG UID=1000

# python3, awscli インストール
RUN amazon-linux-extras install -y \
      python3.8 \
 && python3.8 -m pip install awscli

# その他ビルドに必要なパッケージ
RUN yum update && yum install -y \
      shadow-utils \
      sudo \
      tar \
 && rm -rf /var/cache/yum/* \
 && yum clean all

# ec2-user ユーザー追加
RUN useradd -u ${UID} ec2-user \
 && echo "ec2-user ALL=NOPASSWD: ALL" >> /etc/sudoers

# python コマンドで python3.8 が実行できるようにエイリアス設定
RUN echo "alias python=python3.8" >> /home/ec2-user/.bashrc

USER ${UID}
