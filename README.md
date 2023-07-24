既存のimageを削除しておく
$ docker rmi mini-php

phpコンテナをビルドする
$ docker build -f deploy/php/Dockerfile -t mini-php . --no-cache

nginxコンテナをビルドする
$ docker build -f deploy/nginx/Dockerfile -t mini-nginx . --no-cache

aws phpコンテナpush
$ aws lightsail push-container-image --region ap-northeast-1 --service-name laravel-mini --image mini-php --label mini-php 

awsにnginxをpush
$ aws lightsail push-container-image --region ap-northeast-1 --service-name laravel-mini --image mini-nginx --label mini-nginx
