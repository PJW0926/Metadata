# Educational Digital Games Metadata Schema

## 1. Opening Narrative

EDGMS는 디지털 게임을 교육 현장에서 더 쉽게 비교하고, 선택하고, 활용할 수 있도록 하기 위해 설계되었다. 기존 게임 메타데이터 요소는 게임의 기본적인 식별 정보는 제공할 수 있지만, 교육 수준, 학습 목표, 주제 분야와 같은 교육적 활용 정보를 충분히 설명하기 어렵다. EDGMS는 이러한 도메인 특화 요소를 구조화하여 교사, 사서, 교육 연구자, 학생이 특정 수업 목적이나 학습 환경에 적합한 게임을 판단할 수 있도록 돕는다.

교육용 디지털 게임 분야에서 메타데이터가 필요한 이유는 이용자가 게임을 특정 교육 목적과 학습 상황에 맞는 자료로 선택해야 하기 때문이다. 교사라면 특정 학년, 교과목, 수업 목표, 사용 가능한 플랫폼, 개인 활동 또는 협동 활동 여부, 가격 모델 등을 기준으로 게임을 평가해야 한다. 연구자는 게임의 학습의 효과를 분석하기 위해 교육 수준, 상호작용 방식, 학습 목표 등을 비교해야 한다. 학부모와 사서도 아동이나 이용자에게 적합한 교육용 게임을 선별하기 위해 체계적인 설명 정보가 필요하다.

처음 Draft 1과 Draft 2에서는 병원, 의학 정보센터, 치매 관련 정보자원과 같은 의료 정보 도메인을 고려했다. 그러나 해당 도메인은 전문적인 의학 지식과 실제 의료 정보 표준에 대한 높은 이해가 요구되어, 한 학기 프로젝트 기간 내에 충분히 설계하기 어렵다고 판단하였다. 이후 Draft 3과 Draft 4에서는 나의 평소 관심사를 반영해, 교육 현장에서 실제로 활용될 수 있는 교육용 디지털 게임으로 도메인을 변경하였다. 

EDGMS 설계에서 가장 중요하게 고려한 점은 상호운용성과 도메인 특화성의 균형이다. 제목, 제작자, 발행자, 설명, 언어, 발행일, 주제와 같은 일반적인 설명 요소는 널리 사용되는 DCMI Terms를 재사용하였다. 반면 교육 수준, 학습 목표, 게임 장르, 플랫폼, 플레이 방식, 교육적 활용 유형, 상호작용 유형, 가격 모델처럼 교육용 디지털 게임의 특성을 설명하는 요소는 local EDGMS namespace로 정의하였다. 이를 통해 기본적인 메타데이터 상호운용성을 유지하면서도, 교육용 게임이라는 도메인에 필요한 세부 정보를 표현할 수 있도록 했다. 도메인 특화 요소를 개발할 때는 이용자가 이를 직관적으로 이해할 수 있는지, 활용도가 높은지, 다른 요소와 겹치지 않는지에 초점을 두어 선별했다.

## 2. Relevant Metadata Standards

# Dublin Core / DCMI Terms

DCMI Terms는 다양한 정보자원을 기술하는 데 널리 사용되는 일반 설명 메타데이터 표준이다. EDGMS에서는 교육용 디지털 게임의 기본적인 서지 및 설명 정보를 표현하기 위해 DCMI Terms를 재사용하였다. 구체적으로 dcterms:title, dcterms:creator, dcterms:publisher, dcterms:description, dcterms:language, dcterms:issued, dcterms:subject를 사용하였다.

이 요소들은 다양한 자원 유형에서 공통적으로 사용될 수 있기 때문에, 새로 정의하기보다 기존 표준을 재사용하는 것이 적절하다고 판단하였다. 이를 통해 다른 메타데이터 시스템과의 이해 가능성과 상호운용성을 높일 수 있다.

# IEEE Learning Object Metadata / LOM

IEEE LOM은 학습 객체를 설명하기 위한 대표적인 교육 메타데이터 표준이다. LOM은 학습 자원의 일반 정보, 기술적 조건, 교육적 맥락, 상호작용 방식, 저작권, 분류 정보 등을 기술할 수 있도록 구성되어 있다.

EDGMS는 IEEE LOM의 요소를 XSD에서 직접 참조(import)하지는 않았지만, 교육용 디지털 게임을 학습 자원으로 설명한다는 관점에서 LOM의 개념을 참고하였다. 특히 edgms:educationalLevel, edgms:interactivityType, edgms:educationalUseType과 같은 요소는 LOM의 교육적 맥락, 상호작용 유형, 학습 자원 유형과 관련된 개념을 교육용 디지털 게임 환경에 맞게 재해석한 것이다.

