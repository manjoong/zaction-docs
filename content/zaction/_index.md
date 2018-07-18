+++
title = "Cloud Z Action"
date = 2018-07-05T04:20:00Z
weight = 2
alwaysopen = true
+++
## Cloud Z Action   
---
Cloud Z Action는 서버 관리 없이 웹 애플리케이션을 개발할 수 있는 Cloud Service 입니다.
사용자는 Cloud Z Action를 통해 함수(애플리케이션 내의 단위 함수 모듈)를 작성할 수 있습니다. 그리고 이 함수를 실행할 수 있는 API 엔드포인트(함수를 실행할 수 있는 HTTP Request URL)를 생성할 수 있습니다.
이제 작성된 함수를 API 엔드포인트로 실행함으로써 사용자 웹 애플리케이션을 쉽고 빠르게 개발할 수 있게 됩니다.



> 함수를 사용하지 않는 동안은 비용이 청구 되지 않고, 사용 시에는 사용한 메모리, 사용 시간, 사용 횟수를 바탕으로 비용이 청구 됩니다.



## 액션
----
- 
### 액션이란
Cloud Z Action을 이용하여 개발 가능한 모든 단위 모듈을 액션이라 합니다. 모듈의 종류는 아래의 액션 타입의 내용과  같습니다.

- 
### 액션 타입
액션 타입은 다음과 같은 항목들이 있습니다.
<br>
- 함수 : 코드를 포함한 기본적인 액션입니다. (javascript, python)
- 트리거 : 이벤트를 수신하여 연결된 액션을 호출합니다.
- 플로우 : 정의된 순서대로 여러개의 액션을 호출합니다.
- 스위치 : 조건에 따라 수행되는 액션을 다르게 분기하며, 병렬수행을 가능하게 합니다.
- 블루프린트 : 기본제공되는 템플릿 및 다른 사용자들이 공유한 액션을 이 용하면 보다 손쉽게 액션을 만들수 있습니다.

## 함수
----
함수는 Cloud Z Action에서 생성 가능한 액션 타입 중 하나로, 애플리케이션 내의 단위 함수 모듈을 의미합니다.
```Node

function (context, params) {
// code here
return { ... }

```
위와 같이 작성한 함수를 Cloud Z Action에 저장 및 배포하면 해당 함수를 실행할 수 있는 API Endpoint를 제공 받습니다. API Endpoint는 해당 함수를 HTTPS 방식으로 Request/Response 할 수 있는 URL 입니다. 이렇게 함수를 생성함으로써 사용자의 웹 애플리케이션이 완성되었습니다.

이제 함수를 생성/편집/사용/삭제하는 방법을 알아보겠습니다.

- 
### 함수 새로 만들기

함수액션을 새로 작성합니다.
직접 만들기, 기존에 만들어준 내 함수에서 복사하여 만들기, 블루프린트의 템플릿을 이용하여 만들기 등 세가지 방법으로 만들 수 있습니다.

> 베타 버전에서는 내 함수 복사, 블루 프린트 기능을 제공하지 않습니다.  


![cloudZ](https://dev.action.cloudz.co.kr/assets/img/function_create.cbb01a61.png)

#### 함수이름 (필수 입력 사항)

사용할 함수의 이름을 입력 합니다. 입력 규칙은 다음과 같습니다.

- 영문, 언더스코어(_), 하이픈(-), 숫자 조합
- 한글, 공백은 사용할 수 없음
- 언더스코어(_), 하이픈(-)을 제외한 특수문자는 사용할 수 없음  

> 함수이름 예)
myFn01, dev_getUser, common-make-01, ...



#### 패키지
서로 관련이 있는 함수들을 모아 하나의 묶음(그룹) 단위로 구성하는 것을 말합니다.
특별한 기준이 없고, 사용자의 편의에 따라 자유롭게 구성합니다.
신규 패키지 버튼을 이용하여 신규 패키지를 생성할 수 있고, 또는, 기존 패키지를 선택할 수 있습니다.
패키지를 선택하면 생성될 함수는 선택한 패키지 내에 그룹핑 됩니다.
입력 규칙은 다음과 같습니다.

- 영문, 숫자 조합

> 패키지에 속한 함수를 표시하기 위해 슬래쉬(/)기호를 이용하여 "packageName/functionName"으로 표시되기도 합니다.

#### 런타임 (필수 입력 사항)

함수의 실행 환경을 선택할 수 있습니다.
다음의 런타임 환경을 지원합니다.

- Node.js 6
- Node.js 8

> 베타 버전에서는 Node.js 만 지원 합니다.

