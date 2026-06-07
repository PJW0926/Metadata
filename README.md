# Educational Digital Games Metadata Schema

## 1. Opening Narrative

EDGMS(Educational Digital Games Metadata Schema)는 교육용 디지털 게임, 게임화된 학습 플랫폼, 그리고 교육 현장에서 활용되는 상호작용형 학습 환경을 기술하기 위해 설계한 메타데이터 스키마이다. 이 도메인의 자료들은 단순한 게임이 아니라 디지털 미디어, 소프트웨어, 학습 도구, 수업 활동의 성격을 동시에 가진다. 따라서 제목, 제작자, 발행자와 같은 일반적인 서지 정보만으로는 교육 현장에서 필요한 정보를 충분히 설명하기 어렵다.

교육용 디지털 게임 분야에서 메타데이터가 필요한 이유는 이용자가 게임을 단순히 “재미있는 콘텐츠”로 찾는 것이 아니라, 특정 교육 목적과 학습 상황에 맞는 자료로 선택해야 하기 때문이다. 예를 들어 교사는 특정 학년, 교과목, 수업 목표, 사용 가능한 플랫폼, 개인 활동 또는 협동 활동 여부, 가격 모델 등을 기준으로 게임을 평가해야 한다. 연구자는 게임 기반 학습의 효과를 분석하기 위해 게임의 장르, 상호작용 방식, 학습 목표 등을 체계적으로 비교할 필요가 있다. 학부모와 사서 역시 아동이나 이용자에게 적합한 교육용 게임을 선별하기 위해 구조화된 설명 정보를 필요로 한다.

이 스키마의 주요 이용자는 교육용 게임을 수업에 활용하려는 교사, 게임 기반 학습을 연구하는 연구자, 교육 콘텐츠를 설계하는 instructional designer이다. 부차적 이용자로는 자녀에게 적절한 교육용 게임을 찾는 학부모, 그리고 교육용 디지털 미디어 컬렉션을 관리하는 사서와 디지털 아키비스트를 상정하였다.

처음 Draft 1과 Draft 2에서는 병원, 의학 정보센터, 치매 관련 정보자원과 같은 의료 정보 도메인을 고려하였다. 그러나 해당 도메인은 전문적인 의학 지식과 실제 의료 정보 표준에 대한 높은 이해가 요구되어, 한 학기 프로젝트 범위 안에서 충분히 설계하기 어렵다고 판단하였다. 이후 Draft 3과 Draft 4에서는 교육 현장에서 실제로 활용될 수 있는 교육용 디지털 게임으로 도메인을 변경하였다. 이 변경을 통해 보다 명확한 이용자 집단과 실제적인 검색·선택 상황을 설정할 수 있었다.

EDGMS 설계에서 가장 중요하게 고려한 점은 상호운용성과 도메인 특화성의 균형이다. 제목, 제작자, 발행자, 설명, 언어, 발행일, 주제와 같은 일반적인 설명 요소는 널리 사용되는 DCMI Terms를 재사용하였다. 반면 교육 수준, 학습 목표, 게임 장르, 플랫폼, 플레이 방식, 교육적 활용 유형, 상호작용 유형, 가격 모델처럼 교육용 디지털 게임의 특성을 설명하는 요소는 local EDGMS namespace로 정의하였다. 이를 통해 기본적인 메타데이터 상호운용성을 유지하면서도, 교육용 게임이라는 도메인에 필요한 세부 정보를 표현할 수 있도록 하였다.

## 2. Relevant Metadata Standards

### Dublin Core / DCMI Terms

DCMI Terms는 다양한 정보자원을 기술하는 데 널리 사용되는 일반적인 설명 메타데이터 표준이다. EDGMS에서는 기본적인 서지 및 설명 정보를 표현하기 위해 DCMI Terms를 재사용하였다. 구체적으로 `dcterms:title`, `dcterms:creator`, `dcterms:publisher`, `dcterms:description`, `dcterms:language`, `dcterms:issued`, `dcterms:subject`를 사용하였다.

이 요소들은 교육용 디지털 게임에만 한정되지 않고 다양한 자원 유형에서 공통적으로 사용될 수 있기 때문에, EDGMS에서 새롭게 정의하기보다 기존 표준을 재사용하는 것이 적절하다고 판단하였다. 이를 통해 다른 메타데이터 시스템과의 이해 가능성과 상호운용성을 높일 수 있다.

### Local EDGMS Namespace

Local EDGMS namespace는 교육용 디지털 게임 도메인에 특화된 요소를 표현하기 위해 사용하였다. Dublin Core만으로는 교육용 게임의 학습 맥락, 게임적 특성, 사용 환경을 충분히 설명하기 어렵기 때문이다.

EDGMS에서 새롭게 정의한 요소는 `edgms:educationalLevel`, `edgms:learningObjective`, `edgms:genre`, `edgms:platform`, `edgms:playMode`, `edgms:educationalUseType`, `edgms:interactivityType`, `edgms:pricingModel`이다. 이 요소들은 이용자가 교육용 게임을 선택할 때 실제로 필요로 하는 정보를 중심으로 설계하였다.

### XML Schema / XSD

