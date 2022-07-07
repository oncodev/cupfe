# CUP FE 작업 계획

1. next.js, TS, SCSS 프로젝트 생성 (하위폴더 없이 설치)
  yarn create next-app --typescript .
  yarn add scss

2. storybook cli 로 추가
  npx -p @storybook/cli sb init --type react
  yarn storybook
  https://localhost:6006

3. .storybook/main.js 에서 모듈 추가
  "addons": [
    "@storybook/addon-designs",
  ]

4. Figma 파일 만들고 추가할 버튼 프레임 선택해서 copy link로 URL 복사
  https://www.figma.com/file/lGYeZoaiM1pDzWxHBvqiXa/oncofe?node-id=2%3A7

5. Button.stories.tsx
```
  // 1. withDesign import
  import { withDesign } from 'storybook-addon-designs';

  // 2. Decorator 추가
  export default {
    title: 'Example/Button',
    component: Button,
    // More on argTypes: https://storybook.js.org/docs/react/api/argtypes
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
  button/
    button.css
    Button.stories.tsx
    Button.tsx

---

# Initialize server

