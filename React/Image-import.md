# React에서 이미지 불러오기(import)

- 이미지 경로를 직접 작성하는 방법 <br />

html의 img 요소는 src 속성을 통해 이미지를 불러온다.

```javascript
function App() {
  return <img src="./assets/profile.png" alt="프로필 이미지" />;
}
```

이처럼 src에 이미지 경로를 문자열로 직접 작성하면 개발 환경에서는 이미지가 정상적으로 표시될 수 있다.

하지만 프로젝트를 빌드하고 배포할 때 문제가 발생할 수 있다.

React 프로젝트는 배포하기 전에 빌드 과정을 거친다. 이 과정에서 javascript와 css 등의 파일이 변환되고 최적화되며, 이미지와 같은 정적 파일도 빌드 도구의 설정에 따라 처리된다.

그런데 src에 일반 문자열로 작성한 경로는 빌드 도구가 이미지 파일의 의존성으로 인식하지 못할 수 있다. 이 경우 이미지가 최종 배포 파일에 포함되지 않거나 경로가 올바르게 처리되지 않아 배포 환경에서 이미지가 표시되지 않을 수 있다.

<br />

- import를 사용해 이미지 불러오기

이러한 문제를 방지하기 위해 이미지 파일을 import 키워드로 불러올 수 있다.

```javascript
import profileImage from "./assets/profile.png";

function App() {
  return <img src={profileImage} alt="프로필 이미지" />;
}
```

import를 사용하면 빌드 도구가 해당 이미지 파일을 프로젝트의 의존성으로 인식한다.

따라서 빌드 과정에서 이미지 파일을 함꼐 처리하고, 최종 배포 파일에 포함하거나 최적화된 경로로 연결할 수 있다.

이때 위 profileImage에는 **이미지 파일 자체가 들어가는 것이 아니라, 빌드 도구가 처리한 이미지의 URL 또는 경로가 담긴다.**

JSX에서는 중괄호 {}를 사용해 이 값을 동적으로 전달한다.

```javascript
<img src={profileImage} alt="프로필 이미지" />
```

<br />

- public 폴더를 사용하는 방법

프로젝트의 public 폴더에 이미지를 넣고 절대 경로로 접근하는 방법도 있습니다.

```javascript
public/
└── images/
    └── profile.png
```

```javascript
function App() {
  return <img src="/images/profile.png" alt="프로필 이미지" />;
}
```

public 폴더의 파일은 빌드 과정에서 일반적으로 그대로 배포 폴더에 복사된다. 따라서 별도의 import 없이 경로를 직접 작성해 사용할 수 있다.
