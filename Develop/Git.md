## git

1. 브랜칭전략

- git flow
  - master: 제품 배포 브랜치입니다
  - develop : 개발 브랜치로 개발자들이 이 브랜치를 기준으로 각자 작업한 기능들을 합(Merge)칩니다.
  - feature : 단위 기능을 개발하는 브랜치로 기능 개발이 완료되면 develop 브랜치에 합칩니다.
  - release : 배포를 위해 master 브랜치로 보내기 전에 먼저 QA(품질검사)를 하기위한 브랜치 입니다.
  - hotfix : master 브랜치로 배포를 했는데 버그가 생겼을 떄 긴급 수정하는 브랜치 입니다.
- develop - feature 브렌치간 머지 : Squash and Merge가 유용합니다. 일반적으로 머지 후에 feature 브렌치를 삭제해버리는 점을 떠올려 보면, feature 브렌치의 커밋 히스토리를 모두 develop 브렌치에 직접 연관 지어 남길 필요가 없습니다.
- master - develop 브렌치간 머지 : Rebase and Merge가 유용합니다. develop의 내용을 master에 추가할 때에는 별도의 새로운 커밋을 생성할 이유가 없기 때문입니다.
- hotfix - develop, hotfix - master 브렌치간 머지 : Merge 또는 Squash and Merge 모두 유용합니다.

2. rebase와 merge 비교: 커밋 메시지 기준

- Merge는 branch를 통합하는 것이고, Rebase는 branch의 base를 옮긴다는 개념의 차이가 있습니다.
- rebase를 하고 merge할 경우 커밋 히스토리가 깔끔해진다.
