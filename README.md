# Dev Notes

## 2024.03.18

### 1일차

- Next App 생성
- Readme 세팅
- shadcn/ui, Zod, React Hook Form 학습

### TIL

**shadcn/ui**

- NextUI, MUI를 활용해본적 있다. UI 컴포넌트 요소를 빠르게 제작할 수 있지만, 라이브러리로 제공되며 프로젝트를 무겁게 만들고, 커스텀하기 어렵다는 단점이 있었다. 특히 색을 변경하거나 원하는 형태로 가공하기 어려웠다.
- shadcn/ui는 Radix, Tailwind CSS로 만들어진 재사용 가능한 컴포넌트를 제공한다. 종속성으로 설치하지 않으며 필요한 구성 요소를 직접 선택할 수 있다.
- Radix UI는 커스텀하기 쉽다. 기본 동작은 내부적으로 처리하고 있고, 스타일은 개별 지정할 수 있으며, Compound Component Pattern으로 유연성을 지닌다. 기본 HTML 구조에 접근성도 좋다. 이런 형태를 Headless UI라고 부른다.
- 필요한 구성 요소를 선택하고 코드를 복사하여 프로젝트에 붙여넣어 사용한다. 온전히 사용자가 컨트롤할 수 있다.
- 해당 코드들을 뜯어보며 난이도 높은 코딩을 간접적으로 경험할 수 있으며, Tailwind도 더 복잡하게 쓰여진 부분들을 보며 배울 수 있다.

**Zod**

- 스키마 선언 및 유효성 검사 라이브러리.
- TypeScript는 컴파일 시점에서의 타입에러만 잡아낼 수 있고 런타임 단계에서의 타입에러는 잡지 못한다. 런타임에서 작동되는 것은 JavaScript이기 때문이다.
- 스키마(schema)는 형태 , 모양 , 계획을 의미 하는 그리스어 skhēma에서 유래되었다. 데이터의 형태 및 구조라고 볼 수 있다.
- zod를 통해 객체 형식으로 나타내고, parse를 통해 유효성 검증을 진행한다. 정상적으로 통과하면 입력값을 return, 잘못된 값이 들어가면 error를 throw한다. safeParse라는 기능도 존재한다.
- 스키마를 기준으로 타입 추론이 가능하다. 따라서 타입을 따로 작성할 필요가 없어진다.
- 종속성이 없고, 적은 용량이며, 간결한 인터페이스를 제공한다.

**React Hook Form**

- 비제어 컴포넌트 방식으로 form 을 관리하고 개발
  - 기존 제어 컴포넌트로 폼을 다루기 위해서는 하나하나 state를 선언해주고, 핸들링 함수를 만들고, 에러를 위한 state, 또 검증을 위한 함수 등 모든 유효성 검증을 한다면 코드가 매우 길어질 것이다. 그리고 컴포넌트 리렌더링이 발생하는 조건 중 하나는 state의 값의 변화이다. 모든 값이 state로 연결되어 있다면 무수히 많은 리렌더링이 발생한다.
- react-hook-form을 활용하는 데 여러가지 configuration 옵션이 들어갈 수 있다. 그 중 mode와 defaultValues를 가장 많이 활용한다.
  - mode 옵션은 validation 전략을 설장하는 데 활용한다. onSubmit, onChange, onBlur, all 등의 옵션이 있다. 주의해야 할 점은 mode를 onChange에 놨을 때 다수의 리렌더링이 발생할 수 있어 성능에 영향을 끼칠 수 있다.
  - defaultValues 옵션은 form에 기본 값을 제공하는 옵션이다. 주의해야 할 점은 react-hook-form을 사용할 때 기본값을 제공하지 않는 경우 input의 초기값은 undefined로 관리된다.
- state 를 최소화 함으로써 state 로 부터 야기되는 버그 최소화
  - 라이브러리에 의존성을 부여했기 때문에 직접 다뤄야 하는 로직은 줄고 개발 경험을 높일 수 있다. 또한 비제어 컴포넌트를 통해 폼을 다루기 때문에 기존에 input 태그를 다루기 위해 선언했던 state가 없어지고 컴포넌트가 관리해야 하는 state 수도 적어졌다. 이로 인해서 컴포넌트의 렌더링 횟수도 최소화할 수 있다.
- 우리끼리만 아는 스펙의 최소화
  - 기존에 제어 컴포넌트를 다루기 위해 form을 직접 구현해서 활용했다. 이는 우리끼리만 아는 스펙이 생기는 것인데, 만약 문서화가 잘 되어있지 않거나 기존에 만들었던 사람이 퇴사하는 경우엔 다음 개발자가 이를 활용하는데 어려움이 있다는 단점이 있다. react-hook-form를 활용하면 다른 개발자가 우리의 프로젝트의 유지보수를 하더라도 큰 어려움 없이 할 수 있게 된다.
- 직관적인 코드
  - 직관적으로 폼을 다룸으로써 어떤 state 혹은 함수를 사용해 폼을 구현하는 것이 아닌, form 자체를 직접 다룸으로써 개발을 더욱 직관적으로 편리하게 할 수 있다.

## 2024.03.19

### 2일차

- 예제 코드 Clone
- 코드를 살펴보며 회원가입/로그인 개발 준비하기

### TIL

**Next.js Page Router**

- 기존 프로젝트를 진행할 때 App Router를 주로 다뤄서 Page Router의 이해가 부족했다. 이번 기회에 Page Router를 제대로 익힐 수 있었다.

**pages/index.tsx**

- react-hook-form의 useForm을 활용한 코드를 살펴봤다.
- form.watch()를 통해 작성한 form 정보를 확인할 수 있다.
- alert(JSON.stringify(data, null, 4))
  - JSON.stringify의 옵션에 대해서 살펴보았다.
  - value(필수) : JSON 문자열로 변환할 값
  - replacer(선택) : 함수 또는 배열이 될 수 있다. 이 값이 null 이거나 제공되지 않으면, 객체의 모든 속성들이 JSON 문자열 결과에 포함된다.
  - space(선택) : 가독성을 목적으로 JSON 문자열 출력에 공백을 삽입하는 데 사용되는데, string이나 number 객체가 될 수 있다. 이 값이 null 이거나, 제공되지 않으면 공백이 사용되지 않는다.
- motion.div에서 step 값에 따른 animate(translateX) 변화로 슬라이드 애니메이션 구현
- Button에서 step 값에 따라 hidden 처리
- form.trigger를 활용한 유효성 검사 실패했을 때 오류 문구 출력

  - 빨간색 문구와 아래 오류 문구 출력 원리를 정확히 파악하지 못했다.

**validators/auth.ts**

- zod를 활용한 유효성 검사를 살펴보았다. registerSchema를 선언하고 z.object 안에 각 요소의 유효성 조건이 정의되어 있다.
- 기존 유효성 검사를 할 때 매우 긴 코드로 인해서 관리하기 힘들었는데, zod를 활용하니까 한 눈에 파악이 가능하고 min, max, refine 등 조건을 설정하는 것도 수월하다. 그리고 에러 메시지도 바로 작성할 수 있다.

**components/ui**

- button, card, input 등 다양한 컴포넌트가 있다.
- 공통 컴포넌트를 간단하게만 제작해서 사용해봤는데, 예제 코드처럼 깊게 만들어보진 못했다.
- cva, tailwindmerge, clsx 등을 조합하여 재사용 가능한 UI 제작하는 방법을 더 학습해야겠다.

test2
