
# 행동 지침

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.


---
# C# Nullable Reference Type Coding Rules

## 1. 기본 원칙

* Nullable Reference Type을 기본적으로 허용하지 않는다.
* 객체와 데이터가 정상적인 상태에서는 가능한 한 `null`이 존재하지 않도록 설계한다.
* `null`은 실제로 "값이 없음"을 표현해야 하는 경우에만 사용한다.

## 2. 프로퍼티 기본값
Reference Type 프로퍼티는 가능한 한 기본값을 지정하여 `null` 상태가 발생하지 않도록 한다.

## 3. 생성자 초기화
객체 생성 시 반드시 필요한 값은 생성자를 통해 초기화한다.

## 4. 컬렉션은 null을 반환하지 않는다
컬렉션은 가능한 한 항상 유효한 컬렉션 객체를 반환한다.


---
# 코드 스타일 규칙

- 안전성이 실질적으로 동일하다면 항상 더 짧고 단순한 구조를 선택한다.
- 이름 규칙(프라이빗 필드 `_snake_case` 등)은 새로 정하지 말고 해당 프로젝트의 기존 코드 관례를 따른다.
- `?.` 널 조건 연산자 대신 명시적 `if (x != null) { }` 블록을 사용한다.
