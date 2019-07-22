# Install gitbook-cli 

## Test Env.
* Ubuntu18.04

## NPM설치

```
sudo apt-get install npm
sudo npm install -g gitbook-cli
```

## Gitbook 초기화

기존에 github에서 관리되던 소스 있을 경우, 가져옴.
```
git clone https://github.com/dsaint31x/ds_gitbook.git
```

아래의 sh을 `publish-gitbook.sh`로 저장하고 수행 (초기화 및 github update까지 수행)
```
#!/bin/bash

# remove gitbook old things
rm -rf _book
rm -rf docs

# gitbook init
gitbook install && gitbook build

# build pages
mkdir docs
cp -R _book/* docs/
cp -R ds_temp/* docs/

# delete things
git clean -fx _book

# upload
git add .
git commit -a -m "update docs"
git push -u origin master
```

## Gitbook 로컬에서 수행.

편집된 내용 확인용이고, 서비스를 하려면 github page와 연동이 되어야 함.
```
gitbook serve
```

## Github page만들기.


## References

* (https://pinedance.github.io/blog/2018/10/04/build-eBook-with-gitbook-cli)
* (https://blog.chulgil.me/how-to-make-blog-using-github-5/)