---
title: "레슨 3 - 에이전트 모드: Plan 및 Autopilot"
description: "Plan으로 접근 방식을 정하고, Autopilot으로 이슈에서 필터링 기능을 구현한 뒤 Interactive 모드에서 결과를 검토합니다."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

프로젝트에 작은 기능을 추가하는 것으로 시작했습니다. 하지만 큰 변경에는 더 견고한 프로세스가 필요합니다. GitHub Copilot CLI는 조직의 기존 흐름에 맞춰 올바른 것을 올바른 방식으로 만들 수 있도록 설계되었습니다. 이 레슨부터 이슈를 사용해 새 기능을 만들고, 코드가 유효하고 기능이 예상대로 작동하는지 확인한 뒤 프로젝트에 성공적으로 병합하는 일반적인 에이전트 기반 개발 프로세스를 따릅니다.

> [!NOTE]
> 기능 작업을 계속하는 동안 동일한 대화와 브랜치를 사용합니다. 일반적으로는 작업할 파일 유형에 따라 브랜치나 PR을 나누지만, 핵심 개념에 집중할 수 있도록 여기서는 간소화합니다.

이 레슨에서는 다음을 수행합니다.

- GitHub 이슈에서 새 Copilot 대화를 시작합니다.
- Plan 모드에서 요구 사항을 정의합니다.
- Autopilot 모드로 새 기능을 구현합니다.
- 코드를 검토합니다.
- 포워딩된 브라우저에서 기능을 수동으로 검증합니다.

이 기능을 계속 발전시키면서 리포지토리 지침을 업데이트하고, 기존 `quality-checks` 스킬을 사용자 지정하고, MCP 검증을 추가하고, QA 에이전트를 만들고, 기능 PR을 엽니다.

## 시나리오

Tailspin Toys의 카탈로그가 커지면서 방문자가 게임을 카테고리와 게시자로 좁혀 볼 수 있어야 합니다. 백로그 이슈에 기능이 설명되어 있지만 카테고리 조합과 같은 세부 사항은 코딩 전에 합의해야 합니다. Plan 모드에서 이러한 결정을 정한 다음 Autopilot으로 범위가 정해진 구현을 승인합니다.

## 배경

AI 코딩 에이전트를 개발 흐름에 도입해도 기본 원칙은 바뀌지 않습니다. 오히려 더 중요해집니다. 대부분의 개발자는 다음과 비슷한 흐름을 따릅니다.

1. 해야 할 일을 설명하는 이슈에서 시작합니다.
2. 구현할 내용을 계획합니다.
3. 코드를 작성하고 검토합니다.
4. 테스트를 실행해 코드를 검증합니다.
5. 새 기능을 수동으로 검증합니다.
6. 풀 리퀘스트(PR)를 만듭니다.
7. 코드 검토가 끝나고 지속적 통합 프로세스가 성공하면 코드를 병합합니다.

이 표준 접근 방식을 따르면 AI가 생성한 코드도 요구 사항을 충족하고 수동으로 작성한 코드와 같은 검증 절차를 거치게 됩니다.

## 대화 모드

**대화 모드**는 에이전트의 자율성 수준을 제어합니다. <kbd>Shift</kbd>+<kbd>Tab</kbd>을 눌러 모드를 전환합니다.

- **Interactive**: 사용자와 에이전트가 함께 작업합니다. 에이전트는 변경 사항을 제안하고 사용자의 입력을 기다립니다.
- **Plan**: 에이전트가 먼저 계획을 만들며 프로젝트 파일을 편집할 수 없습니다.
- **Autopilot**: 에이전트가 자율적으로 코드를 작성하고 테스트를 실행하며 작업이 완료될 때까지 반복합니다.

Plan 모드에서 시작해 계획을 검토한 다음 Autopilot으로 구현합니다.

## 이슈에서 시작하기

필터링 작업을 시작하기 전에 Codespace로 돌아가 리포지토리와 터미널을 준비합니다.

1. Codespace로 돌아갑니다. 중지된 상태라면 다시 시작합니다.
2. 별점 PR이 병합되었는지 확인합니다.
3. 터미널이 열려 있지 않으면 <kbd>Control</kbd>+<kbd>\`</kbd>(Mac) 또는 <kbd>Ctrl</kbd>+<kbd>\`</kbd>(Windows/Linux)를 누릅니다.
4. `main`을 업데이트한 다음 필터링 작업용 브랜치를 만듭니다.

   ```bash
   git checkout main
   git pull --ff-only
   git checkout -b game-filters-cli
   ```

5. Copilot CLI를 시작합니다.

   ```bash
   copilot --yolo
   ```

6. <kbd>Tab</kbd>을 두 번 눌러 **Issues** 탭을 엽니다.
7. <kbd>A</kbd>를 눌러 모든 이슈를 표시합니다.
8. **Allow users to filter games by category and publisher**라는 이슈를 화살표 키로 강조 표시합니다.
9. <kbd>C</kbd>를 눌러 이슈를 프롬프트에 추가하고 **Session** 탭으로 돌아갑니다.

프롬프트가 `#7`(또는 비슷한 번호)로 시작하는 것을 확인합니다. `#`을 사용하면 GitHub의 이슈나 풀 리퀘스트(PR)를 컨텍스트로 가져올 수 있습니다.