# Local EDGMS Namespace

Local EDGMS namespace는 교육용 디지털 게임 도메인에 특화된 요소를 표현하기 위해 사용하였다. Dublin Core만으로는 교육용 게임의 학습 맥락, 게임적 특성, 사용 환경을 충분히 설명하기 어렵기 때문이다.

EDGMS에서 새롭게 정의한 요소는 edgms:educationalLevel, edgms:learningObjective, edgms:genre, edgms:platform, edgms:playMode, edgms:educationalUseType, edgms:interactivityType, edgms:pricingModel이다. 이 요소들은 이용자가 교육용 게임을 선택할 때 필요로 하는 정보를 중심으로 설계하였다.

# XML Schema / XSD

XML Schema는 EDGMS의 구조와 검증 규칙을 기계가 처리할 수 있는 형식으로 표현하기 위해 사용하였다. XSD는 각 요소의 순서, 필수 여부, 반복 가능 여부, 데이터 타입, controlled vocabulary 제약을 정의한다. 이를 통해 XML 레코드가 EDGMS의 구조를 제대로 따르는지 검증할 수 있다.

또한 XSD 파일에는 xs:documentation annotation를 포함하여 각 요소가 어떤 의도로 설계되었는지 설명하였다. 

## 3. Vocabulary Specification

EDGMS는 총 15개의 주요 요소로 구성된다. 이 중 7개는 DCMI Terms에서 재사용한 일반 설명 요소이고, 8개는 교육용 디지털 게임 도메인에 맞게 새롭게 정의한 EDGMS 요소이다.

### 3.1 Element Overview Table

| No. | Element Name | Brief Definition |
|---|---|---|
| 1 | `dcterms:title` | 게임의 공식 명칭 |
| 2 | `dcterms:creator` | 게임을 개발한 개발자, 개발팀, 스튜디오 |
| 3 | `dcterms:publisher` | 게임을 배포하거나 공개한 회사, 기관 |
| 4 | `dcterms:description` | 게임의 내용, 중심 메커니즘에 대한 간략한 설명 |
| 5 | `dcterms:language` | 게임에서 지원하는 언어 |
| 6 | `dcterms:issued` | 게임이 처음 공개되거나 출시된 날짜 |
| 7 | `dcterms:subject` | 게임이 다루는 학문 분야 또는 교과 영역 |
| 8 | `edgms:educationalLevel` | 게임이 대상으로 하는 교육 단계 또는 학년 범위 |
| 9 | `edgms:learningObjective` | 게임을 통해 달성하고자 하는 구체적인 학습 목표 |
| 10 | `edgms:genre` | 게임의 주요 장르 |
| 11 | `edgms:platform` | 게임을 실행하거나 접속할 수 있는 기기, 운영체제, 웹 환경 |
| 12 | `edgms:playMode` | 싱글 플레이, 협동 플레이, 경쟁 플레이, 학급 단위 활동 여부 |
| 13 | `edgms:educationalUseType` | 게임이 교육적으로 활용되는 유형 |
| 14 | `edgms:interactivityType` | 학습자가 게임 콘텐츠와 상호작용하는 주요 방식 |
| 15 | `edgms:pricingModel` | 이용자 또는 기관이 게임을 이용할 수 있는 가격 및 접근 모델 |

### 3.2 Full Data Dictionary

#### Element 1: Title

| Field                   | Detail                                                                       |
| ----------------------- | ---------------------------------------------------------------------------- |
| Element Name            | Title                                                                        |
| Label                   | Game Title                                                                   |
| URI                     | `http://purl.org/dc/terms/title`                                             |
| Definition              | The official name of the object as designated by its creator or publisher.   |
| Data Values             | Free text string                                                             |
| Cardinality: Mandatory  | Yes                                                                          |
| Cardinality: Repeatable | No                                                                           |
| Comments                | Alternative titles or localized titles may be recorded separately if needed. |
| Example                 | Minecraft: Education Edition                                                 |

#### Element 2: Creator

| Field                   | Detail                                                                                                                                     |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Element Name            | Creator                                                                                                                                    |
| Label                   | Game Creator / Developer                                                                                                                   |
| URI                     | `http://purl.org/dc/terms/creator`                                                                                                         |
| Definition              | The individual, team, company, or studio primarily responsible for designing and developing the game.                                      |
| Data Values             | Free text string; use an authorized form of name where possible.                                                                           |
| Cardinality: Mandatory  | Yes                                                                                                                                        |
| Cardinality: Repeatable | Yes                                                                                                                                        |
| Comments                | This element is distinct from Publisher. If the creator and publisher are the same organization, both elements may contain the same value. |
| Example                 | Mojang Studios                                                                                                                             |

