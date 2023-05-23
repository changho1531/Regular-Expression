# Regular-Expression
정규표현식 정리글

# 정규 표현식 (Regular Expression)

정규 표현식(Regular Expression)은 텍스트에서 특정 패턴을 찾거나 매칭하는 데 사용되는 문자열 표현 방식입니다. 정규 표현식은 문자열 처리 작업을 보다 간단하고 효율적으로 수행할 수 있도록 도와줍니다.

## 필요성

정규 표현식은 다음과 같은 경우에 필요합니다:

- 특정 패턴이나 형식을 가진 문자열을 추출하고자 할 때
- 문자열의 유효성을 검사하고자 할 때
- 텍스트에서 특정 패턴을 대체하거나 변경하고자 할 때

## 파이썬에서의 기본 사용법

파이썬에서는 `re` 모듈을 통해 정규 표현식을 사용할 수 있습니다. 아래는 파이썬에서 정규 표현식을 사용하는 기본적인 예제입니다.

```python
import re

# 패턴 매칭
pattern = r"apple"  # apple 패턴을 정의
text = "I have an apple"  # 텍스트에서 패턴 매칭을 검사할 문자열
match = re.search(pattern, text)  # 정규 표현식과 문자열을 비교하여 매칭 결과를 반환
if match:
    print("매칭되었습니다.")
else:
    print("매칭되지 않았습니다.")

# 패턴 추출
pattern = r"(\d+)-(\d+)-(\d+)"  # 숫자로 이루어진 날짜 패턴을 정의
text = "Date: 2023-05-22"  # 텍스트에서 패턴 매칭을 검사할 문자열
match = re.search(pattern, text)  # 정규 표현식과 문자열을 비교하여 매칭 결과를 반환
if match:
    year = match.group(1)  # 그룹화된 부분 패턴을 추출
    month = match.group(2)
    day = match.group(3)
    print(f"Year: {year}, Month: {month}, Day: {day}")
else:
    print("패턴이 일치하지 않습니다.")

# 패턴 대체
pattern = r"apple"  # apple 패턴을 정의
text = "I have an apple"  # 텍스트에서 패턴을 대체할 문자열
replaced_text = re.sub(pattern, "orange", text)  # 정규 표현식과 문자열을 비교하여 패턴을 대체
print(replaced_text)
```
- 패턴 매칭: re.search() 함수를 사용하여 주어진 텍스트에서 패턴을 검사합니다. 매칭 결과를 반환하고 매칭 여부를 확인합니다.
- 패턴 추출: 괄호 ()를 사용하여 부분 패턴을 그룹화합니다. match.group() 함수를 사용하여 추출된 패턴을 확인합니다.
- 패턴 대체: re.sub() 함수를 사용하여 주어진 텍스트에서 패턴을 찾아 다른 문자열로 대체합니다.

## 파이썬에서의 사용법 예제

아래는 파이썬에서 정규 표현식을 사용하는 또 다른 예제입니다.

```python
import re
# 이메일 주소 유효성 검사
pattern = r"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"
email = "example@example.com"
if re.match(pattern, email):
    print("유효한 이메일 주소입니다.")
else:
    print("유효하지 않은 이메일 주소입니다.")

# 전화번호 추출
pattern = r"\d{3}-\d{4}-\d{4}"
text = "고객센터: 010-1234-5678"
phone_numbers = re.findall(pattern, text)
print("추출된 전화번호:")
for number in phone_numbers:
    print(number)

# 태그 제거
pattern = r"<[^>]+>"
html = "<h1>제목</h1><p>본문입니다.</p>"
removed_tags = re.sub(pattern, "", html)
print("태그 제거 결과:")
print(removed_tags)
```
- 이메일 주소 유효성 검사: 입력된 이메일 주소가 유효한 형식인지 확인합니다.
- 전화번호 추출: 주어진 텍스트에서 전화번호 패턴을 추출합니다.
- 태그 제거: HTML 태그를 제거하여 태그 없는 텍스트를 얻습니다.
