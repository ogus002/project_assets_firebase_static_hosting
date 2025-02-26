# Firebase Static Assets Hosting

이 프로젝트는 Firebase Hosting을 사용하여 정적 자산(이미지, JSON 파일 등)을 호스팅하고 외부에서 URL을 통해 접근할 수 있도록 설정한 예제입니다.

## 프로젝트 구조

```
project-root/
├── public/
│   ├── assets/
│   │   ├── images/
│   │   │   └── [이미지 파일들]
│   │   ├── data/
│   │   │   └── [JSON 파일들]
│   │   └── ...
│   └── index.html
├── firebase.json
├── .firebaserc
└── README.md
```

## 기능

- Firebase Hosting을 사용하여 정적 파일 호스팅
- `/assets` 경로를 통해 이미지, JSON 등의 리소스에 접근 가능
- 외부 애플리케이션에서 URL을 통한 리소스 접근 지원

## 설치 및 설정 방법

### 1. 사전 요구사항

- [Node.js](https://nodejs.org/) 설치
- Firebase 계정 및 프로젝트 생성
- Firebase CLI 설치
  ```bash
  npm install -g firebase-tools
  ```

### 2. 프로젝트 클론 및 설정

```bash
# 저장소 클론
git clone https://github.com/your-username/your-repository.git
cd your-repository

# Firebase에 로그인
firebase login

# Firebase 프로젝트 선택 또는 생성
firebase init hosting
```

### 3. 로컬 개발 서버 실행

```bash
firebase serve
```

### 4. 배포

```bash
firebase deploy
```

## 사용 방법

배포 후 다음과 같은 URL 패턴으로 자산에 접근할 수 있습니다:

```
https://your-project-id.web.app/assets/images/example.jpg
https://your-project-id.web.app/assets/data/config.json
```

## 외부 프로젝트에서 접근 방법

외부 프로젝트나 애플리케이션에서 호스팅된 자산에 접근하는 예제:

### HTML에서 사용

```html
<img src="https://your-project-id.web.app/assets/images/example.jpg" alt="Example Image">
```

### JavaScript에서 JSON 데이터 가져오기

```javascript
fetch('https://your-project-id.web.app/assets/data/config.json')
  .then(response => response.json())
  .then(data => {
    console.log(data);
  });
```

## CORS 설정 (필요한 경우)

다른 도메인에서 자산에 접근해야 하는 경우 CORS 설정이 필요할 수 있습니다. Firebase Hosting에서 `firebase.json` 파일에 다음과 같이 설정할 수 있습니다:

```json
{
  "hosting": {
    "public": "public",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ],
    "headers": [
      {
        "source": "/assets/**",
        "headers": [
          {
            "key": "Access-Control-Allow-Origin",
            "value": "*"
          }
        ]
      }
    ]
  }
}
```

## 기여 방법

1. 이 저장소를 포크합니다.
2. 새로운 기능 브랜치를 생성합니다 (`git checkout -b feature/amazing-feature`).
3. 변경사항을 커밋합니다 (`git commit -m 'Add some amazing feature'`).
4. 브랜치에 푸시합니다 (`git push origin feature/amazing-feature`).
5. Pull Request를 생성합니다.

## 라이센스

[MIT](LICENSE) 또는 여러분이 선택한 라이센스

## 연락처

프로젝트 관리자: [이름](mailto:ogus02@gmail.com)