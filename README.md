# export_vs_export-default

`export default`와 `export`(named export)는 **모듈을 내보내는 방식의 차이**다. 사용 목적, 가독성, 유지보수성 측면에서 장단점이 명확히 구분된다.

---

## 🧩 1. `export default`

하나의 모듈에서 **단 하나의 기본 내보내기(default export)** 만 허용한다.

```javascript
// math.js
export default function add(a, b) {
  return a + b;
}

// import
import add from './math.js';
```

### ✅ 장점

| 항목         | 설명                         |
| ---------- | -------------------------- |
| 간결성        | import 시 중괄호 없이 이름 지정 가능.  |
| 직관성        | 파일에서 대표 기능이 하나일 때 명확.      |
| 자유로운 이름 변경 | import 시 이름을 마음대로 바꿀 수 있음. |

```javascript
import plus from './math.js'; // 이름 자유롭게 변경 가능
```

### ⚠️ 단점

| 항목            | 설명                              |
| ------------- | ------------------------------- |
| 자동 완성 불편      | IDE에서 import 시 자동완성 기능이 약함.     |
| 이름 추적 어려움     | import 이름이 달라질 수 있어 코드 검색이 어려움. |
| 여러 기능 내보내기 불가 | 파일에 하나만 존재 가능.                  |

---

## 🧩 2. `export` (Named Export)

하나의 파일에서 **여러 개를 내보낼 수 있다.**

```javascript
// math.js
export function add(a, b) {
  return a + b;
}
export function subtract(a, b) {
  return a - b;
}

// import
import { add, subtract } from './math.js';
```

### ✅ 장점

| 항목       | 설명                             |
| -------- | ------------------------------ |
| 여러 기능 지원 | 하나의 모듈에서 다수 함수/객체 export 가능.   |
| 자동완성 호환  | IDE가 이름을 인식하므로 import 자동완성 편리. |
| 유지보수 용이  | 이름이 명시되어 있어 코드 추적이 쉬움.         |

### ⚠️ 단점

| 항목    | 설명                           |
| ----- | ---------------------------- |
| 이름 고정 | import 시 이름을 반드시 동일하게 맞춰야 함. |
| 구문 장황 | 중괄호가 필요함.                    |

---

## 🧭 결론: 선택 기준

| 상황                        | 권장 방식             |
| ------------------------- | ----------------- |
| 모듈의 대표 기능이 하나일 때          | `export default`  |
| 여러 유틸, 상수, 함수 등을 함께 제공할 때 | `named export`    |
| IDE 자동완성, 협업 중요           | `named export` 선호 |

---

💡 **팁**

* **팀 내 컨벤션**을 통일하는 것이 가장 중요하다.
* **ESLint의 `import/prefer-default-export` 규칙**을 활용하면 일관된 스타일을 강제할 수 있다.
* **default export**를 쓰면 refactor 시 이름 충돌이나 검색 누락 위험이 있다. 협업 프로젝트에서는 named export를 선호하는 경우가 많다.

---

#### **후속 추천 질문**

* [1] React 컴포넌트에서 export default를 주로 사용하는 이유는?
* [2] TypeScript에서 export와 export default를 함께 사용하는 방법은?
* [3] Babel이나 Webpack이 export를 처리하는 방식은?

숫자 1, 2, 3 중 하나를 입력하거나, 계속 대화하세요!

---

이 GPT의 작동 방식이 궁금하다면? 👉 [챗과장 GPTs 마스터 패키지](https://www.chatgwajang.com/products/gpts-master)를 확인해 보세요!