#### Element 3: Publisher

| Field                   | Detail                                                                                                                |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Element Name            | Publisher                                                                                                             |
| Label                   | Publisher                                                                                                             |
| URI                     | `http://purl.org/dc/terms/publisher`                                                                                  |
| Definition              | The company, organization, or institution responsible for distributing or making the game publicly available.         |
| Data Values             | Free text string                                                                                                      |
| Cardinality: Mandatory  | No                                                                                                                    |
| Cardinality: Repeatable | Yes                                                                                                                   |
| Comments                | In cases where the developer self-publishes the game, the same organization may appear in both Creator and Publisher. |
| Example                 | Microsoft                                                                                                             |

#### Element 4: Description

| Field                   | Detail                                                                                                                                                                                                     |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Element Name            | Description                                                                                                                                                                                                |
| Label                   | Game Description                                                                                                                                                                                           |
| URI                     | `http://purl.org/dc/terms/description`                                                                                                                                                                     |
| Definition              | A concise textual summary of the game's content and core mechanics.                                                                                                                  |
| Data Values             | Free text string                                                                                                                                                                                           |
| Cardinality: Mandatory  | Yes                                                                                                                                                                                                        |
| Cardinality: Repeatable | No                                                                                                                                                                                                         |
| Comments                | The description should be written in plain language for educators and non-specialist users. Marketing language should be avoided.                                                                          |
| Example                 | Minecraft: Education Edition is a sandbox game in which students build structures, explore environments, and complete teacher-designed lessons across subjects including STEM, history, and language arts. |

#### Element 5: Language

| Field                   | Detail                                                                              |
| ----------------------- | ----------------------------------------------------------------------------------- |
| Element Name            | Language                                                                            |
| Label                   | Available Language(s)                                                               |
| URI                     | `http://purl.org/dc/terms/language`                                                 |
| Definition              | The language(s) in which the game's interface, text, or audio content is available. |
| Data Values             | ISO 639-1 two-letter language codes                                                 |
| Cardinality: Mandatory  | No                                                                                  |
| Cardinality: Repeatable | Yes                                                                                 |
| Comments                | Multiple values may be used when the game supports multiple languages.              |
| Example                 | en; ko                                                                              |

#### Element 6: Issued

| Field                   | Detail                                                                     |
| ----------------------- | -------------------------------------------------------------------------- |
| Element Name            | Issued                                                                     |
| Label                   | Release Date                                                               |
| URI                     | `http://purl.org/dc/terms/issued`                                          |
| Definition              | The original date on which the game was first publicly released or issued. |
| Data Values             | ISO 8601 date format, such as `YYYY-MM-DD` or `YYYY`                       |
| Cardinality: Mandatory  | No                                                                         |
| Cardinality: Repeatable | No                                                                         |
| Comments                | If the exact date is unknown, the year alone may be used.                  |
| Example                 | 2016                                                                       |

#### Element 7: Subject

| Field                   | Detail                                                                                                                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Element Name            | Subject                                                                                                                                                                                           |
| Label                   | Subject Area                                                                                                                                                                                      |
| URI                     | `http://purl.org/dc/terms/subject`                                                                                                                                                                |
| Definition              | The academic subject area or knowledge domain that the game addresses or supports.                                                                                                                |
| Data Values             | Controlled vocabulary; see Appendix A                                                                                                                                                             |
| Cardinality: Mandatory  | Yes                                                                                                                                                                                               |
| Cardinality: Repeatable | Yes                                                                                                                                                                                               |
| Comments                | Multiple subject values may be used. Because this element is reused from DCMI Terms, the local EDGMS vocabulary is documented as a recommended value list rather than as a newly defined element. |
| Example                 | Mathematics; Science                                                                                                                                                                              |

#### Element 8: Educational Level

| Field                   | Detail                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------- |
| Element Name            | EducationalLevel                                                                                  |
| Label                   | Educational Level                                                                                 |
| URI                     | `http://edgms.org/schema/educationalLevel`                                                        |
| Definition              | The intended educational stage or grade range for which the game is designed or most appropriate. |
| Data Values             | Controlled vocabulary; see Appendix B                                                             |
| Cardinality: Mandatory  | Yes                                                                                               |
| Cardinality: Repeatable | Yes                                                                                               |
| Comments                | Multiple levels may be used when a game is appropriate for more than one age or grade range.      |
| Example                 | Elementary School (K-5); Middle School (6-8)                                                      |

