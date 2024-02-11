# Upgrade

[Upgrade-paths](https://docs.gitlab.com/ee/update/#upgrade-paths)

```shell
docker stop gitlab
docker rm gitlab
docker run --detach --hostname gitlab.myhost.ru --publish 443:443 --publish 80:80 --name gitlab --restart always --volume /root/gitlab/config:/etc/gitlab --volume /root/gitlab/logs:/var/log/gitlab --volume /root/gitlab/data:/var/opt/gitlab gitlab/gitlab-ee:14.10.5-ee.0
