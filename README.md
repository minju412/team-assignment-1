# [팀 과제] 노션에서 브로드 크럼스(Breadcrumbs) 만들기


## 목표
노션과 유사한 간단한 페이지 관리 API를 구현해주세요.

## 요구사항
- 각 페이지는 제목, 컨텐츠, 그리고 서브 페이지를 가질 수 있습니다. 
- 특정 페이지에 대한 브레드크럼(Breadcrumbs) 정보도 반환해야 합니다.
- orm 을 사용하지 않고 raw 쿼리만 사용합니다.
- depth 가 같은 서브페이지가 여러 개일 수 있습니다.

### 브레드크럼(Breadcrumbs)이란?
브레드 크럼이란 빵 부스러기로 헨젤과 그레텔에서 따온 용어로 현재 페이지의 위치를 시각적으로 나타내는 경로 또는 계층 구조의 탐색 메뉴를 의미합니다.
![스크린샷 2023-09-04 오후 4 29 16](https://github.com/minju412/jenkins-test/assets/59405576/16d5307d-92f6-4450-935b-3fcc2c386c0b)


## ERD
![스크린샷 2023-09-04 오후 4 56 44](https://github.com/minju412/jenkins-test/assets/59405576/77c5c3cf-a40e-4d61-8507-72ef4efda990)


## 과제 설명
- ”왜 이 구조가 최선인지?” 등



## API 명세 (request/response 포함)
### 1️⃣ 페이지 생성
```javascript
POST /pages
Host : 127.0.0.1:8080
Content-type : application/json
```
- 새로운 페이지를 생성할 수 있는 엔드포인트입니다.

#### Request Body
```json
{
  "title": "D",
  "content": "sss",
  "parentPageId" : 2
}
```
|    Name     |  Type  | Description | Nullable |
|:-----------:|:------:|:-----------:|:--------:|
|  **title**  | String |     제목      |  false   |
|**content** | String |     본문      |  false   |
|**parentPageId** |  Long   | 상위 페이지 아이디  |   true    |

#### Response
```json
{
  "id": 3,
  "title": "C",
  "content": "sample",
  "breadcrumbs": " / A / B / C",
  "parentPageId": 2
}
````

### 2️⃣ 페이지 조회
```javascript
GET /pages/{pageId}
Host : 127.0.0.1:8080
Content-type : application/json
```
- 브레드크럼과 하위 페이지를 포함한 페이지 정보를 조회할 수 있는 엔드포인트입니다.

#### Response
```json
{
  "id": 3,
  "title": "C",
  "breadcrumbs": " / A / B / C",
  "subPages": [
    "D",
    "E"
  ]
}
````

## Team Rule
### 1. Git Commit
커밋 메시지는 header 뿐만 아니라 body까지 상세히 작성합니다.
![image](https://github.com/petit-a-petit/team-assignment-1/assets/139187207/f7c77232-cab1-4b5c-a85a-96f12c703cf9)

### 2. Pull Request
- 테이블 구조
- 코드나 테이블 구조에 대한 설명. (”왜 이 구조가 최선인지?” 등)
- 결과 정보

### 3. PR Review
- Review는 마음껏 달아주세요!
  - 궁금한 점 🤔
  - 개선하면 좋을 것 같은 점 🚧
  - 인상적인 코드 😮

