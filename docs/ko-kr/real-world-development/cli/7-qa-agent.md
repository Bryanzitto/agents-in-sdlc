---
title: "레슨 7 - QA 에이전트 만들기 및 사용하기"
description: "이슈 요구 사항, quality-checks 스킬, Playwright MCP를 결합하는 QA 사용자 지정 에이전트를 만듭니다."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

`quality-checks` 스킬로 자동 검사를 실행하고 Playwright MCP로 브라우저의 필터링 환경을 살펴봤습니다. 이제 이러한 기능을 명확한 QA 프로세스를 갖춘 사용자 지정 에이전트로 결합합니다.

이 레슨에서는 다음을 수행합니다.

- 사용자 지정 에이전트가 지침, 스킬, MCP 도구와 작동하는 방식을 살펴봅니다.
- 재사용 가능한 품질 보증 프로필을 만들고 검사합니다.
- QA 에이전트를 선택하고 필터링 이슈를 기준으로 결과를 검토합니다.

## 시나리오

Tailspin Toys는 풀 리퀘스트(PR)를 열기 전에 요구 사항, 코드 품질, 자동 검사, 테스트 범위, 브라우저 동작을 일관되게 검토하려고 합니다. 사용자 지정 에이전트는 이 QA 프로세스를 조율하고 재사용 가능한 보고서를 제공할 수 있습니다.

## 사용자 지정 에이전트란?

사용자 지정 에이전트는 Markdown 프로필에 정의된 Copilot의 전문 버전입니다. 프로필은 에이전트의 목적, 지침, 사용 가능한 도구를 설명합니다. 이 워크숍에서는 `.github/agents/qa.agent.md`에 QA 역할을 정의하고 Copilot CLI에서 선택합니다.

지금까지 사용한 사용자 지정 기능은 서로 다른 역할을 합니다. 리포지토리 지침은 팀의 표준을 설명하고, `quality-checks` 스킬은 반복 가능한 검사를 패키징하며, Playwright MCP는 브라우저 도구를 제공합니다. QA 프로필은 Copilot에 이러한 기능을 사용해 요구 사항을 평가하고 결과를 보고하는 방법을 알려 줍니다. 이 기능을 대체하거나 다른 대화를 요구하지 않습니다.

## QA 프로필 만들기

기능 PR을 열기 전에 Copilot에 재사용 가능한 QA 프로필을 만들도록 요청합니다. 프로필은 QA가 수행할 검사와 따라야 할 범위를 모두 정의합니다.

1. Codespace로 돌아가 필터링 대화가 Interactive 모드인지 확인합니다.
2. 기본 에이전트에 새 사용자 지정 에이전트를 만들도록 요청합니다.

   ```plaintext
   Create a custom agent named QA in .github/agents/qa.agent.md. It should check features against their issues and agreed requirements, follow the repository instructions, run the quality-checks skill, use Playwright MCP to verify behavior, and add tests when coverage is missing.

   Have it report each requirement as pass, fail, or blocked with supporting evidence. It must ask before changing implementation code, and it must not commit changes or open pull requests.

   Just create the profile for now so I can review it.
   ```

## 프로필 검사하기

새 에이전트를 사용하기 전에 Copilot이 의도한 QA 작업 흐름과 범위를 반영했는지 프로필을 검토합니다. 검증만 하려는 상황에서 불완전하거나 지나치게 넓은 에이전트가 기능을 변경하는 일을 막을 수 있습니다.

1. `/diff`를 입력하고 `.github/agents/qa.agent.md`를 엽니다.
2. frontmatter를 읽습니다. `description`은 필수이며 `name`은 선택 사항이지만, 포함하면 에이전트에 명확한 표시 이름을 지정할 수 있습니다.
3. 프로필 지침을 읽고 QA가 요구 사항에서 시작하고 리포지토리 지침을 따르며 `quality-checks` 스킬을 실행하고 Playwright MCP를 사용하는지 확인합니다.
4. QA가 근거를 보고하고 구현 코드를 변경하기 전에 요청하며 커밋하거나 풀 리퀘스트를 열지 않는지 확인합니다.
5. 생성된 프로필에 이러한 책임이나 범위가 빠졌다면 계속하기 전에 기본 에이전트에 수정을 요청합니다.

## 이슈를 기준으로 QA 실행하기

Copilot CLI는 대화가 시작될 때 프로젝트 에이전트를 불러옵니다. 프로필을 만든 뒤 동일한 필터링 대화를 다시 시작하고 QA를 선택하면 컨텍스트에 있는 이슈와 계획 결정을 사용할 수 있습니다.

1. 다음 프롬프트로 에이전트를 활성화합니다.

   ```plaintext
   /agent QA
   ```

> [!NOTE]
> 방금 에이전트를 만들었으므로 사용 가능한 에이전트 목록에 표시되지 않을 수 있습니다. 에이전트는 존재하며 위 명령으로 활성화할 수 있습니다.

2. 다음 프롬프트로 QA 에이전트에 기능을 검토하도록 요청합니다.

   ```plaintext
   Review the filtering feature against the issue and the decisions in our plan. Is it ready for a PR?
   ```

3. QA 에이전트가 작업하는 과정을 살펴봅니다.
4. 작업이 끝나면 제공된 보고서를 읽습니다.

## 요약 및 다음 단계

재사용 가능한 전문 역할을 워크플로에 추가하고 결과를 검토했습니다. 이 레슨에서는 다음을 수행했습니다.

- 사용자 지정 에이전트가 지침, 스킬, MCP 도구와 작동하는 방식을 살펴봤습니다.
- 재사용 가능한 품질 보증 프로필을 만들고 검사했습니다.
- QA 에이전트를 선택하고 필터링 이슈를 기준으로 결과를 검토했습니다.

이제 구현, 스킬 업데이트, QA 프로필, 테스트, 검증 보고서가 검토할 준비가 되었습니다. 다음으로 [기능 PR에서 이를 결합하고 Agent Merge를 사용][next-lesson]합니다.

## 리소스

- [Copilot CLI용 사용자 지정 에이전트 만들기][create-agents]
- [사용자 지정 에이전트 구성][agent-config]

[previous-lesson]: ../4-mcp/
[next-lesson]: ../8-create-pull-request/
[create-agents]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli
[agent-config]: https://docs.github.com/copilot/reference/custom-agents-configuration
