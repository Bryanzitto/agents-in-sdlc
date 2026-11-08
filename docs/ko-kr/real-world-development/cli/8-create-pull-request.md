---
title: "레슨 8 - 기능 PR 만들기 및 병합하기"
description: "필터링, 지침, 스킬 업데이트, QA 프로필, 테스트를 함께 검토한 뒤 PR을 만들고 Agent Merge를 사용합니다."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

필터링 구현, 지침 업데이트, 스킬 업데이트, 품질 보증(QA) 프로필, 테스트가 하나의 브랜치에 저장되어 있습니다. 이제 함께 검토하고 풀 리퀘스트를 열 차례입니다. 별점 PR은 직접 병합했지만, 이번에는 **Agent Merge**가 프로세스를 관리하도록 합니다.

> [!NOTE]
> 일반적으로 기능, 지침 업데이트, 스킬 업데이트, QA 에이전트를 몇 개의 별도 PR로 나눕니다. 워크숍을 간소화하기 위해 전체 필터링 및 품질 작업 흐름을 하나의 대화와 브랜치에서 진행하고 모든 작업을 이 PR에 포함했습니다.

이 레슨에서는 다음을 수행합니다.

- Agent Merge가 무엇이며 병합 수명 주기를 자동화하는 방식을 알아봅니다.
- 전체 기능 변경 사항과 검증 근거를 검사합니다.
- 필터링 PR을 만듭니다.
- 검토한 후에만 Agent Merge를 활성화하고 PR이 병합되었는지 확인합니다.

## 시나리오

필터링 작업 흐름 전반에서 Copilot을 사용해 기능을 계획하고 구현하고 검증했습니다. 이제 Tailspin Toys는 개발자가 병합 권한을 계속 제어하는 가운데 남은 PR 작업을 자동화하려고 합니다.

## Agent Merge 소개

**Agent Merge**는 풀 리퀘스트를 병합하는 데 필요한 남은 작업을 자동화합니다. Agent Merge를 활성화하면 Copilot이 PR을 막는 문제를 해결하고, 실패한 지속적 통합(CI) 검사를 수정하고, 검토 의견에 응답하고, 필요한 경우 리베이스한 다음 리포지토리에서 허용할 때 GitHub 자동 병합을 활성화합니다.

지금까지는 직접 **Merge pull request**를 선택했습니다. 이제 Agent Merge가 이 책임을 맡을 수 있습니다. Agent Merge를 활성화하기 전에 작업을 검토하고 준비가 되었는지 확인합니다.

## Agent Merge로 PR 관리하기

모든 코드를 작성했으므로 함께 검토하고 PR을 만든 뒤 Agent Merge가 나머지 과정을 관리하도록 합니다.

1. Codespace로 돌아갑니다.
2. `/agent`를 입력해 에이전트 대화 상자를 엽니다.
3. 옵션 목록에서 **Default**를 선택하고 <kbd>Enter</kbd>를 누릅니다.
4. `/pr create` 명령을 사용해 새 PR을 만듭니다.
5. `/pr agentmerge` 명령을 사용해 Agent Merge를 활성화합니다.
6. Copilot이 PR의 지속적 통합 프로세스를 지켜보는지 확인합니다. 모든 검사가 성공하면 병합을 수행합니다.
7. Copilot에서 `"PR #14 was squash-merged successfully."`와 비슷한 메시지가 표시되는지 확인합니다.

> [!IMPORTANT]
> Agent Merge는 필수 승인, 브랜치 보호, 병합 큐, 리포지토리 설정 또는 누락된 권한을 우회하지 않습니다. 차단된 경우 보고된 이유를 읽고 리포지토리에서 허용하는 경우 검토한 병합을 수동으로 완료합니다.

## 요약 및 다음 단계

코드 생성, 코드 테스트 및 검증, 이제 풀 리퀘스트 프로세스 등 개발 프로세스의 여러 부분을 자동화했습니다. 이 레슨에서는 다음을 수행했습니다.

- Agent Merge가 무엇이며 병합 수명 주기를 자동화하는 방식을 알아봤습니다.
- 전체 기능 변경 사항과 검증 근거를 검사했습니다.
- 필터링 PR을 만들었습니다.
- 검토한 후에만 Agent Merge를 활성화하고 PR이 병합되었는지 확인했습니다.

다음으로 [유용한 Copilot CLI 슬래시 명령][next-lesson]을 살펴보고 컨텍스트, 모델, 공유, 선택적 cloud agent 위임을 알아봅니다.

## 리소스

- [Copilot CLI로 풀 리퀘스트 관리하기][manage-prs]
- [Copilot CLI 명령 참조][cli-reference]

[previous-lesson]: ../7-qa-agent/
[next-lesson]: ../7-slash-commands/
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
