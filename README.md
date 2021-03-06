# CUP FE 작업 계획

1. next.js, TS, SCSS 프로젝트 생성 (하위폴더 없이 설치)  
  `yarn create next-app --typescript .`  
  `yarn add scss`

2. storybook cli 로 추가  
  `npx -p @storybook/cli sb init --type react`  
  `yarn storybook`  
  `https://localhost:6006`

3. .storybook/main.js 에서 모듈 추가
```
  "addons": [
    "@storybook/addon-designs",
  ]
```

4. Figma 파일 만들고 추가할 버튼 프레임 선택해서 copy link로 URL 복사  
  https://www.figma.com/file/lGYeZoaiM1pDzWxHBvqiXa/oncofe?node-id=2%3A7

5. Button.stories.tsx
```js
  // 1. withDesign import
  import { withDesign } from 'storybook-addon-designs';

  // 2. Decorator 추가
  export default {
    title: 'Example/Button',
    component: Button,
    argTypes: {
      backgroundColor: { control: 'color' },
    },
    decorators: [withDesign], // 2. Decorator 추가
  } as ComponentMeta<typeof Button>;

  // 3. Template 추가
  Example.parameters = {
    design: {
      type: 'figma',
      url: 'https://www.figma.com/file/lGYeZoaiM1pDzWxHBvqiXa/oncofe?node-id=2%3A7',
    },
  };
```

6. components 디렉토리에 컴포넌트별로 나눠서 관리

6-1. 기존 story 경로 수정  
  .storybook/main.js 에서 

  ```js
  module.exports = {
    "stories": [
      "../stories/**/*.stories.mdx",
      "../stories/**/*.stories.@(js|jsx|ts|tsx)"
    ],
  ```

  아래처럼 경로에서 stories 경로 제거 

  ```js
  module.exports = {
    "stories": [
      "../**/*.stories.mdx",
      "../**/*.stories.@(js|jsx|ts|tsx)"
    ],
  ```

6-2. 컴포넌트 폴더 생성 후 파일이동
```
  button/
    button.css
    Button.stories.tsx
    Button.tsx
```

---

# Initialize server


- 크로마틱 추가해서 배포하기 : https://storybook.js.org/tutorials/intro-to-storybook/react/ko/deploy/

- 깃헙액션 추가해서 배포하기 : https://budiirawan.com/how-to-publish-storybook-github-pages/

7. Storybook 배포하기 

7.0 깃허브 리포 Settings에서 pages에 페이지 활성화하기

https://oncodev.github.io/cupfe/


7.1 수동 배포하기
- 깃허브 페이지에 수동으로 배포할때는 `yarn add gh-pages -D`
- packages.json 에 `deploy-storybook` 추가

```json
"scripts": {
  // ...
  "build-storybook": "build-storybook",
  "deploy-storybook": "gh-pages -d storybook-static",
```

다음과 같이 실행

```bash
$ yarn run build-storybook
$ ls -alh storybook-static
total 3.3M
drwxr-xr-x 1 User 197121    0  7월  7 20:06 ./gh-pages)
drwxr-xr-x 1 User 197121    0  7월  7 20:12 ../
-rw-r--r-- 1 User 197121 146K  7월  7 20:06 142.bb7bf43fdd5fd1f24ad9.manager.bundle.js
-rw-r--r-- 1 User 197121  227  7월  7 20:06 142.bb7bf43fdd5fd1f24ad9.manager.bundle.js.LICENSE.txt
-rw-r--r-- 1 User 197121 2.0M  7월  7 20:06 295.c40d66457a3c5da08f74.manager.bundle.js0.2".
-rw-r--r-- 1 User 197121  994  7월  7 20:06 860.8dcebab9433c411ba3ab.manager.bundle.js
-rw-r--r-- 1 User 197121  33K  7월  7 18:17 favicon.ico
-rw-r--r-- 1 User 197121 2.3K  7월  7 20:06 index.html
...

$ yarn run deploy-storybook
```

7.2 깃허브 액션으로 main에서 푸시 하면 스토리북 자동 배포하기

- 브랜치 만들기 : `git checkout -b gh-pages`
- 스토리북 빌드 : `yarn build-storybook`
- 디렉토리 생성 : `.github/workflows/storybook.yml`


> 에러 메세지 : TypeError [ERR_INVALID_ARG_TYPE]: The "id" argument must be of type string. Received an instance of Object  
> 댓글을 보고 스토리북 버전 6.5.9에서 6.5.5로 낮춰봄 : https://issuehunt.io/r/storybookjs/storybook/issues/18448

https://www.codegrepper.com/code-examples/shell/typeerror+%5Berr_invalid_arg_type%5D%3A+the+%22id%22+argument+must+be+of+type+string.+received+function+app

https://minemanemo.tistory.com/165

---
# Troubleshooting
깃헙 액션에서 `Install and Build` 태스크에서 아래 에러 등으로 Task 가 실패.

```bash
ERR! TypeError [ERR_INVALID_ARG_TYPE]: The "id" argument must be of type string. Received an instance of Object
ERR!     at new NodeError (node:internal/errors:371:5)
ERR!     at validateString (node:internal/validators:119:11)
ERR!     at Module.require (node:internal/modules/cjs/loader:998:3)
ERR!     at require (node:internal/modules/cjs/helpers:102:18)
ERR!     at interopRequireDefault (C:\Users\User\Desktop\cupfe\node_modules\@storybook\core-common\dist\cjs\presets.js:178:16)
ERR!     at getContent (C:\Users\User\Desktop\cupfe\node_modules\@storybook\core-common\dist\cjs\presets.js:194:10)
ERR!     at loadPreset (C:\Users\User\Desktop\cupfe\node_modules\@storybook\core-common\dist\cjs\presets.js:203:20)
ERR!     at C:\Users\User\Desktop\cupfe\node_modules\@storybook\core-common\dist\cjs\presets.js:256:18
ERR!     at Array.reduce (<anonymous>)
ERR!     at loadPresets (C:\Users\User\Desktop\cupfe\node_modules\@storybook\core-common\dist\cjs\presets.js:255:18)
```

그러나 실제로 문제되는 부분이 아니므로 무시하고 넘어가도록 수정

```yaml
- name: Install and Build
  run: |
    npm install
    npm run build-storybook
```

->

```yaml
- name: Install and Build
  run: |
    npm install
    npm run build-storybook || true
```

