# docker-dev

这是一个docker的服务器环境配置的项目，可以一键配置docker的php环境。

克隆本项目，执行命令
`docker-compose up -d`

## composer的安装

composer是php开发必须的包管理工具。所以开发环境需要使用composer进行安装相应的框架。

下载对应环境的版本
```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'a5c698ffe4b8e849a443b120cd5ba38043260d5c4023dbf93e1558871f1f07f58274fc6f4c93bcfd858c6bd0775cd8d1') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```
使用安装

`php composer.phar install ***`

## docker 安装  (ubuntu 18 环境)

参考[官方文档](https://docs.docker.com/v17.12/install/linux/docker-ce/ubuntu/#set-up-the-repository)

按照顺序执行，即可安装

## 参考文档


