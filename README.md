# wiki-creator

에이전트가 프로젝트의 근거·결정·구현 지식을 Markdown 위키로 만들고 유지하도록 돕는 스킬이다. 새 위키를 시작하거나 기존 위키에 자료를 반영하고, 위키를 바탕으로 답변하고, 프로젝트 변경과의 일치 여부를 점검한다.

## 설치

[skills.sh의 CLI](https://skills.sh/docs/cli)를 사용한다. Node.js 22.20.0 이상과 npm/npx가 필요하다. 스킬을 사용할 프로젝트에서 실행하면 설치할 에이전트를 선택할 수 있다.

```sh
npx skills add mkachi/wiki-creator --skill wiki-creator
```

여러 프로젝트에서 사용하려면 전역으로 설치한다.

```sh
npx skills add mkachi/wiki-creator --skill wiki-creator -g
```

Codex만 지정하고 선택 과정 없이 설치하려면 다음과 같이 실행한다.

```sh
npx skills add mkachi/wiki-creator --skill wiki-creator -a codex -g -y
```

설치 전에 스킬 목록을 확인할 수도 있다.

```sh
npx skills add mkachi/wiki-creator --list
```

위 명령은 이 저장소의 파일이 GitHub에 반영되어 있고 해당 저장소에 접근할 수 있을 때 사용할 수 있다. 별도의 npm 패키지 배포는 필요하지 않다.

## 사용

설치한 에이전트에 원하는 작업을 요청한다.

| 작업 | 요청 예시 |
| --- | --- |
| 위키 시작 | `wiki-creator로 이 프로젝트의 기존 문서와 지침에 맞는 위키를 만들어줘.` |
| 자료 반영 | `이 릴리스 노트의 확인된 내용을 기존 위키에 근거 링크와 함께 반영해줘.` |
| 질문 | `기존 위키를 바탕으로 재시도 정책과 그 근거를 설명해줘. 파일은 수정하지 마.` |
| 변경 동기화 | `이번 변경과 관련된 위키 문서를 확인하고 달라진 내용을 갱신해줘.` |
| 일관성 점검 | `위키의 깨진 링크, 중복, 오래된 주장과 근거를 점검해줘.` |

설치는 스킬과 참고 자료를 에이전트에 제공한다. 대상 프로젝트의 위키는 위와 같이 생성을 요청할 때 만든다. 기존 위키 경로와 프로젝트 지침을 우선하며, 정해진 경로가 없으면 `.agents/wiki/`를 시작점으로 사용할 수 있다.

템플릿의 자세한 적용 방식은 [템플릿 안내](assets/llm-wiki-template/README.md)를 참고한다.

## 저장소 구성

```text
wiki-creator/
├── SKILL.md                       # 스킬 이름·설명과 실행 절차
├── assets/llm-wiki-template/       # 프로젝트에 맞춰 적용할 위키 템플릿
│   ├── AGENTS.md
│   ├── README.md
│   └── .agents/
│       ├── wiki/                  # 작성 기준·운영 절차·시작 문서
│       └── templates/             # 주제·출처·결정 양식
└── references/                    # 컨벤션 선택 기준과 기술별 참고 자료
```

루트에 `SKILL.md`를 두는 단일 스킬 구조는 [공식 스킬 탐색 규칙](https://github.com/vercel-labs/skills/blob/main/docs/creating-skills.md#skill-discovery)에서 지원한다. `assets/`와 `references/`는 스킬의 일부이므로 함께 유지하며, 템플릿 안의 숨김 폴더 `.agents/`도 포함한다. 설치를 위해 `package.json`이나 빌드 단계를 추가할 필요는 없다.

## 로컬 확인

저장소 루트에서 설치 없이 스킬 탐색을 확인한다.

```sh
npx skills add . --list
```

실제 설치를 검증할 때는 별도의 빈 프로젝트를 사용한다. 설치 결과에 `SKILL.md`, `references/`, `assets/llm-wiki-template/.agents/`가 포함되는지 확인한다.
