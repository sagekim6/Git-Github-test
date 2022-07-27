# 원격 저장소의 모든 커밋 히스토리 삭제하기

- open api를 가져와 사용하던 중 api key가 노출되면 안된다는 사실을 알고 일단 급하게 레포지토리를 private으로 바꿨었다.  
  api key를 따로 key.js 파일로 만들어 export 시키고 .gitignore 파일에 추가시키긴 했지만 원격 저장소에는 이미 커밋 히스토리에 api key가 남아있어서 히스토리를 아예 다 지우고 다시 api key를 보호해서 올리고 싶었다.

## `Orphan Branch` 만들기

- `Orphan Branch`는 다른 브랜치와 다르게 하나의 독립적인 브랜치로 다른 브랜치나 커밋으로 아예 단절된 브랜치를 말한다.

  `git checkout --orphan [브랜치 이름]`

  위 명령어로 orphan 브랜치를 생성하면 기존의 파일들이 staged된 상태로 새로운 독립적인 브랜치가 만들 수 있다.

그 후 원래 있던 `master` 브랜치는 삭제해준다. &rarr; `git branch -D master`

## `git branch -m [브랜치명]` 브랜치 이름 바꾸기

- `git branch -m [브랜치명]`에서 `-m`은 move/rename의 약자로 브랜치 이름을 바꿀 수 있다.
- `orphan` 브랜치의 이름을 `main`으로 바꿔준 뒤 `git push -f origin main` 원격 저장소에 강제로 push 해준다.

### + 레포지토리 default 저장소를 main으로 바꾸고 master 브랜치는 아예 삭제해주기!
