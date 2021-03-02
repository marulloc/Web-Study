# 문자열 & 정규표현식

- 특정한 비-알파벳 문자들은 역슬래시(\)로 시작하는 이스케이프 문자열을 통해 지원한다.

- 구두점 문자(?,!,.,등등)를 일반 문자로 취급할려면 반드시 \를 문자 앞에 붙여야 한다.

### 문자열 변환

```js
string.toUpperCase();
string.toLowerCase();
```

### 문자열 치환

```js
string.replace("banana", "tomato");
string.replace(/banana/gi, "tomato");
```

- replace는 첫번째로 발견된 banana만 tomato로 반환한다.
- replaceAll이 javascript에는 없다. 따라서 정규표현식을 써서 치환해야 한다.
  - g 옵션은 글로벌 매치로 문자열 전체에서 치환 가능한 부분문자열을 모두 치환한다.
  - i 옵션은 대소문자 구분을 없앤다. 따라서 `"Banana banana".replace(/banana/gi,"tomato)`는 "tomato tomato"가 된다.

### 특정 문자 제거

```js
string.replace(/[^\w-.]/g, "");
```

- `[^xy]`는 "x와 y가 아니면"의 의미다. `^[xy]`는 "xy로 시작하는.."의 의미다.
- `\w`는 `알파벳, 숫자, "_"`를 의미한다.
- 따라서 `replace(/[^\w-_.]/g,"")`는 `알파벳,숫자,"_","-","."`가 아닌 모든(**g옵션**) 문자열을 제거(**""**)한다.

### 문자열의 시작과 끝

```js
string.replace(/^\@/, "");
string.replace(/\@$/, "");
string.replace(/^\@|\@$/, "");
```

- `^@`는 @로 시작되는 문자열의 시작 @를 ""로 치환
- `@$`는 @로 끝나는는 문자열의 끝 @를 ""로 치환
- `^@ | @$`는 @로 시작되거나 @로 끝나는 문자열의 @를 ""로 치환

### 특정 문자 반복

```js
string.replace(/\@{2}/g, "@");
string.replace(/\@{2,}/g, "@");
string.replace(/\@{2,4}/g, "@");
```

- `@{n}`은 @가 n번 반복되는 부분 문자열을 말한다.
- `@{n,}`은 @가 n번 **이상** 반복되는 부분 문자열을 말한다.
- `@{n,m}`은 @가 최소 n번 이상 최대 m번 이하로 반복되는 부분 문자열을 말한다.

### 문자열 반복

```js
string.repeat(2);
```

- js에는 문자열에 `*`연산이 안된다.
- 문자열을 반복하려면 repeat 메소드를 써야한다.