#### Element 9: Learning Objective

| Field                   | Detail                                                                                                                                                               |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Element Name            | LearningObjective                                                                                                                                                    |
| Label                   | Learning Objective                                                                                                                                                   |
| URI                     | `http://edgms.org/schema/learningObjective`                                                                                                                          |
| Definition              | A statement describing the specific knowledge, skill, or competency that learners are expected to develop through engagement with the game.                          |
| Data Values             | Free text string                                                                                                                                                     |
| Cardinality: Mandatory  | No                                                                                                                                                                   |
| Cardinality: Repeatable | Yes                                                                                                                                                                  |
| Comments                | Learning objectives should be written clearly and may follow an action-verb format. They may also be aligned with instructional frameworks such as Bloom's Taxonomy. |
| Example                 | Students will be able to apply basic algebraic reasoning to solve in-game puzzles.                                                                                   |

#### Element 10: Genre

| Field                   | Detail                                                                                                |
| ----------------------- | ----------------------------------------------------------------------------------------------------- |
| Element Name            | Genre                                                                                                 |
| Label                   | Game Genre                                                                                            |
| URI                     | `http://edgms.org/schema/genre`                                                                       |
| Definition              | The gameplay or activity category that characterizes the primary mechanics and structure of the game. |
| Data Values             | Controlled vocabulary; see Appendix C                                                                 |
| Cardinality: Mandatory  | Yes                                                                                                   |
| Cardinality: Repeatable | Yes                                                                                                   |
| Comments                | A game may belong to more than one genre.                                                             |
| Example                 | Sandbox; Simulation                                                                                   |

#### Element 11: Platform

| Field                   | Detail                                                                                                 |
| ----------------------- | ------------------------------------------------------------------------------------------------------ |
| Element Name            | Platform                                                                                               |
| Label                   | Platform / Device                                                                                      |
| URI                     | `http://edgms.org/schema/platform`                                                                     |
| Definition              | The hardware device, operating system, or web environment on which the game can be accessed or played. |
| Data Values             | Controlled vocabulary; see Appendix D                                                                  |
| Cardinality: Mandatory  | Yes                                                                                                    |
| Cardinality: Repeatable | Yes                                                                                                    |
| Comments                | Browser-based games should be listed as Web Browser rather than by operating system alone.             |
| Example                 | Windows; macOS; iOS                                                                                    |

#### Element 12: Play Mode

| Field                   | Detail                                                                                                                                               |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Element Name            | PlayMode                                                                                                                                             |
| Label                   | Play Mode                                                                                                                                            |
| URI                     | `http://edgms.org/schema/playMode`                                                                                                                   |
| Definition              | Describes whether the game is designed for individual play, cooperative group play, competitive multiplayer interaction, or classroom-wide activity. |
| Data Values             | Controlled vocabulary; see Appendix E                                                                                                                |
| Cardinality: Mandatory  | No                                                                                                                                                   |
| Cardinality: Repeatable | Yes                                                                                                                                                  |
| Comments                | Classroom-wide refers to games or platforms where a single activity is shared across an entire class simultaneously.                                 |
| Example                 | Single-player; Cooperative Multiplayer                                                                                                               |

#### Element 13: Educational Use Type

| Field                   | Detail                                                                                                                                                                                                       |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Element Name            | EducationalUseType                                                                                                                                                                                           |
| Label                   | Educational Use Type                                                                                                                                                                                         |
| URI                     | `http://edgms.org/schema/educationalUseType`                                                                                                                                                                 |
| Definition              | Indicates the educational role or category of the digital game, game-based tool, or interactive learning environment.                                                                                        |
| Data Values             | Controlled vocabulary; see Appendix F                                                                                                                                                                        |
| Cardinality: Mandatory  | Yes                                                                                                                                                                                                          |
| Cardinality: Repeatable | No                                                                                                                                                                                                           |
| Comments                | This element distinguishes between games originally designed for education, gamified learning platforms, commercial games repurposed for educational use, and programming or creative learning environments. |
| Example                 | Commercial Game Repurposed for Education                                                                                                                                                                     |

#### Element 14: Interactivity Type

