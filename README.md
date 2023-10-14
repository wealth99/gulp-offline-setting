# yarn install offline

---

## 1. 사용하는 패키지 설치 (yarn add)

```
$ yarn add gulp --dev
$ yarn add gulp-autoprefixer --dev
...
```

## 2. 프로젝트 홈 경로에 .yarnrc 파일 생성

```
// .yarnrc
yarn-offline-mirror "./npm_packages"
yarn-offline-mirror-pruning true
```

- yarn-offline-mirror: 압축된 .tgz 파일들이 들어갈 폴더
- yarn-offline-mirror-pruning: 업데이트 된 패키지 추가 시 yarn cache를 먼저 확인하고 여기에 없는 dependency를 가져옴

## 3. node_modules와 yarn.lock 파일 삭제

## 4. 캐시 삭제

```
$ yarn cache clean
```

## 5. 패키지 받아오기

```
$ yarn install
```

yarn install을 실행하면 /npm_packages 폴더가 생성되면서 \*.tgz파일들이 저장되고새로운 yarn.lock 파일이 생성된다.

완료 되었으면 node_modules 를 제외하고, npm_packages, .yarnrc, yarn.lock, package.json, 작성한 파일들을 가져가면 된다.

내부망에 yarn과 node.js가 설치되어 있지 않다면 설치파일을 가지고 가서 따로 설치해줘야 한다.

## 6. 오프라인 환경 설치

```
$  yarn install --offline
```

만약 패키지가 추가된다면 node_modules, npm_packages, yarn.lock 파일 삭제하고

```
$ yarn install
```

패키지를 yarn install 로 다시 패킹한 다음에 새로 만든 파일들을 담은 후

```
$ yarn install --offline
```

다시 설치하여 사용하면 된다.
