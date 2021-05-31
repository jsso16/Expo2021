# Expo2021 - 201930231 전소진
Expo CLI 2021

## 5월 28일
> Expo CLI

**0. Expo란?**
- Expo는 React 애플리케이션을 위한 프레임워크이자 플랫폼이다.<br>
https://docs.expo.io/

**1. Expo VS React Native CLI**
- Expo의 특징
```
[장점]
- 쉬운 build system을 지니고 있다.
- Android Studio, Xcode 없이도 Expo SDK를 이용해 빌드 및 테스트가 가능하다.
- expo 앱을 이용하면 자신의 스마트폰애서 직접 결과 확인이 가능하다.
- MacBook 없이도 iOS 환경도 빌드가 가능하다.
- 카메라, 위치, 알림, 센서 등에 접근할 수 있는 라이브러리가 존재한다.
- 언제든지 React Native CLI로 변환이 가능하다.
[단점]
- 상대적으로 업데이트가 느리다.
- native 환경에서 사용하는 third party 라이브러리를 사용할 수 없다는 한계가 있다.
```
- React Native CLI의 특징
```
[장점]
- RN 개발진들이 운영하고 있어서 업데이트가 빠르다.
- native 언어인 Java, Kotlin과 Swift를 사용할 수 있다.
[단점]
- 안드로이드는 Android Studio, iOS는 Xcode가 있어야 한다.
```

**2. Expo CLI 설치하기**
- Expo CLI를 설치하기 위해서는 아래의 명령어를 실행해주어야 한다.
- 이때 -g 옵션은 global 옵션이므로 반드시 사용해야 한다.
```
npm install -g expo-cli
```
- 설치가 완료되면 정상적으로 설치되었는지 확인하기 위해 아래의 명령어를 실행한다.
```
expo --version
```

**3. 프로젝트 생성하기**
- 작업할 폴더에서 아래의 명령을 실행하면 자동으로 프로젝트 폴더가 생성된다.
```
expo init [project name]
```
- 프로젝트를 생성하면 방향키로 템플릿을 선택할 수 있는데, TypeScript 사용이 익숙하지 않다면 blank를 선택한다.

**4. App 실행하기**
- 생성한 디렉토리로 이동하여 아래의 명령을 통해 expo를 실행한다.
```
expo start
```
- expo가 실행되면 아래 사진의 사이트로 접속된다.
<img width="810" alt="expo web" src="https://user-images.githubusercontent.com/62285642/120213622-60228c00-c26e-11eb-86d8-fadeb2029617.png">

**5. 터미널 메뉴 알아보기**
- 터미널에도 아래 사진과 같은 화면이 출력된다.
- 다양한 동작들 중 w를 선택하면 브라우저에서 App 화면을 출력할 수 있으며, 이 외에도 다양한 기기에서 App 화면을 출력할 수 있다.
<img width="636" alt="terminal" src="https://user-images.githubusercontent.com/62285642/120213545-4b45f880-c26e-11eb-9061-2f9066847d3b.png">

**6. QR코드를 이용해서 스마트폰에서 화면 실행하기**
- Play Store에서 "expo"를 검색하여 설치한 후, QR코드를 이용하여 본인의 폰에서도 화면을 출력할 수 있다.
- 단, 화면을 정상적으로 출력하기 위해서는 같은 네트워크 상에 있어야 한다.

**7. Expo로 React Navigation 앱 만들기**
- Expo를 이용하여 React Navigation의 createMaterialBottomTabNavigator를 만들 수 있다.
- material-design 테마인 React Native Paper는 React 네비게이션을 네이티브처럼 보이게 하기 위해서 사용하는 Material Design 라이브러리이다.<br>
https://reactnativepaper.com/
- React Native Paper 라이브러리는 아래의 명령어를 통해 설치할 수 있다.
```
npm install @react-navigation/material-bottom-tabs react-native-paper
```
- MaterialBottomTabNavigator에서 React Native Paper의 사용 방법
```jsx
import * as React from 'react'
import { BottomNavigation, Text } from 'react-native-paper'

const MusicRoute = () => <Text>Music</Text>;

const AlbumsRoute = () => <Text>Albums</Text>;

const RecentsRoute = () => <Text>Recents</Text>;

const MyComponent = () => {
  const [index, setIndex] = React.useState(0);
  const [routes] = React.useState([
    { key: 'music', title: 'Music', icon: 'queue-music' },
    { key: 'albums', title: 'Albums', icon: 'album' },
    { key: 'recents', title: 'Recents', icon: 'history' },
  ]);

  const renderScene = BottomNavigation.SceneMap({
    music: MusicRoute,
    albums: AlbumsRoute,
    recents: RecentsRoute,
  });

  return (
    <BottomNavigation
      navigationState={{ index, routes }}
      onIndexChange={setIndex}
      renderScene={renderScene}
    />
  );
};

export default MyComponent
```