#### 버전

작성한 함수에 버전을 기록해두면, 과거에 배포한 특정 버전의 함수로 롤백할 수 있습니다.
버전은 다음과 같은 특징이 있습니다.
- 버전은 버전명과 상관 없이 최신순으로 저장됩니다.
- 최대 10개의 버전이 저장되고, 10개가 초과되는 경우, 가장 오래된 순으로 버전과 함수 데이터가 삭제 됩니다.

> 베타 버전에서는 지원하지 않는 기능 입니다.

<br>
#### 테그

함수에 복수개의 별칭을 표시해두는 기능이 테그 입니다.
함수 리스트에서 검색 조건에 테그를 추가하면 해당 테그가 표시된 함수만 검색이 가능합니다.
단위 테그 입력 후 **엔터키** (Enter)를 입력하면 추가 테그를 입력할 수 있습니다.

#### 설명

함수에 대한 설명 및 기록할 사항을 입력합니다.

#### 함수만들기

필수 입력 사항을 입력하고 입력 규칙에 따라 입력하였다면, 이제 함수만들기 버튼을 이용하여 함수를 생성하게 됩니다.

> 취소 버튼으로 함수만들기를 취소하면 기존 입력한 데이터가 삭제됨을 유의해야 합니다.

- 
### 코드 및 테스트

생성된 함수의 코드를 작성 하고, 해당 코드에 대한 테스트 실행을 합니다.
파일은 여러개 생성할 수 있으나, 메인 함수는 오직 하나여야 합니다.

> 테스트 실행 시 비용이 발생됩니다.

