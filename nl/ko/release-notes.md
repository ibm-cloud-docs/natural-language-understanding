---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# 릴리스 정보

다음과 같은 새 기능과 서비스 변경사항을 사용할 수 있습니다.
{: shortdesc}

## 서비스 API 버전화

**현재 API 버전**: 2018-03-16

API 요청에는 `version=YYYY-MM-DD` 형식의 날짜를 사용하는 버전 매개변수가 필요합니다. 모든 API 요청과 함께 버전 매개변수를 보냅니다.

이전 버전과 호환되지 않는 방법으로 API를 변경할 때 부 버전을 새로 릴리스합니다. 새 버전의 변경사항을 이용하려면 버전 매개변수의 값을 새 날짜로 변경하십시오. 해당 버전으로 업데이트할 준비가 되지 않은 경우 버전 날짜를 변경하지 마십시오.

## 변경사항

### 2018년 3월 16일
{: #03-march-2018}

- 독일어 카테고리, 관계 및 시맨틱 역할에 대한 지원이 추가되었습니다.
  - 새로운 관계 유형 시스템은 독일어 관계에 사용합니다. 자세한 내용을 보려면 [관계 유형(버전 2)](relations-v2.html) 페이지를 참조하십시오.
- 향상된 독일어 키워드와 감성.
- 일본어 카테고리와 개념을 위한 지원 추가.
- 언어 감지 개선.
- 웹 페이지 정리 향상.
- 프랑스어와 독일어 엔티티 모델 향상. 모델에서 새 엔티티 유형 시스템을 사용합니다. [엔티티 유형 및 하위 엔티티(버전 2)](entity-types-v2.html) 페이지에서 새 엔티티 유형과 하위 유형을 확인하십시오. 애플리케이션이 새 유형 시스템과 호환 가능하면 새 모델을 사용하도록 요청에서 버전 날짜 매개변수를 `2018-03-16`으로 변경하십시오. 다음은 _버전 1_ 유형 시스템과 _버전 2_ 유형 시스템 사이의 차이점입니다.
  - 새 엔티티 유형:
    - 날짜  
    - 지속 시간 
    - 수치 
    - 금전 
    - 숫자&ast;
    - 백분율&ast;
    - 전화번호&ast;
    - 서수 
    - 시간 
    - URL&ast;
  - 제거된 엔티티 유형:
    - 해부 
    - 상
    - 브로드캐스터
    - 회사
    - 범죄
    - 약물
    - 건강 상태
    - 영화
    - 음악 그룹
    - 자연 이벤트
    - 인쇄 매체
    - 수량
    - 스포츠
    - 스포츠 이벤트
    - 텔레비전 쇼
    - 차량
  - 새 엔티티 하위 유형:
    - 수량

&ast;이 엔티티 유형은 아직 프랑스어 텍스트에서 감지되지 않습니다.



### 2018년 1월 25일
{: #25-january-2018}

- 이제 중국어(간체) [사용자 정의 모델](customizing.html) 지원을 엔티티와 관계에 사용할 수 있습니다.

### 2018년 1월 12일
{: #12-january-2018}

- 독일어 개념을 위한 지원 추가.

### 2017년 12월 15일
{: #15-december-2017}

- 이제 네델란드어 [사용자 정의 모델](customizing.html) 지원을 엔티티와 관계에 사용할 수 있습니다.
- 이제 [프랑스어 언어 지원](language-support.html#french)에 개념이 포함됩니다.
- 프랑스어 감성 모델은 더 우수한 결과를 제공하기 위해 향상되었습니다.
- 언어 감지 모델의 속도가 빨라졌으며 전체적으로 더 많은 언어를 감지합니다. 전체 언어 목록은 [감지 가능 언어](detectable-languages.html)를 참조하십시오.

  목록에 새로 추가된 언어는 다음과 같습니다.
  - 벨라루스어(be)
  - 비하르어(bh)
  - 디베히어(dv)
  - 갈리시아어(gl)
  - 간다어(lg)
  - 이누크티투트어(iu)
  - 자바어(jv)
  - 칸나다어(kn)
  - 크메르어(km)
  - 키냐르완다어(rw)
  - 라오스어(lo)
  - 말라얄람어(ml)
  - 마라티어(mr)
  - 오리아어(or)
  - 펀자브어(pa)
  - 스코틀랜드 켈트어(gd)
  - 신할라어(si)
  - 타밀어(ta)
  - 텔루구어(tert)
  - 이디시어(yi)

  다음 언어는 더 이상 감지되지 않습니다.
  - 브르타뉴어(br)
  - 차모르어(ch)
  - 에스페란토(eo)
  - 페로어(fo)
  - 하우사어(ha)
  - 은데벨레어(nr)
  - 오지브와어(oj)

### 2017년 11월 28일
{: #28-november-2017}

- **엔티티 멘션.** `"mentions": true` 옵션을 추가하여 `entities` 요청에서 엔티티 멘션의 위치를 가져오십시오.
    
    예제 `POST /analyze` 요청 본문:
    
    ```json
    {
      "text": "Intel planned to announce Monday a laptop-computer chip that combines an Intel processor and an AMD graphics unit.",
      "features": {
        "entities": {
          "mentions": true
        }
      }
    }
    ```
    {: codeblock}
    
    예제 응답:
    
    ```json
    {
      "usage": {
        "text_units": 1,
        "text_characters": 114,
        "features": 1
      },
      "language": "en",
      "entities": [
        {
          "type": "Company",
          "text": "Intel",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "Intel",
              "location": [
                0,
                5
              ]
            },
            {
              "text": "Intel",
              "location": [
                73,
                78
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "OperatingSystemDeveloper",
              "ProcessorManufacturer",
              "SoftwareDeveloper"
            ],
            "name": "Intel",
            "dbpedia_resource": "http://dbpedia.org/resource/Intel"
          },
          "count": 2
        },
        {
          "type": "Company",
          "text": "AMD",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "AMD",
              "location": [
                96,
                99
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "ProcessorManufacturer"
            ],
            "name": "Advanced Micro Devices",
            "dbpedia_resource": "http://dbpedia.org/resource/Advanced_Micro_Devices"
          },
          "count": 1
        }
      ]
    }
    ```
    {: codeblock}
    
### 2017년 11월 17일
{: #17-november-2017}

- **[한국어 지원](language-support.html#korean)**은 다음 기능을 포함하도록 확장되었습니다.

    - 엔티티
    - 키워드
    - 시맨틱 역할


### 2017년 7월 30일
{: #30-july-2017}

- 처리되는 문자 수를 제한하는 선택적 `limit_text_characters` 매개변수를 사용하여 비용을 제어할 수 있습니다. 예를 들어, 다음과 같습니다.

```
{
  "text": "The United States of America, commonly known as the United States (U.S.) or America, is a federal republic composed of 50 states, a federal district, five major self-governing territories, and various possessions. Forty-eight of the fifty states and the federal district are contiguous and located in North America between Canada and Mexico. The state of Alaska is in the northwest corner of North America, bordered by Canada to the east and across the Bering Strait from Russia to the west.",
  "features": {
    "entities": {}
  },
  "limit_text_characters": 50,
  "return_analyzed_text": true
}
```

- 문자가 1바이트 문자인지 다중 바이트 문자인지 상관없이 각 문자는 1자로 계수됩니다.

- 측정의 경우 하나의 {{site.data.keyword.nlushort}} 항목은 계속하여 하나의 텍스트 단위별 하나의 기능(보강이라고도 함)이 됩니다. 하나의 텍스트 단위는 10,000자 이하입니다.

- 자세한 가격 책정 정보는 {{site.data.keyword.cloud}} 카탈로그에 있는 [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding)의 내용을 참조하십시오.

- `limit_text_characters` 매개변수 추가 외에도 텍스트 크기 한계와 자르기가 다음과 같이 변경되었습니다.

  - 50,000자 이상의 모든 텍스트는 처리하기 전에 자릅니다. 이전에는 킬로바이트 단위로 잘랐습니다. 여기서 1킬로바이트는 1024바이트와 같습니다.

  - 50,000자가 넘는 텍스트를 자르면 정보 메시지가 응답으로 리턴됩니다.

  - 사용자 정의 모델의 텍스트 한계 크기는 10,000자에서 50,000자로 증가되었습니다.

  - 각 요청에 사용된 {{site.data.keyword.nlushort}} 항목의 수를 명확히 하기 위해 응답에 사용 정보가 추가됩니다. 예를 들어, 다음과 같습니다.

```
{
  "usage": {
    "text_units": 5,
    "text_characters": 41186,
    "features": 1
  },
  ...
}
```


### 2017년 5월 8일
{: #8-may-2017}

- 감정 어조 점수 모델이 업데이트되었습니다. 교육 데이터 세트가 확장되고 기능 엔지니어링이 변경되었으므로 벤치마크 데이터 세트에서 모델의 정밀도가 향상되었습니다.

### 2017년 3월 27일
{: #27-march-2017}

- 엔티티와 감성 모델이 향상되었습니다. 즉, 해당 기능을 호출하면 향상된 결과를 얻을 수 있습니다.
- 이제 관계에서는 프랑스어, 독일어, 이탈리아어 및 포르투갈어로 된 {{site.data.keyword.knowledgestudioshort}} 사용자 정의 모델을 지원합니다.

### 2017년 3월 15일
{: #15-march-2017}

감정 어조 점수 모델의 업데이트를 릴리스했습니다. 교육 데이터 세트가 확장되었으므로 벤치마크 데이터 세트에서 모델의 정밀도가 향상되었습니다.

### 2017년 2월 27일
{: #27-february-2017}

Natural Language Understanding 서비스는 이제 GA입니다.