| Field                   | Detail                                                                                                                                                                    |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Element Name            | InteractivityType                                                                                                                                                         |
| Label                   | Interactivity Type                                                                                                                                                        |
| URI                     | `http://edgms.org/schema/interactivityType`                                                                                                                               |
| Definition              | The primary mode through which a learner interacts with the game content.                                                                                                 |
| Data Values             | Controlled vocabulary; see Appendix G                                                                                                                                     |
| Cardinality: Mandatory  | No                                                                                                                                                                        |
| Cardinality: Repeatable | No                                                                                                                                                                        |
| Comments                | Active means the learner must perform tasks; Expositive means the learner primarily receives content; Mixed refers to a combination of active and expositive interaction. |
| Example                 | Active                                                                                                                                                                    |

#### Element 15: Pricing Model

| Field                   | Detail                                                                                                                                                       |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Element Name            | PricingModel                                                                                                                                                 |
| Label                   | Pricing Model / Access                                                                                                                                       |
| URI                     | `http://edgms.org/schema/pricingModel`                                                                                                                       |
| Definition              | The pricing or access model through which the game is obtained by users or institutions.                                                                     |
| Data Values             | Controlled vocabulary; see Appendix H                                                                                                                        |
| Cardinality: Mandatory  | No                                                                                                                                                           |
| Cardinality: Repeatable | No                                                                                                                                                           |
| Comments                | Freemium refers to games with a free base version and paid premium features. Institutional License applies to school-wide or district-wide licensing models. |
| Example                 | Institutional License                                                                                                                                        |

### 3.3 Controlled Vocabularies

EDGMS는 값의 일관성을 높이기 위해 여러 요소에 controlled vocabulary를 적용하였다. Controlled vocabulary는 이용자가 같은 개념을 서로 다른 표현으로 입력하는 문제를 줄이고, 검색과 필터링의 정확성을 높이기 위해 사용된다.

사용한 controlled vocabularies는 다음과 같다.

#### Appendix A — Subject Area

Recommended values for `dcterms:subject`:

* Mathematics
* Science
* Language Arts
* Social Studies
* History
* Geography
* Computer Science
* Foreign Language
* Art
* Music
* Physical Education
* Career Education
* General
* Other

dcterms:subject는 외부 DCMI Terms 스키마에서 재사용한 요소이므로, EDGMS의 로컬 권장사항으로 문서화하였다.

#### Appendix B — Educational Level

Allowed values for `edgms:educationalLevel`:

* Early Childhood (Pre-K)
* Elementary School (K-5)
* Middle School (6-8)
* High School (9-12)
* Undergraduate
* Lifelong Learning
* All Ages

#### Appendix C — Game Genre

Allowed values for `edgms:genre`:

* Puzzle
* Simulation
* Role-Playing Game (RPG)
* Strategy
* Sandbox
* Quiz
* Adventure
* Platformer
* Typing
* Language Learning
* Other

#### Appendix D — Platform

Allowed values for `edgms:platform`:

* Windows
* macOS
* Linux
* iOS
* Android
* Web Browser
* Nintendo Switch
* Other

#### Appendix E — Play Mode

Allowed values for `edgms:playMode`:

* Single-player
* Cooperative Multiplayer
* Competitive Multiplayer
* Classroom-wide

#### Appendix F — Educational Use Type

Allowed values for `edgms:educationalUseType`:

* Explicitly Educational Game
* Gamified Learning Platform
* Commercial Game Repurposed for Education
* Educational Programming Environment
* Gamified Learning Tool
* Other

#### Appendix G — Interactivity Type

Allowed values for `edgms:interactivityType`:

* Active
* Expositive
* Mixed

#### Appendix H — Pricing Model

Allowed values for `edgms:pricingModel`:

* Free
* Freemium
* Paid (One-time)
* Subscription-based
* Institutional License
* Open Educational Resource
* Other

## 4. XSD File

EDGMS의 전체 XSD 파일은 이 GitHub repository에 업로드하였다.

* [edgms.xsd](schema/edgms.xsd)

direct raw URL은 다음과 같다.

```text
https://raw.githubusercontent.com/PJW0926/Metadata/main/schema/edgms.xsd
```

이 XSD 파일은 EDGMS XML 레코드의 구조, 요소 순서, 데이터 타입, 필수 요소, 반복 가능 요소, controlled vocabulary 제약을 정의한다. 샘플 XML 레코드는 이 XSD 파일을 참조하여 validation할 수 있도록 구성하였다.

## 5. Sample XML Records

다음 샘플 XML 레코드는 실제 교육용 디지털 게임을 EDGMS로 기술한 예시이다.

* [Minecraft: Education Edition](examples/minecraft.xml)
* [Prodigy Math](examples/prodigymath.xml)

각 XML 레코드는 EDGMS XSD 구조를 따르도록 작성되었으며, 게임의 기본 설명 정보와 교육용 게임 특화 정보를 함께 포함한다.