![cloudZ](https://dev.action.cloudz.co.kr/assets/img/function_edit.da6cdd3d.png)


#### 코드 작성 방법

함수 생성 시, 기본으로 제공되는 코드 입니다.
```Node
module.exports = function (context, params) {
let name = "Noone";
if (params.name) {
name = params.name;
}
let place = "Nowhere";
if (params.place) {
place = params.place;
}
return {myField: 'Hello, ' + name + ' from ' + place}
};
```

#### module.exports

사용자 코드를 Node.js 모듈로 export/import 하기 때문에 함수를 정의할 때는 _**반드시 module.exports 를 사용해야 합니다.**_
#### context

배포 환경 별 환경 변수가 전달 됩니다.
#### params

요청 파라미터가 전달 됩니다.
"매개변수"에 "입력 값 설정"이 오버라이드 되고, 그 다음에 요청 파라미터가 오버라이드 됩니다.
#### return

return object type은 다음을 고려하여 결정 합니다.
- 코드 상에 동기(synchronous) 코드만 존재하는 경우 - **JSON Object**
```JSON
return {key1: value1, key2: value2}
```
- 코드 상에 비동기(asynchronous) 코드를 포함하는 경우 - **Promise Object**
```Node
return new Promise(function(resolve, reject){
asyncExcute().then(arg => {
resolve({status:200, data: arg});
})
.catch(err => {
resolve({status:500, data: err});
})
})
```
#### 저장

함수의 코드를 수정 후 저장합니다. 저장이 정상 수행된 경우 함수 최초 생성 직후는 이미 기본 코드가 저장된 상태입니다. 만약 수정 사항을 저장할 경우, 화면 우상단에 저장 결과에 대한 토스트 메시지가 표시 됩니다.
![cloudZ](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAskAAAAtCAIAAADTHWEHAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyRpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNi1jMTQyIDc5LjE2MDkyNCwgMjAxNy8wNy8xMy0wMTowNjozOSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTggV2luZG93cyIgeG1wTU06SW5zdGFuY2VJRD0ieG1wLmlpZDpERUE0N0JCMTdCNDIxMUU4QkM3OEY3NERDQjRFMzU4OCIgeG1wTU06RG9jdW1lbnRJRD0ieG1wLmRpZDpERUE0N0JCMjdCNDIxMUU4QkM3OEY3NERDQjRFMzU4OCI+IDx4bXBNTTpEZXJpdmVkRnJvbSBzdFJlZjppbnN0YW5jZUlEPSJ4bXAuaWlkOkRFQTQ3QkFGN0I0MjExRThCQzc4Rjc0RENCNEUzNTg4IiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOkRFQTQ3QkIwN0I0MjExRThCQzc4Rjc0RENCNEUzNTg4Ii8+IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY+IDwveDp4bXBtZXRhPiA8P3hwYWNrZXQgZW5kPSJyIj8+MnkkzgAAHWJJREFUeNrsXQl8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)
<br>

#### 입력값 설정

테스트 실행 시 전달될 파라미터를 설정합니다. "입력 값 설정"은 코드 및 테스트 화면에서 테스트 버튼을 이용해 테스트를 수행할 경우에만 전달되는 파라미터 입니다.

> API Endpoint를 통해 함수 실행(HTTP Request) 시에는 "입력 값 설정"은 전달되지 않습니다.
단, 매개변수는 항상 전달 됩니다.

![cloudZ](https://dev.action.cloudz.co.kr/assets/img/function_test_parameter.423218a1.png)

#### 테스트 실행 및 테스트 결과

저장된 함수의 코드를 실행하고, 테스트 결과 화면에 표시 합니다.

> 저장하지 않은 상태의 화면 상의 코드는 수행되지 않습니다.

테스트 결과는 다음과 같은 정보를 표시 합니다.
![cloudZ](https://dev.action.cloudz.co.kr/assets/img/function_test.9f55aae3.png)

- 테스트 아이디 (uuid)
- 테스트 실행 완료한 시점의 타임스템프
- 정상/에러에 대한 요청 Input, Output
- 사용자 지정 로그(console.log 등)
- 함수 실행 소요 시간
- 테스트 사용 메모리


> 테스트 최대 사용 메모리를 이용하여 함수에 적합한 운영 사용 메모리를 설정해야 메모리 및 성능의 부족 없이 함수를 실행할 수 있습니다.
함수 테스트 시 비용이 발생합니다.



- 
### 구성 정보

코드 이외의 함수의 속성 및 설정 정보를 확인 및 편집할 수 있고, API Endpoint를 확인할 수 있습니다.

> 각 구성 정보 변경 사항을 반영하기 위해 [저장]이 필요 합니다.


#### 기본정보

패키지, 태그, 설명의 정보를 변경할 수 있습니다.
#### 매개변수

Key{string} / Value{string} 구조의 정적 파라미터를 저장 할 수 있습니다. 이렇게 저장된 매개변수는 함수가 실행될 때마다 함수의 인자(params)에 전달 됩니다. 단 아래와 같은 오버라이드 규칙이 있음을 참고 바랍니다.


> API Endpoint를 통해 함수가 실행될 때 전달되는 데이터를 "요청 파라미터"라고 한다면, 최종적으로 함수의 인자(params)로 전달될 데이터는 "매개변수"에 "입력 값 설정"이 오버라이드 되고, 그 상태에서 "요청 파라미터"가 오버라이드 된 데이터입니다.


#### 런타임
함수의 "런타임", "타임아웃(Seconds)", "메모리(MB)"를 설정/변경할 수 있습니다.
"타임아웃(Seconds)"은 함수가 실행되는 동안의 소요 시간 또는 실행 시간을 의미 합니다.
"메모리(MB)"는 함수 실행에 필요한 최대 메모리 제한을 의미 합니다. 함수 [테스트] 실행 시 최대 사용 메모리 측정값을 알 수 있습니다. 이 최대 사용 메모리를 바탕으로 적절한 "메모리(MB)"를 설정해야 합니다.

> "메모리(MB)"에 비례하여 비용이 발생 합니다.

#### API Endpoint

HTTTP Request URL을 통해 함수를 실행할 수 있는 API Endpoint를 제공하고, 그 설정은 다음과 같습니다.
- Public/Private

> Public은 누구나 접근 가능한 API 엔드포인트를 설정하고, Private은, API 엔드포인트가 API KEY로 보호됩니다.
API KEY는 각 영역(Space)별로 고유한 값이 부여됩니다. API KEY가 유출되지 않도록 보안에 유의해야 합니다. API KEY는 HTTP Header에 정해진 규약으로 전송해야 하는데, HTTP Header Field name을 "apikey"로 하고, API KEY를 값으로 합니다.

- 타겟 환경

> 함수가 배포되는 환경을 의미 합니다. 영역(Space)별로 최대 3개의 타겟 환경을 생성/관리 할 수 있습니다. 예를들어, 개발계/검증계/운영계와 같은 환경 구성이 가능한 것 입니다.
베타 버전에서는 타겟 환경을 하나만 제공됩니다.

- API 엔드포인트 사용

> API 엔드포인트의 요청 가능 상태를 Enabled/Disabled 처리 할 수 있습니다.

- HTTP 메소드

> GET, POST, PUT, DELETE를 지원합니다.

- Content Type

> application/json을 지원합니다.

- URL

> API 엔드포인트를 호출할 수있는 HTTTP Request URL 입니다.

- cURL

> 테스트를 위해 제공됩니다.




