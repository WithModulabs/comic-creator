# Comic Creator

한국어 만화 제작을 빠르게 시작할 수 있는 Codex 하네스입니다. 아이디어 한 줄에서 출발해 4컷 만화, 짧은 웹툰, 스토리보드, 대사, 이미지 프롬프트, 레이아웃, 리뷰 문서까지 제작 가능한 산출물로 정리합니다.

## Node.js 설치 방법

Codex CLI는 npm으로 설치할 수 있으므로, 먼저 Node.js와 npm이 준비되어 있어야 합니다. 처음 설치하는 경우에는 안정적인 LTS 버전을 권장합니다.

### 1. 이미 설치되어 있는지 확인

PowerShell 또는 터미널을 열고 아래 명령을 실행합니다.

```powershell
node --version
npm --version
```

두 명령 모두 버전이 출력되면 Node.js 설치는 완료된 상태입니다. 둘 중 하나라도 명령을 찾을 수 없다고 나오면 아래 절차로 설치합니다.

### 2. Windows에서 설치

가장 쉬운 방법은 공식 설치 파일을 사용하는 것입니다.

1. [Node.js 공식 다운로드 페이지](https://nodejs.org/en/download)에 접속합니다.
2. `LTS` 버전을 선택합니다.
3. Windows Installer인 `.msi` 파일을 내려받습니다.
4. 설치 파일을 실행하고 기본 옵션으로 설치합니다.
5. 설치가 끝나면 PowerShell을 새로 열고 버전을 확인합니다.

```powershell
node --version
npm --version
```

여러 Node.js 버전을 바꿔 써야 한다면 Microsoft 문서에서 권장하는 `nvm-windows` 방식도 사용할 수 있습니다. 단순히 Codex CLI만 설치하려면 공식 `.msi` 설치 방식이 가장 간단합니다.

### 3. macOS에서 설치

공식 설치 파일을 사용할 수 있습니다.

1. [Node.js 공식 다운로드 페이지](https://nodejs.org/en/download)에 접속합니다.
2. `LTS` 버전을 선택합니다.
3. macOS Installer인 `.pkg` 파일을 내려받아 설치합니다.
4. 터미널을 새로 열고 확인합니다.

```bash
node --version
npm --version
```

Homebrew를 사용한다면 아래처럼 설치할 수도 있습니다.

```bash
brew install node
```

### 4. Linux 또는 WSL2 Ubuntu에서 설치

Linux에서는 배포판 패키지 관리자나 Node.js 공식 안내의 패키지 매니저 설치 방식을 사용할 수 있습니다. Ubuntu/WSL2에서는 먼저 패키지 목록을 갱신한 뒤 설치합니다.

```bash
sudo apt update
sudo apt install -y nodejs npm
node --version
npm --version
```

배포판 기본 저장소의 Node.js가 너무 오래된 경우에는 Node.js 공식 다운로드 페이지의 Linux 패키지 매니저 안내를 참고해 LTS 버전을 설치합니다.

### 5. Node.js 설치 문제 해결

- `node` 또는 `npm` 명령을 찾을 수 없음: 설치 후 터미널을 완전히 닫았다가 다시 엽니다.
- Windows에서 계속 인식되지 않음: Node.js 설치 경로가 `PATH` 환경 변수에 들어갔는지 확인하거나 `.msi` 설치 파일로 재설치합니다.
- 오래된 버전이 출력됨: 기존 Node.js를 제거한 뒤 LTS 버전을 다시 설치하거나, 버전 관리 도구를 사용합니다.
- 권한 오류가 남: 관리자 권한으로 억지 설치하기보다 사용자 계정의 npm 전역 설치 경로 설정을 먼저 확인합니다.

참고 문서:

- [Node.js 공식 다운로드](https://nodejs.org/en/download)
- [npm 공식 설치 안내](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
- [Microsoft Windows Node.js 설정 안내](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-beginners-tutorial)

## Codex CLI 설치 방법

이 저장소는 Codex CLI에서 사용하는 것을 기준으로 구성되어 있습니다. 아래 절차는 Node.js와 npm 설치가 끝난 뒤 진행합니다.

### 1. 설치 전 확인

먼저 터미널에서 `node`와 `npm`을 사용할 수 있는지 다시 확인합니다.

```powershell
node --version
npm --version
```

버전이 출력되지 않으면 위의 Node.js 설치 방법을 먼저 진행합니다. Windows에서는 PowerShell에서 그대로 사용할 수도 있고, Linux 환경이 필요하면 WSL2의 Ubuntu 터미널에서 진행할 수도 있습니다.

Git은 필수는 아니지만 저장소 작업, 변경 내역 확인, PR 보조 기능을 쓰려면 설치를 권장합니다.

```powershell
git --version
```

### 2. npm으로 설치

가장 기본적인 설치 방법은 npm 전역 설치입니다.

```powershell
npm i -g @openai/codex
```

설치 후 `codex` 명령이 잡히는지 확인합니다.

```powershell
codex --version
```

명령을 찾을 수 없다고 나오면 터미널을 새로 열어 보거나, npm 전역 실행 파일 경로가 `PATH`에 포함되어 있는지 확인합니다.

```powershell
npm prefix -g
```

### 3. 첫 실행과 로그인

프로젝트 폴더로 이동한 뒤 Codex를 실행합니다.

```powershell
cd path\to\comic-creator
codex
```

처음 실행하면 로그인을 요구합니다. 화면 안내에 따라 ChatGPT 계정으로 로그인하거나 API key 방식을 선택합니다. 로그인 후에는 현재 폴더의 파일을 읽고, 수정하고, 필요한 명령을 실행하는 방식으로 작업합니다.

### 4. 업데이트

Codex CLI는 자주 업데이트되므로 문제가 있거나 새 기능이 필요하면 최신 버전으로 갱신합니다.

```powershell
npm i -g @openai/codex@latest
```

업데이트 후 다시 버전을 확인합니다.

```powershell
codex --version
```

### 5. macOS 설치 옵션

macOS에서는 npm 외에 Homebrew cask로도 설치할 수 있습니다.

```bash
brew install --cask codex
```

### 6. 자주 막히는 부분

- `codex` 명령을 찾을 수 없음: 터미널을 새로 열고, npm 전역 설치 경로가 `PATH`에 들어 있는지 확인합니다.
- 권한 오류가 남: 관리자 권한 터미널을 쓰기보다, 사용자 계정에서 npm 전역 설치 경로를 정상 설정하는 방식을 권장합니다.
- Windows에서 Linux 도구가 필요함: PowerShell 네이티브 실행 대신 WSL2 Ubuntu 안에서 설치하고 실행합니다.
- 설치는 됐지만 실행이 이상함: `npm i -g @openai/codex@latest`로 갱신한 뒤 `codex --version`과 `codex` 실행을 다시 확인합니다.

참고 문서:

- [OpenAI Codex CLI 문서](https://developers.openai.com/codex/cli)
- [OpenAI Codex GitHub 저장소](https://github.com/openai/codex)
- [Codex 설치 및 빌드 문서](https://github.com/openai/codex/blob/main/docs/install.md)

## 주요 용도

- 만화 아이디어를 제작 가능한 브리프로 정리
- 4컷 만화나 짧은 웹툰의 스토리보드 작성
- 컷별 대사, 내레이션, 효과음, 말풍선 메모 작성
- 캐릭터 기준 프롬프트와 컷별 이미지 생성 프롬프트 작성
- 페이지 또는 웹툰형 레이아웃 지시서 작성
- 완성 전 검토 리포트 작성

## 폴더 구조

```text
.codex/
|-- AGENTS.md
`-- skills/
    `-- comic-creator/
        |-- SKILL.md
        |-- agents/
        |   `-- openai.yaml
        `-- references/
            |-- character-design-system.md
            |-- panel-composition.md
            |-- role-guides.md
            `-- visual-narrative.md
```

## 사용 예시

Codex에게 아래처럼 요청하면 됩니다.

```text
4컷 만화 만들어줘.
주제: 코딩하다가 버그 잡는 이야기
톤: 가볍고 웃긴 느낌
스타일: 한국 웹툰풍
```

조금 더 명확하게 요청하려면 다음처럼 말할 수 있습니다.

```text
comic-creator 스킬로 4컷 만화 제작 패키지 만들어줘.
대상: 중학생 이상
장르: 코미디
포함 산출물: 스토리보드, 대사, 이미지 프롬프트, 레이아웃, 리뷰
```

## 생성 산출물

작업 결과는 날짜 기반 고유 폴더인 `_workspace/YYYY-MM-DD/` 아래에 저장됩니다. 같은 날짜 폴더가 이미 있으면 `_workspace/YYYY-MM-DD-01/`, `_workspace/YYYY-MM-DD-02/`처럼 다음 번호를 사용합니다.

- `00_input.md`: 사용자 요청을 정리한 제작 브리프
- `01_storyboard.md`: 줄거리, 캐릭터 시트, 컷별 스토리보드
- `02_dialogue.md`: 대사, 내레이션, 효과음, 말풍선 메모
- `03_image_prompts.md`: 캐릭터 기준 프롬프트와 컷별 이미지 프롬프트
- `04_layout.md`: 페이지 또는 웹툰 레이아웃 지시서
- `05_review_report.md`: 전체 검토 결과와 수정 필요 사항
- `panels/`: 생성되었거나 배치 예정인 패널 이미지

## 작업 원칙

- 결과물은 채팅에만 남기지 않고 작업 폴더에 파일로 저장합니다.
- 형식이 명확하지 않은 짧은 만화 요청은 기본적으로 4컷 만화로 진행합니다.
- 필요한 정보가 일부 비어 있으면 안전한 기본값으로 진행하고, 가정한 내용은 `00_input.md`에 기록합니다.
- 실제 이미지 생성을 요청받지 않은 경우에는 제작 가능한 프롬프트와 레이아웃 지시서를 우선 작성합니다.
