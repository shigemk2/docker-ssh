空パスワードまたは指定したパスワードで root ログインできるコンテナを作りログイン(CentOS6)

http://qiita.com/comutt/items/1251cc19885947cd6d3d

```sh
$ alias ssh-ignorekey='ssh -oUserKnownHostsFile=/dev/null -oStrictHostKeyChecking=no'
$ docker build -t ssh-enabled .
$ CONTAINER_ID=$(docker run -P -d ssh-enabled) && SSH_PORT=$(docker port $CONTAINER_ID 22 | cut -d: -f2) && SSH_HOST=$(docker port $CONTAINER_ID 22 | cut -d: -f1);
$ ssh-ignorekey -p $SSH_PORT root@$SSH_HOST
```