XML Schema는 EDGMS의 구조와 검증 규칙을 기계가 처리할 수 있는 형식으로 표현하기 위해 사용하였다. XSD는 각 요소의 순서, 필수 여부, 반복 가능 여부, 데이터 타입, controlled vocabulary 제약을 정의한다. 이를 통해 XML 레코드가 EDGMS의 구조를 제대로 따르는지 검증할 수 있다.

또한 XSD 파일에는 `xs:documentation` annotation과 design-intent comment를 포함하여 각 요소가 어떤 의도로 설계되었는지 설명하였다. 이는 스키마를 실제로 구현하려는 이용자가 요소의 의미와 사용 방식을 이해하는 데 도움을 준다.


## 3. Vocabulary Specification

EDGMS는 총 15개의 주요 요소로 구성된다. 이 중 7개는 DCMI Terms에서 재사용한 일반 설명 요소이고, 8개는 교육용 디지털 게임 도메인에 맞게 새롭게 정의한 EDGMS 요소이다.

### 3.1 Element Overview Table

| No. | Element Name | Brief Definition |
|---|---|---|
| 1 | `dcterms:title` | 게임의 공식 명칭 |
| 2 | `dcterms:creator` | 게임을 개발한 개발자, 개발팀, 또는 스튜디오 |
| 3 | `dcterms:publisher` | 게임을 배포하거나 공개한 회사 또는 기관 |
| 4 | `dcterms:description` | 게임의 내용, 플레이 방식, 교육적 목적에 대한 간략한 설명 |
| 5 | `dcterms:language` | 게임에서 지원하는 언어 |
| 6 | `dcterms:issued` | 게임이 처음 공개되거나 출시된 날짜 |
| 7 | `dcterms:subject` | 게임이 다루는 학문 분야 또는 교과 영역 |
| 8 | `edgms:educationalLevel` | 게임이 대상으로 하는 교육 단계 또는 학년 범위 |
| 9 | `edgms:learningObjective` | 게임을 통해 달성하고자 하는 구체적인 학습 목표 |
| 10 | `edgms:genre` | 게임의 주요 장르 또는 활동 유형 |
| 11 | `edgms:platform` | 게임을 실행하거나 접근할 수 있는 기기, 운영체제, 웹 환경 |
| 12 | `edgms:playMode` | 개인 플레이, 협동 플레이, 경쟁 플레이, 학급 단위 활동 여부 |
| 13 | `edgms:educationalUseType` | 게임이 교육적으로 활용되는 방식 또는 유형 |
| 14 | `edgms:interactivityType` | 학습자가 게임 콘텐츠와 상호작용하는 주요 방식 |
| 15 | `edgms:pricingModel` | 이용자 또는 기관이 게임을 이용할 수 있는 가격 및 접근 모델 |

### 3.2 Full Data Dictionary

이 섹션에는 Draft 3에서 작성한 전체 data dictionary를 넣는다. 각 요소는 다음 항목을 포함하도록 구성한다.

- Element Name
- Label
- URI
- Definition
- Data Values
- Cardinality: Mandatory
- Cardinality: Repeatable
- Comments
- Example

### 3.3 Controlled Vocabularies

EDGMS는 값의 일관성을 높이기 위해 여러 요소에 controlled vocabulary를 적용하였다. Controlled vocabulary는 이용자가 같은 개념을 서로 다른 표현으로 입력하는 문제를 줄이고, 검색과 필터링의 정확성을 높이기 위해 사용된다.

사용한 controlled vocabularies는 다음과 같다.

- Subject Area
- Educational Level
- Game Genre
- Platform
- Play Mode
- Educational Use Type
- Interactivity Type
- Pricing Model

각 controlled vocabulary의 세부 값은 Draft 3의 Appendix A-H에 제시한 목록을 사용한다.

## 4. XSD File

EDGMS의 전체 XSD 파일은 이 GitHub repository에 업로드하였다.

- [edgms.xsd](schema/edgms.xsd)

검증을 위한 direct raw URL은 다음과 같다.

```text
https://raw.githubusercontent.com/USERNAME/REPOSITORY/main/schema/edgms.xsd

이 XSD 파일은 EDGMS XML 레코드의 구조, 요소 순서, 데이터 타입, 필수 요소, 반복 가능 요소, controlled vocabulary 제약을 정의한다. 샘플 XML 레코드는 이 XSD 파일을 참조하여 validation할 수 있도록 구성하였다.

# 5. Sample XML Records

다음 샘플 XML 레코드는 실제 교육용 디지털 게임을 EDGMS로 어떻게 기술할 수 있는지 보여준다.

Minecraft: Education Edition
Prodigy Math

각 XML 레코드는 EDGMS XSD 구조를 따르도록 작성되었으며, 게임의 기본 설명 정보와 교육용 게임 특화 정보를 함께 포함한다. 예를 들어 Minecraft: Education Edition 레코드는 제목, 제작자, 발행자, 설명, 언어, 발행일, 주제뿐 아니라 교육 수준, 학습 목표, 장르, 플랫폼, 플레이 방식, 교육적 활용 유형, 상호작용 유형, 가격 모델을 포함한다.
