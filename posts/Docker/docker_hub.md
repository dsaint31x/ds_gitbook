# Docker hub 이용.

## 로그인

* [docker hub](https://hub.docker.com/)의 계정으로 로그인.
* example
```
docker login
```

## Docker hub에 업로드

* `push` 명령어를 이용하여 이미지를 업로드.
* 해당 이미지의 이름은 다음과 같이 지정함. (docker hub의 아이디를 기재)
  * `docker_hub_id`/`image_name:tag`
  * `docker list`에서 `REPOSITORY`에 해당하는 항목에 해당.
* 이미 commit 된 image들이 docker hub에 push됨.
* example
```
docker push dsaint31x/ds_debian:190708
```

## Docker hub에서 다운로드

* `pull` 명령어를 이용하여 이미지를 다운로드.
* example
```
docker pull dsaint31x/ds_debian:190708
```

## Docker hub에서 image 검색하기

* `search` 등의 하위 명령이 dockerhub에서 image를 검색하는데 사용됨.
* `NAME` 항목에서 `docker_hub_id/image_name` 의 형태로 보임.
* `TAG` 는 기본적으로 docker command에서 확인하지 못함.
  * docker hub에서 `TAG`정보를 확인 가능함.
  * 특별히 지정하지 않으면(`:TAG`), `latest`가 됨.
  
## References

* [DockerHub 사용하기::아리수](https://arisu1000.tistory.com/27802)