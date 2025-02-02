# 🚀 GitHub & Flutter 개발 시작하기

안녕하세요! GitHub와 Flutter 개발을 처음 시작하시는 분들을 위한 가이드입니다. 이 문서를 통해 기본적인 Git 사용법과 Flutter 버전 관리 방법을 배워보세요.

## 📌 시작하기 전에 준비할 것들

1. [Git 설치하기](https://git-scm.com/downloads)
2. [GitHub 계정 만들기](https://github.com)
3. 개발 도구 설치
    - Flutter 개발: Android Studio 설치
    - 일반 개발: VS Code 설치 (선택사항)

## 🔍 GitHub 기본 용어 설명

- **Repository (저장소)**: 프로젝트의 모든 파일과 히스토리가 저장되는 공간
- **Clone (클론)**: 원격 저장소를 내 컴퓨터로 복사하는 작업
- **Commit (커밋)**: 변경사항을 저장하는 작업
- **Push (푸시)**: 내 컴퓨터의 변경사항을 GitHub에 업로드
- **Pull (풀)**: GitHub의 변경사항을 내 컴퓨터로 다운로드

## 💻 개발 환경 설정하기

### FVM (Flutter Version Management) 설치

Windows:
```bash
dart pub global activate fvm
```

macOS:
```bash
brew tap leoafarias/fvm
brew install fvm
```

### Flutter 설치 및 설정
```bash
# Flutter 3.24.5 설치
fvm install 3.24.5

# 설치된 버전 확인
fvm list
```

## ✨ 자주 사용하는 명령어

### Git 명령어
```bash
# 변경사항 확인
git status

# 변경사항 스테이징
git add .

# 변경사항 커밋
git commit -m "커밋 메시지"

# GitHub에 업로드
git push

# GitHub에서 최신 변경사항 가져오기
git pull
```

### Flutter & FVM 명령어
```bash
# 프로젝트 실행
fvm flutter run

# 패키지 설치
fvm flutter pub get

# 프로젝트 빌드
fvm flutter build

# 빌드 캐시 정리
fvm flutter clean
```

## 🚫 자주 발생하는 문제와 해결방법

### GitHub 관련

1. **권한 오류가 발생할 때**
    - GitHub 계정 정보가 정확한지 확인하세요
    - repository 접근 권한이 있는지 확인하세요

2. **충돌(Conflict)이 발생할 때**
    - 같은 파일이 다른 사람에 의해 수정되었을 수 있습니다
    - 변경사항을 확인하고 수동으로 병합해야 합니다

3. **push가 거절될 때**
    - 먼저 `git pull`로 최신 변경사항을 가져온 후 다시 시도하세요

### Flutter & FVM 관련

1. **VS Code에서 Flutter SDK를 찾지 못할 때**
   `.vscode/settings.json` 파일에 추가:
   ```json
   {
     "dart.flutterSdkPath": ".fvm/flutter_sdk"
   }
   ```

2. **Android Studio에서 SDK 문제 발생 시**
    - Preferences > Languages & Frameworks > Flutter
    - Flutter SDK 경로를 `.fvm/flutter_sdk`로 설정
    - 안드로이드 스튜디오에서 먼저 fvm install을 한 경우는 별도 설정이 필요 없습니다

## 💡 유용한 팁

- 커밋 메시지는 명확하고 구체적으로 작성하세요
- 큰 변경사항은 작은 단위로 나누어 커밋하세요
- `.gitignore` 파일을 활용해 불필요한 파일은 제외하세요
- Flutter 프로젝트에서는 버전 충돌을 피하기 위해 FVM 사용을 권장합니다
- 문제가 생겼을 때는 당황하지 마세요! Google과 Stack Overflow에서 많은 해결책을 찾을 수 있습니다

## 🔗 더 알아보기

- [Git 공식 문서](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com)
- [Flutter 공식 문서](https://flutter.dev/docs)
- [FVM 공식 GitHub](https://github.com/leoafarias/fvm)

## ❓ 도움이 필요하신가요?

문제가 발생하거나 추가 질문이 있으시다면 언제든 Issue를 생성해주세요. 커뮤니티와 함께 해결방법을 찾아보겠습니다!

---
⭐ 이 가이드가 도움이 되었다면 Star를 눌러주세요!