## 필터링 기능 계획하기

계획을 세우면 기능을 구현하거나 작업을 Copilot에 넘기기 전에 접근 방식을 정할 수 있습니다. 복잡한 작업은 먼저 계획하는 것이 좋습니다. Plan 모드로 전환해 Copilot에 계획을 만들도록 요청합니다.

1. <kbd>Shift</kbd>+<kbd>Tab</kbd>을 눌러 Plan 모드로 전환합니다. 프롬프트 아래의 모드 표시기에 **Plan**이 표시되는지 확인합니다.
2. 앞 단계에서 추가한 이슈 참조 뒤에 다음 프롬프트를 입력합니다.

   ```plaintext
   Create a plan for implementing this feature.
   ```

Copilot이 프로젝트를 살펴본 뒤 가장 좋은 접근 방식을 정해 계획을 작성합니다.

3. 필터링 기능이 어떻게 작동해야 하는지 Copilot이 질문할 수 있습니다. 원하는 방식에 따라 답합니다. 정답은 없습니다.
4. 계획이 완성되면 <kbd>Control</kbd>+<kbd>E</kbd>(Mac) 또는 <kbd>Ctrl</kbd>+<kbd>E</kbd>(Windows/Linux)를 눌러 계획을 확장합니다.
5. 계획을 위아래로 스크롤하며 검토합니다.
6. 결정과 맞지 않는 부분은 Copilot에 수정을 요청합니다.

## Autopilot 승인하기

계획을 작성하고 검토했으므로 구현할 차례입니다. Autopilot을 사용해 Copilot이 작업하도록 합니다.

Autopilot을 사용하면 Copilot이 작업이 완료되었다고 판단할 때까지 문제를 반복해서 해결합니다.

1. **Accept plan and build on autopilot (recommended)** 또는 설치된 버전에서 같은 의미의 옵션을 선택합니다.
2. 프롬프트 아래의 모드 표시기에 **Autopilot**이 표시되는지 확인합니다.
3. Copilot이 계획을 따라 반복하고 코드를 생성하며 테스트를 실행하는 과정을 살펴봅니다.

> [!NOTE]
> 승인하면 구현이 즉시 시작될 수 있으므로 먼저 계획을 검토합니다. Copilot이 누락된 종속성이나 포트 충돌을 보고하면 설정 문제를 해결한 뒤 검사를 완료된 것으로 봅니다.

## 구현 검토 및 확인하기

코드가 생성되면 다른 코드와 마찬가지로 병합 전에 검토해야 합니다. 코드를 검토하고 사이트를 실행해 제대로 표시되는지 확인합니다.

1. <kbd>Shift</kbd>+<kbd>Tab</kbd>을 눌러 Interactive 모드로 들어갑니다. 모드 표시기에 **Plan**이나 **Autopilot**이 더 이상 표시되지 않는지 확인합니다.
2. `/diff`를 입력하고 필터링 구현과 테스트를 살펴봅니다.
3. 결과를 이슈 및 계획 중 내린 결정과 비교합니다.
4. 코드 검토가 끝나면 <kbd>Esc</kbd>를 눌러 diff 보기를 닫습니다.
5. 프로젝트 검사 결과를 검토하고 실패한 항목은 Copilot에 해결을 요청합니다.

## 새 기능 살펴보기

코드는 좋아 보이지만 실제로 실행될까요? 이전처럼 앱을 시작하고 Codespaces의 포워딩된 포트를 통해 사이트를 엽니다.

1. Copilot에 앱을 시작하도록 요청합니다.

   ```plaintext
   Start the app so I can try the filtering feature in my browser. Tell me the URL and leave the server running.
   ```

2. Codespaces에서 포트 `4321`을 사용할 수 있다고 알리면 **Open in Browser**를 선택합니다.
3. 계획에서 합의한 카테고리 필터링, 게시자 필터링 및 조합을 시도합니다.
4. 재설정 및 결과 없음 동작이 이슈와 결정에 맞는지 확인합니다.
5. Codespace로 돌아가 Copilot에 시작한 개발 서버를 중지하도록 요청합니다.

## 요약 및 다음 단계

서로 다른 대화 모드로 기능을 만들고 검토했습니다. 이 레슨에서는 다음을 수행했습니다.

- GitHub 이슈에서 새 Copilot 대화를 시작했습니다.
- Plan 모드에서 요구 사항을 정의했습니다.
- Autopilot 모드로 새 기능을 구현했습니다.
- 코드를 검토했습니다.
- 포워딩된 브라우저에서 기능을 수동으로 검증했습니다.

다음으로 [사용자 지정 지침][next-lesson]을 사용해 코드가 문서화된 관행을 따르도록 생성되는 과정을 자세히 살펴봅니다.

## 리소스

- [GitHub Copilot CLI의 Autopilot][autopilot]
- [Copilot CLI 명령 참조][cli-reference]

[autopilot]: https://docs.github.com/copilot/concepts/agents/copilot-cli/autopilot
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[previous-lesson]: ../1-install-copilot-cli/
[next-lesson]: ../2-custom-instructions/
