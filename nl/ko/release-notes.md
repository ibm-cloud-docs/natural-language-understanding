---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-21"

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
{: #release-notes}

다음과 같은 새 기능과 서비스 변경사항을 사용할 수 있습니다.
{: shortdesc}

## 새 API 인증 프로세스
{: #iam-auth-process }

2018년 10월 30일, 댈러스(미국 남부)와 프랑크푸르트(독일) 위치는 토큰 기반 IAM(Identity and Access Management) 인증을 사용하도록 전환되었습니다 (자세한 정보는 [IAM 토큰으로 인증 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/watson/getting-started-iam.html) 참조).
{: important}

{{site.data.keyword.nlushort}} 서비스에는 다음 위치에서 호스팅하는 서비스 인스턴스에 대해 새 API 인증 프로세스가 있습니다.

- 2018년 10월 30일 현재 댈러스
- 2018년 10월 30일 현재 프랑크푸르트
- 런던
- 2018년 5월 29일 현재 시드니
- 도쿄
- 2018년 6월 12일 현재 워싱턴 DC

{{site.data.keyword.cloud_notm}}는 토큰 기반 IAM(Identity and Access Management) 인증으로 마이그레이션 중입니다. 일부 서비스 인스턴스에서는 IAM을 사용하여 API를 인증할 수 있습니다.

- 나열된 날짜 이후에 해당 위치에서 작성한 *새* 서비스 인스턴스가 있는 경우 IAM을 사용하여 API를 인증할 수 있습니다. 권한 헤더 또는 API 키에 전달자(bearer) 토큰을 전달할 수 있습니다. 이 토큰을 통해서는 모든 호출에 서비스 인증 정보를 임베드하지 않고 인증된 요청을 지원합니다. API 키는 기본 인증을 사용합니다. [IAM](/docs/services/watson/getting-started-iam.html)에 관해 자세히 알아보십시오.

    Watson SDK를 사용하면 API 키를 전달하고 SDK를 통해 토큰의 라이프사이클을 관리할 수 있습니다. 자세한 정보와 예는 API 참조서의 [인증 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/natural-language-understanding/#authentication){: new_window}을 참조하십시오.
- 표시된 날짜 전에 작성한 _기존_ 서비스 인스턴스의 경우 서비스 인스턴스의 사용자 이름과 비밀번호를 제공하여 계속 인증합니다. 결국 해당 서비스 인스턴스를 IAM 인증으로 마이그레이션해야 합니다. 마이그레이션 프로세스와 날짜에 관한 업데이트가 제공됩니다. 마이그레이션에 관한 자세한 정보는 [Cloud Foundry 서비스 인스턴스를 리소스 그룹으로 마이그레이션](/docs/resources/instance_migration.html)을 참조하십시오.

사용할 인증을 찾으려면 [{{site.data.keyword.cloud_notm}} 리소스 페이지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/resources){: new_window}에서 서비스 인스턴스를 클릭하여 서비스 인증 정보를 확인하십시오.


## 서비스 API 버전화
{: #service-api-versioning}

**현재 API 버전**: 2019-06-04

API 요청에는 `version=YYYY-MM-DD` 형식의 날짜를 사용하는 버전 매개변수가 필요합니다. 모든 API 요청과 함께 버전 매개변수를 보냅니다.

이전 버전과 호환되지 않는 방법으로 API를 변경할 때 부 버전을 새로 릴리스합니다. 새 버전의 변경사항을 이용하려면 버전 매개변수의 값을 새 날짜로 변경하십시오. 해당 버전으로 업데이트할 준비가 되지 않은 경우 버전 날짜를 변경하지 마십시오.

### 활성 버전 날짜
{: #active-version-dates}

다음 표에서는 각 버전 날짜에 대한 서비스 작동 변경사항을 보여줍니다. 추후 버전 날짜로 전환하면 이전 버전에 도입된 모든 변경사항이 활성화됩니다. 

|버전 날짜|변경사항 요약|
|---|---|
|[`2019-06-04`](#4-june-2019)| <li>사용자 정의 모델을 사용하는 엔티티 요청이 `limit` 옵션을 무시하게 한 버그가 수정되었습니다.</li><li>모든 엔티티 요청에 대한 기본 `limit` 값은 이제 모든 모델에 대해 50입니다. </li><li>250개 엔티티의 최대 `limit` 값이 제거되었습니다. </li>|
|[`2018-11-16`](#16-november-2018)| <li>버전 2 이탈리아어 엔티티 유형 시스템.</li>|
|[`2018-09-21`](#21-september-2018)| <li>버전 2 포르투갈어 엔티티 유형 시스템.</li>|
|[`2018-03-16`](#16-march-2018)| <li>버전 2 프랑스어 엔티티 유형 시스템.</li><li>버전 2 독일어 엔티티 유형 시스템.</li>| 
|[`2017-02-27`](#27-february-2017)| 기본 버전.| 

## 변경사항
{: #changes}

### 2019년 6월 21일
{: #21-june-2019}

- 이제 사용자 정의 기계 학습 모델을 사용하는 엔티티 요청에 대해 엔티티 신뢰도 점수가 리턴됩니다. 

### 2019년 6월 4일
{: #4-june-2019}

다음 변경사항은 `2019-06-04` 이후의 버전 날짜를 사용할 때 활성화됩니다. 

- 사용자 정의 모델을 사용하는 엔티티 요청이 `limit` 옵션을 무시하게 한 버그가 수정되었습니다.
- 모든 엔티티 요청에 대한 기본 `limit` 값은 이제 모든 모델에 대해 50입니다. 
- 250개 엔티티의 최대 `limit` 값이 제거되었습니다. 

### 2019년 5월 29일
{: #29-may-2019}

- 스페인어 감성이 향상되었습니다. 
- 대상에 특수 문자가 포함된 경우 대상으로 지정된 감성 결과에 영향을 줄 수 있는 버그가 수정되었습니다. 
- 워싱턴 DC, 도쿄, 런던 및 시드니에서 서비스 인스턴스에 대해 다음 변경사항이 사용 가능합니다.
  - 아랍어 및 러시아어를 제외한 모든 감성 지원 언어에 대해 사용자 지정 모델을 사용하는 엔티티 요청에 대한 감성 옵션을 사용할 수 있습니다. 


### 2019년 5월 24일
{: #24-may-2019}

- 독일어 키워드가 향상되었습니다.
- 댈러스가 아닌 모든 IBM Cloud 위치에서 서비스 인스턴스에 대한 영어 감성 업데이트가 릴리스되었습니다.

### 2019년 5월 3일
{: #3-may-2019}

- 독일어 문서 레벨 감성 감지가 향상되었습니다.

### 2019년 4월 25일 
{: #25-april-2019}

- 규칙 기반 [사용자 정의 모델](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing)에 대한 엔티티 멘션이 사용 가능합니다. 결과에서 멘션을 보려면 `mentions` 엔티티 옵션을 `true`로 설정하십시오.
- 영어 카테고리 결과에 대한 설명을 릴리스했습니다. 각 결과에 기여한 소스의 관련 텍스트를 보려면 `explanation` 카테고리 옵션을 `true`로 설정하십시오.

### 2019년 3월 19일
{: #19-march-2019}

- {{site.data.keyword.knowledgestudioshort}}로 작성된 사용자 정의 카테고리 모델에 대한 실험적 지원이 도입되었습니다. 시작하려면 [사용자 정의 카테고리 모델 작성](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model)을 참조하십시오. 
- 스페인어 키워드 및 개념이 향상되었습니다. 

### 2019년 1월 10일
{: #10-january-2019}

- 버전 날짜 매개변수를 포함하지 않는 **모델 나열** 및 **모델 삭제** 요청에서 이제 성공적인 응답이 아니라 `400` 오류를 리턴합니다.
- 영어 이외 언어의 엔티티 성능이 향상되었습니다.

### 2018년 12월 14일
{: #14-december-2018}

- 이제 IBM Cloud 런던 위치에 {{site.data.keyword.nlushort}} 서비스 인스턴스를 작성할 수 있습니다.
- 포르투갈어 관계에 대한 지원이 추가되었습니다.
- 이탈리아어 관계에 대한 지원이 추가되었습니다.
- 최대 10개까지 리턴되는 카테고리 수를 제어하는 카테고리 요청의 `limit` 매개변수가 추가되었습니다.
- 일본어와 독일어 감성의 정확도가 향상되었습니다.

### 2018년 12월 6일
{: #6-december-2018}

- 이탈리아어 카테고리, 키워드, 엔티티 및 카테고리의 정확도가 향상되었습니다.

### 2018년 11월 27일
{: #27-november-2018}

- 영어, 프랑스어, 일본어 및 포르투갈어 입력의 키워드 결과 품질이 향상되었습니다.
- 여러 다른 대소문자가 포함된 키워드는 이제 결과에서 같은 키워드로 표시됩니다.
- **모델 가져오기** 메소드에서는 이제 여러 배치 간에 사용자 정의 모델을 관리하는 데 사용할 수 있는 추가 필드를 리턴합니다.
  - `version`: {{site.data.keyword.knowledgestudioshort}}의 사용자 제공 버전 문자열
  - `version_description`: {{site.data.keyword.knowledgestudioshort}}의 이 버전에 관한 사용자 제공 설명(예: 이전 버전 이후 변경된 내용)
  - `workspace_id`: 동일한 {{site.data.keyword.knowledgestudioshort}} 작업공간에서 반복적으로 배치될 때 일관된 상태로 남아 있는 {{site.data.keyword.knowledgestudioshort}}에서 제공하는 ID
  - `created`: 모델을 NLU에 배치하는 시기를 나타내는 Datetime 문자열

### 2018년 11월 16일
{: #16-november-2018}

- 정확도와 성능을 향상시키기 위해 영어 키워드와 감성을 위한 새 알고리즘을 릴리스했습니다.
- 영어, 프랑스어, 일본어 및 포르투갈어 입력의 키워드 정확도와 성능이 향상되었습니다.
- 큰 텍스트 샘플의 정확도 향상을 포함하여 이탈리아어 감성 정확도와 성능이 향상되었습니다.
- URL 인코딩 텍스트가 스페인어 엔티티의 명확한 결과에 표시되게 만든 버그를 수정했습니다.
- 최신 엔티티 유형 시스템이 포함된 새로운 이탈리아어 엔티티 모델을 릴리스했습니다. [엔티티 유형 및 하위 유형(버전 2)](entity-types-v2.html) 페이지에서 최신 유형 시스템에 관해 알아볼 수 있습니다. 애플리케이션이 새 유형 시스템과 호환 가능하면 새 모델을 사용하도록 요청에서 버전 날짜 매개변수를 `2018-11-16`으로 변경하십시오.

### 2018년 11월 9일
{: #9-november-2018}

- 지원되는 모든 언어에서 카테고리의 정확도가 상당히 향상되었습니다.

### 2018년 11월 8일
{: #8-november-2018}

- 이제 IBM Cloud 도쿄 위치에 {{site.data.keyword.nlushort}} 서비스 인스턴스를 작성할 수 있습니다.

### 2018년 11월 5일
{: #5-november-2018}

- 이탈리아어 개념에 대한 지원이 추가되었습니다.

### 2018년 10월 30일	
{: #30-october-2018}	

2018년 10월 30일 현재 독일 및 미국 남부 지역에서 작성한 새 서비스 인스턴스에서 [IAM(Identity and Access Management) 인증](#iam-auth-process)을 사용합니다.	

### 2018년 9월 21일
{: #21-september-2018}

- 프랑스어 관계와 포르투갈어 개념에 대한 지원이 추가되었습니다.
- 대상이 지정된 감성 옵션이 이제 프랑스어와 포르투갈어 키워드에 지원됩니다.
- 프랑스어 키워드가 향상되었습니다.
- 한국어 감성이 향상되었습니다.
- 포르투갈어 키워드와 감성이 향상되었습니다.
- 최신 엔티티 유형 시스템이 포함된 새로운 포르투갈어 엔티티 모델을 릴리스했습니다. [엔티티 유형 및 하위 유형(버전 2)](entity-types-v2.html) 페이지에서 최신 유형 시스템에 관해 알아볼 수 있습니다. 애플리케이션이 새 유형 시스템과 호환 가능하면 새 모델을 사용하도록 요청에서 버전 날짜 매개변수를 `2018-09-21`로 변경하십시오. 

### 2018년 6월 26일
{: #26-june-2018}

일본어 엔티티와 키워드에 대한 지원이 추가되었습니다.

- 일본어 입력의 경우 다음 엔티티는 아직 지원되지 않습니다.
  - 숫자
  - 백분율
  - 전화번호
  - URL
- 일본어 입력의 IPv6 주소는 아직 IPAddress 엔티티로 감지될 수 없습니다.

### 2018년 6월 12일
{: #12-june-2018}

2018년 6월 12일 현재 미국 동부 지역에서 작성한 새 서비스 인스턴스에서 [IAM(Identity and Access Management) 인증](#iam-auth-process)을 사용합니다.

### 2018년 6월 6일
{: #06-june-2018}

- 한국어 카테고리 결과가 상당히 향상되었습니다.

### 2018년 5월 29일
{: #29-may-2018}

2018년 5월 29일 현재 시드니 지역에서 작성한 새 서비스 인스턴스에서 [IAM(Identity and Access Management) 인증](#iam-auth-process)을 사용합니다.

### 2018년 5월 9일
{: #9-may-2018}

- 독일어 엔티티가 향상되었습니다.

### 2018년 5월 4일
{: #4-may-2018}

- 일본어 감성과 시맨틱 역할에 대한 지원이 추가되었습니다.
- 메타데이터 요청의 성능이 향상되었습니다.
- `NAN` 관련성 점수를 일부 엔티티 결과에 표시하게 만든 버그를 수정했습니다.
- `500` 오류 코드가 더 적합한 상황에서 독일어와 한국어 키워드 요청에 `400` 오류 코드를 리턴하는 버그를 수정했습니다.


### 2018년 4월 19일
{: #19-april-2018}

- 일본어 관계에 대한 지원이 추가되었습니다.
- 독일어 키워드가 향상되었습니다.
- 잘못된 엔티티 멘션 텍스트를 리턴하게 만든 버그를 수정했습니다.
- 대상으로 지정된 감성의 저조한 결과를 초래할 수 있는 버그를 수정했습니다.
- 리턴된 `analyzed_text`에 분석되지 않은 문자가 포함되게 만든 버그를 수정했습니다.


### 2018년 4월 5일
{: #05-april-2018}

- 웹 페이지 컨텐츠 페칭이 향상되었습니다. `url` 매개변수를 사용하여 웹 페이지를 분석하는 경우 프레임 세트와 쿠키를 사용하는 웹 페이지에서 특히 결과가 향상됩니다.
- 한국어 개념이 상당히 향상되었습니다.

### 2018년 3월 16일
{: #03-march-2018}

- 독일어 카테고리, 관계 및 시맨틱 역할에 대한 지원이 추가되었습니다.
  - 새로운 관계 유형 시스템은 독일어 관계에 사용합니다. 자세한 내용을 보려면 [관계 유형(버전 2)](relations-v2.html) 페이지를 참조하십시오.
- 향상된 독일어 키워드와 감성.
- 일본어 카테고리와 개념에 대한 지원 추가.
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

- 독일어 개념에 대한 지원 추가.

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

- **[한국어 지원](language-support.html#korean)**이 다음 기능을 포함하도록 확장되었습니다.

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

- 자세한 가격 정보는 {{site.data.keyword.cloud}} 카탈로그에 있는 [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding)의 내용을 참조하십시오.

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

Natural Language Understanding 서비스가 이제 GA되었습니다.
