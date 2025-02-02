# Flutter 프로젝트 시작하기 (초보자용)
## SSH란?
SSH(Secure Shell)는 '보안이 강화된 셸'이라는 뜻으로, 1995년에 만들어진 네트워크 프로토콜입니다. 비유하자면 '디지털 신분증'과 같습니다.
쉽게 설명하면:
- 일반 비밀번호는 매번 입력해야 하고 해킹될 위험이 있지만,
- SSH는 한 번 설정하면 자동으로 안전하게 인증이 되는 방식입니다.
- 마치 건물에 들어갈 때 사원증을 찍으면 자동으로 출입이 되는 것과 비슷합니다.

## FVM이란?
FVM(Flutter Version Management)은 Flutter 버전 관리 도구입니다.
쉽게 설명하면:
- 여러 프로젝트에서 각각 다른 Flutter 버전을 사용해야 할 때 편리합니다.
- 예를 들어, A 프로젝트는 Flutter 2.0, B 프로젝트는 Flutter 3.0을 써야 한다면
- FVM을 사용하면 프로젝트마다 알맞은 Flutter 버전을 쉽게 전환할 수 있습니다.
- 마치 여러 개의 옷장에서 상황에 맞는 옷을 골라 입는 것처럼요!

## SSH 키 생성 및 GitHub 연동
> SSH를 설정하면 GitHub에 매번 아이디/비밀번호를 입력하지 않아도 됩니다.

### 1. SSH 키 생성하기
터미널(맥) 또는 명령 프롬프트(윈도우)를 열고 다음 명령어를 입력합니다.
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
> ⚠️ `your_email@example.com` 부분을 자신의 GitHub 이메일로 바꿔주세요.

이후 나오는 질문들:
1. "키를 저장할 위치" → 그냥 엔터 누르기 (기본 위치에 저장)
2. "암호 입력" → 엔터 2번 누르기 (암호 없이 설정)

### 2. 생성된 SSH 키 복사하기
#### macOS 사용자
```bash
cat ~/.ssh/id_ed25519.pub | pbcopy
```
> 이 명령어를 실행하면 자동으로 SSH 키가 복사됩니다.

#### Windows 사용자
```bash
type %userprofile%\.ssh\id_ed25519.pub | clip
```
> 이 명령어를 실행하면 자동으로 SSH 키가 복사됩니다.

### 3. GitHub에 SSH 키 등록하기
1. GitHub.com에 로그인
2. 오른쪽 상단의 프로필 사진 클릭 → Settings 클릭
3. 왼쪽 메뉴에서 "SSH and GPG keys" 클릭
4. 초록색 "New SSH key" 버튼 클릭
5. Title: 사용하는 기기 이름 입력 (예: "회사 맥북", "개인 컴퓨터")
6. Key: 아까 복사한 내용 붙여넣기
7. "Add SSH key" 버튼 클릭

### 4. SSH 연결 확인하기
```bash
ssh -T git@github.com
```
> "Hi [사용자이름]!" 메시지가 나오면 성공입니다.

### 5. 프로젝트 가져오기
```bash
git clone git@github.com:username/repository.git
```
> ⚠️ 실제 repository 주소는 GitHub의 초록색 "Code" 버튼을 클릭하고 SSH 탭에서 복사할 수 있습니다.

## Flutter 프로젝트 생성하기
### 1. 새 프로젝트 생성
프로젝트를 생성할 디렉토리로 이동한 후, 다음 명령어를 실행합니다:
```bash
flutter create .
```
> 이 명령어는 현재 디렉토리에 Flutter 프로젝트를 생성합니다.

## FVM 설치하기
> 여러 Flutter 버전을 효율적으로 관리하기 위한 도구입니다.

### macOS 사용자
터미널에서 아래 명령어들을 순서대로 입력합니다:
```bash
brew tap leoafarias/fvm
brew install fvm
```
> ⚠️ brew가 설치되어 있지 않다면 먼저 [Homebrew 설치](https://brew.sh/)가 필요합니다.

### Windows 사용자
명령 프롬프트(CMD)를 관리자 권한으로 실행하고 입력:
```bash
dart pub global activate fvm
```
> ⚠️ Dart SDK가 설치되어 있어야 합니다.

## Flutter 버전 설정하기
### 1. 지정된 Flutter 버전 설치
```bash
fvm install
```
> 이 명령어는 Flutter 3.24.5 버전을 다운로드하고 설치합니다.

### 2. 프로젝트에 Flutter 버전 적용
```bash
fvm use 3.24.5   # 해당 버전 사용 설정
```

### 3. 프로젝트 실행 확인
프로젝트가 정상적으로 생성되었는지 확인하기 위해:
```bash
fvm flutter run
```
> ⚠️ 실행하기 전에 에뮬레이터나 실제 기기가 연결되어 있어야 합니다.

## IDE 설정하기 ( 문제가 발생하는 경우에만 )
### VS Code 사용자
1. VS Code 실행
2. 프로젝트 폴더에서 `.vscode` 폴더 생성
3. `.vscode` 폴더 안에 `settings.json` 파일 생성
4. 아래 내용 추가:
```json
{
  "dart.flutterSdkPath": ".fvm/flutter_sdk"
}
```

### Android Studio 사용자
1. Android Studio 실행
2. Preferences (맥) 또는 Settings (윈도우) 메뉴 열기
   - 맥: `⌘ + ,`
   - 윈도우: `Ctrl + Alt + S`
3. 왼쪽 메뉴에서 Languages & Frameworks → Flutter 선택
4. Flutter SDK path에 `.fvm/flutter_sdk` 입력
5. Apply → OK 클릭

## 그 외의 문제가 발생하는 경우
위 가이드에서 다루지 않은 문제가 발생하면, GitHub 저장소에서 이슈를 작성할 수 있습니다:
1. [GitHub Issues](https://github.com/coding-sensei-class/first_clone/issues) 페이지 방문
2. "New issue" 버튼 클릭
3. 문제 상황을 자세히 설명:
   - 사용 중인 운영체제
   - FVM 버전
   - 오류 메시지
   - 시도해본 해결 방법
4. 제출 전 비슷한 이슈가 있는지 검색해보면 더 빠른 해결 방법을 찾을 수 있습니다!
