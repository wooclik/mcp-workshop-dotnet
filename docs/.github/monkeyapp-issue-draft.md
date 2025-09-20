
# Monkey 콘솔 애플리케이션 구현 - 이슈 초안

아래는 이 저장소에 올릴 GitHub 이슈의 완성된 본문 초안입니다. 이슈 기능이 비활성화된 경우 이 내용을 기반으로 Pull Request를 생성해 제안할 수 있습니다.

제목: Monkey 콘솔 애플리케이션 구현

요구사항

- C# 콘솔 애플리케이션을 구현하세요. 애플리케이션은 다음 기능을 제공해야 합니다:
   - 사용 가능한 모든 원숭이 목록 출력
   - 이름으로 특정 원숭이의 세부 정보 조회
   - 무작위 원숭이 선택 기능
- 애플리케이션은 프로젝트의 `Monkey` 모델 클래스를 사용해야 합니다(속성 예: `Name`, `Location`, `Population`).
- 출력은 가독성과 시각적 매력을 위해 간단한 ASCII 아트를 포함해야 합니다.

레이블: enhancement, good first issue

구현 세부사항 (개발자 가이드)

- 위치: 가능한 경우 `workshop/MyMonkeyApp` 프로젝트에 구현하세요. 이미 `MyMonkeyApp` 프로젝트가 있다면 그 내부를 사용합니다.
- 구조 제안:
   - Models/Monkey.cs : `Name`, `Location`, `Population` 등의 속성
   - Helpers/MonkeyHelper.cs : 샘플 데이터(정적 리스트)와 다음 메서드 제공
      - `IEnumerable<Monkey> GetMonkeys()`
      - `Monkey? GetMonkeyByName(string name)`
      - `Monkey GetRandomMonkey()`
   - Program.cs : 콘솔 메뉴와 입력 처리, ASCII 아트 출력
- 계약(간단)
   - 입력: 콘솔 입력(메뉴 선택, 원숭이 이름 등)
   - 출력: 콘솔 텍스트(목록, 상세, ASCII 아트)
   - 오류 처리: 잘못된 입력에 대해 친절한 메시지 제공

권장 구현 세부사항

- `MonkeyHelper`는 테스트 편의를 위해 인터페이스로 추상화하지 않아도 됩니다(초기 작업).
- 데이터는 하드코딩된 샘플 리스트로 충분합니다(예: 5종류의 원숭이).
- 이름 조회는 대소문자 구분 없이 동작해야 합니다.
- 무작위 선택은 .NET의 `Random`을 사용하고, 테스트를 위해 시드 주입을 허용하면 좋습니다.

예상 엣지 케이스

- 원숭이 이름이 존재하지 않을 때 (존재하지 않음 메시지)
- 빈 목록(샘플 데이터가 올바르게 로드되지 않은 경우)
- 사용자 입력이 비어있거나 유효하지 않은 경우

작업 체크리스트

- [ ] `Monkey` 모델 클래스 정의(프로퍼티: `Name`, `Location`, `Population`)
- [ ] `MonkeyHelper` 구현(샘플 데이터, `GetMonkeys`, `GetMonkeyByName`, `GetRandomMonkey`)
- [ ] 콘솔 UI 구현(메뉴: 목록, 이름 조회, 무작위 선택, 종료)
- [ ] ASCII 아트 추가 및 출력 포맷 개선
- [ ] 입력 유효성 검사 및 예외 처리
- [ ] README 또는 docs에 실행 방법과 예시 추가
- [ ] (선택) 간단한 유닛 테스트 추가(핵심 메서드 테스트)

간단한 ASCII 아트 예시

```
    (\_/)
    (o.o)  Monkey
    /) )
```

작업 예시(개발자에게 유용한 팁)

- `GetMonkeyByName`는 내부적으로 `string.Equals(name, candidate.Name, StringComparison.OrdinalIgnoreCase)` 사용
- 무작위 선택은 `new Random().Next(list.Count)` 식으로 구현하되, 테스트 시에는 `Random`을 주입 가능하도록 설계
- 콘솔 UI는 간단한 숫자 기반 메뉴로 구현(예: 1: 목록, 2: 이름조회, 3: 무작위, 0: 종료)

참고: 리포지토리의 Issues 기능이 비활성화되어 있으면 PR로 제안하세요. PR에는 이 이슈 초안과 구현 코드를 함께 포함하면 리뷰가 용이합니다.

