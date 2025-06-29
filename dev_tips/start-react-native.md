---
title: "React Native 시작하기"
layout: post
date: 2025-06-24
author: pear27
tags: [ReactNative]
---

React Native를 활용한 모바일 애플리케이션 개발에 앞서,
본격적인 개발과 배포에 들어가기 전 필요한 사전 작업들을 정리해보았습니다.

---

### 🧰 1. Software Requirements

1. **Node.js 설치 확인** (`2025-06-24` 기준)
    
    설치된 **Node.js** 버전이 `v18` 미만인 경우, `ReadableStream`을 기본적으로 제공하지 않아 프로젝트가 실행되지 않습니다.

    원활한 사용을 위해 `v22.16.0`의 **Node.js**를 설치합니다. CMD를 **관리자 모드**로 실행한 뒤, 아래 명령어를 입력합니다.
    ```bash
    nvm install 22.16.0
    nvm use 22.16.0
    ```
    정상적으로 설정이 완료되면 아래 명령어로 버전을 확인할 수 있습니다.
    ```bash
    node -v
     # v22.16.0
    npm -v
     # 10.2.4
    ```

2. **Expo 설치하기**

    **Expo**는 React Native로 개발한 모바일 어플리케이션을 미리 실행하고 테스트할 수 있는 오픈 소스 플랫폼입니다. JavaScript 코드와 Markup/Styling 작성 후 바로 앱을 테스트해 볼 수 있습니다. 

    CMD에서 아래 명령어를 입력하여 **Expo**를 설치합니다. 
   ```bash
   npm install --global expo-cli         
        # Install the command line tools
    ```

    MAC 사용자의 경우: **watchman** 설치
    ```bash
    $ brew update
    $ brew install watchman
    ``` 

    테스트할 모바일 기기(Android/IOS)에 **Expo**(혹은 **Expo Go**)를 설치하고, 계정을 생성합니다. 

---

### 📦 2. Creating the App

1. **새 프로젝트 만들기**

    CMD에서 아래 명령어를 입력하여 새 프로젝트 폴더를 생성합니다. 

    ```bash 
    expo init my-project
        # 프로젝트명은 my-project
    ```
    위 내용을 입력하면 설치를 시작하기에 앞서 template을 선택할 수 있는데, 본 포스트에서는 첫 번째 옵션인 **blank**를 기준으로 합니다.

2. **프로젝트 실행하기**

    `expo login`

    **Expo** 모바일 어플리케이션에서 생성한 계정으로 로그인합니다. 

    `npm start` 
    
    프로젝트를 실행합니다.
    
    정상적으로 실행되는 경우 모바일 기기의 **Expo** 어플리케이션에서 현재 실행 중인 프로젝트를 확인할 수 있습니다. 

    아래와 같이 `App.js`에 기본값으로 작성된 내용이 화면에 나타납니다.

    ```bash
    Open up App.js to start working on your app!
    ```

    **React JS**를 사용할 때와 동일하게, 코드를 변경한 후 저장하면 바로 **Expo** 어플리케이션 화면에 반영됩니다.
---
### 💡 React Native 문법: React JS와의 차이점을 중심으로

  ```jsx
  <View>
      <Text>Open up App.js to start working on your app!</Text>
      <StatusBar style="auto" />
  </View>
  ```

  * `View` 태그: 모든 레이아웃 컨테이너로 사용됩니다.
  * `Text` 태그: 모든 텍스트 요소를 담을 때 사용됩니다. (`p`, `span` 등의 HTML 태그를 사용할 수 없습니다)

  ```js
  const styles = StyleSheet.create({
    container: {
        // 스타일 속성 정의
    },
  });
  ```
  * `StyleSheet` 객체: 코드 에디터에서 CSS 자동 완성 기능을 지원합니다. (필수X)
---