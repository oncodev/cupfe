# CUP FE 작업 계획

1. next.js, TS, SCSS 프로젝트 생성
  yarn create next-app --typescript
  yarn add scss
2. storybook cli 로 
  

이거 하위폴더 안만들고 그냥  설치하는방법은 없나요 ㅜㅜ 예전에도 못찾았어요 ㄷㄷ
yarn create next-app --typescript . 하면 될거에요.

혹시 제꺼 터미널도 보이시나요ㄷㄷ 네 보여요!

앗 README.md 겹쳐서...
뭐지 파일이 아무 것도 없어야 되나
으ㅡ음......
타입스크립트가 문제인걸까요..

일단 이 파일을 밖으로 빼버리죠.
mv README2.md ..
베리 나이스...
보여요!

혹시 3000번 포트 같은 화면 보이시나요!?
아 이거 저번에 공유했어서 지금도 공유되나보...는...군요 아닌가... 아!! 좋아요!!
네 보여요! 띄울 때 저한테 볼거냐고 팝업 뜨더라구요 신기해요

바뀐것도 보이시나요 바로 변경되나용 좋아요!!! 스토리북을 그럼 먼저 추가해볼게요 만든지 3년은 된거같은데...
감사합니다!!!
네 바로 보여요 

npx -p @storybook/cli sb init --type react

yarn storybook

https://localhost:6006

페이지 바로 뜨시나요 아맞다 
아 저번에 3000은 추가해둬서 있는데 6006은 추가 안해서 없는거였군요! 
죠아요오오오
이제 그럼....
피그마...를... 한번도 연결 안해봤어요


6006 추가해주세요오
스토리북 떠요!

addon을 추가하면 될까요 ㄷㄷ 
yarn add -D storybook-addon-designs

네 해보죠!

혹시 그냥 README.md 파일도 보이시나요??

네 보여요. 거기로 옮길까요! 거기에 순서를 적고있어요

이거를 하려는데 그럼 파일을 먼저 만들어야하는거 맞죠
https://storybook.js.org/docs/react/sharing/design-integrations#link-figma-components-to-stories


Button 컴포넌트를 수정해볼까요?  네!!!

이미 있는거...

음.... 버튼...을... 버튼에 추가하는건가요!?
컴포넌트를 만든 다음에 추가하...는거 맞겠죠...

    Embed a file or prototype, click the "Share" button to generate a unique URL for the file then click "Copy link". <- 완료했어요

    Embed a component or frame check "Link to selected frame" in the Share dialog. Or right click on the frame and go to "Copy/Paste as" » "Copy link".

아 프레임 선택해서

버튼을 하나 만들고 복사했어요
https://www.figma.com/file/lGYeZoaiM1pDzWxHBvqiXa/oncofe?node-id=2%3A7


Button.stories.tsx 에 한번 추가해볼께요.

버튼이 사라졌어요...!
Design Tab이 떠야된다는데 안보이네요 으으음

혹시 storybook 한번 껏다 켜주실 수...
왜 탭이 흠...

탭 나왔어요!

밸류를 추가했는데 예제에는 왜 밸류가 없는지 몰라요 ㄷㄷ

근데 상태가 이상해요 ㄷㄷ
와 어떻게 하셨어요

values로 추가는 되었는데 라지로 들어가면 화면이 안나오고 그래요 ㅜㅜ
예제에는 밸류 추가가 없어서... 다른 방법으로 해야하나봐요

음 예제ㅔㅇ 있는 피그마 주소로 하니 나오네요.
오 그러게요!!!!


오 그러면 음음음음음음음음음으믕므

그..근데 예제에 있는건 왜되는거지?!
주소가 조금 다른거같아요
프레임 선택하면 프레임마다 나오는데
용진님 통화로해도 되나요

네네 근데 집이신거에요? @.@ 아 그럴리가 없구나 회사컴.. 어 저두 잠시만... 다녀왔어요. 앗 마이크 저 그럼 잠시만요

잠시만요 장실좀다녀올게요...

저두요!

링크 공유할게요 잠시만요

https://meet.google.com/zgn-yajt-dhk

아아아
저
이거 구글밋으로 했어요 여기는 데탑 소리가 안나서

제말 안들리시나요 ㄷㄷ 전 들려요

왜 안 들리죠 ㅠㅠㅠ전 폰으로 접속했어요..



fi다시 접속해볼께요.