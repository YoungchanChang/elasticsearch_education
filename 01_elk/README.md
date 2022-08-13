# mac에 도커 설치
> https://docs.docker.com/desktop/install/mac-install/


# Docker-compose로 여러개 띄우기
> https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html

# 도커 인증서 복사하는 명령어
$ docker cp 01_elk_es01_1:/usr/share/elasticsearch/config/certs/ca/ca.crt .

# 로그스태시 명령어
user@users-MacBook-Air logstash-8.3.2 % bin/logstash -f config/logstash-tmdb.conf