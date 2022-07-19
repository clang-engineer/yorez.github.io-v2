---
layout  : wiki
title   : 깃헙을 데이터 저장소처럼 활용하기
summary : 
date    : 2022-07-19 11:35:32 +0900
updated : 2022-07-19 11:54:10 +0900
tags    : 
toc     : true
public  : true
parent  : [[git/index]]
latex   : false
---
* TOC
{:toc}

# 소개
Github에서는 Github REST API를 별도로 제공한다. \
이를 이용해서 Github에 올라와있는 파일들을 원격저장소처럼 접근할 수 있다.

공식 문서 가이드(https://docs.github.com/en/rest/repos/contents#get-repository-content) 

```txt
{
  "type": "file",
  "encoding": "base64",
  "size": 5362,
  "name": "README.md",
  "path": "README.md",
  "content": "encoded content ...",
  "sha": "3d21ec53a331a6f037a91c368710b99387d012c1",
  "url": "https://api.github.com/repos/octokit/octokit.rb/contents/README.md",
  "git_url": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/3d21ec53a331a6f037a91c368710b99387d012c1",
  "html_url": "https://github.com/octokit/octokit.rb/blob/master/README.md",
  "download_url": "https://raw.githubusercontent.com/octokit/octokit.rb/master/README.md",
  "_links": {
    "git": "https://api.github.com/repos/octokit/octokit.rb/git/blobs/3d21ec53a331a6f037a91c368710b99387d012c1",
    "self": "https://api.github.com/repos/octokit/octokit.rb/contents/README.md",
    "html": "https://github.com/octokit/octokit.rb/blob/master/README.md"
  }
}
```

"download_url" 부분의  "https://raw.githubusercontent.com/octokit/octokit.rb/master/README.md" 이 해당 파일을 다운로드 받을 수 있는 url

# 사용법
```txt
https://raw.githubusercontent.com/{owner}/{repo}/{branch}/{file_path}
```

- {owner} : 깃헛 소유자 ID
- {repo} : repository 이름
- {branch} : branch 이름
- {file_path} : 다운받을 파일 경로

## 파일 다운로드 예시
```sh
$ curl -O https://raw.githubusercontent.com/octokit/octokit.rb/master/README.md
```
