# DOM_Crawler

DOM 기반의 웹 크롤러 라이브러리를 사용해보고 응용해 보았습니다.

기존 라이브러리 사용시, 블로그 또는 뉴스 등 정형화된 구조에만 적합한 경우가 다수이며 사이트별로 적용되지 않는 사례가 많았습니다.

따라서, 모든 웹 사이트에서도 구조가 변하더라도 적용 가능한 크롤링 방법론을 개발하였습니다.

기본적인 아키텍처는 DOM 구조로 이루어진 웹 사이트의 특징을 활용하여 부모 노드로부터 할당된 모든 자식 노드들의 class명, id명, 태그명에 해당되는 값을 딕셔너리 형태로 저장합니다.

재귀적인 함수 호출을 통해 모든 노드를 부모 노드로 가정하며 진행됩니다.

## Prerequisites

- Python 3.6+
- pandas
- selenium
- lxml
- Autoscraper
- cetd
- body_text_extraction

## Process

The `directory` should look like:

    DOM_Crawler
    ├── 기존 라이브러리
    │   ├── DOM practice_github_ver1.ipynb
    │   ├── DOM practice_github_ver2.ipynb
    │   ├── Autoscraper_시행착오.ipynb
    │   ├── Autoscraper_적용_API리스트유지보수.ipynb
    │   └── groose3.ipynb
    │       
    └── 새 방법론
        ├── 1. 스크래핑 하고자 하는 URL 리스트를 수집한 경우 (뉴스).ipynb
        ├── 2. Selenium webdriver로 page_source 가져오는 경우 (comar).ipynb
        ├── Depth 기반의 크롤링.ipynb  
        └── 공공데이터_태그 기반 크롤링.ipynb

### 0. 개요

- 홈페이지에서 스크래핑/크롤링 을 통해 데이터 수집 시 다음과 같은 문제가 발생함

      1. 홈페이지의 구조가 조금 변하면 코드가 에러가 발생하여 수집 불가
      2. 새롭게 업데이트 될 시, 테이블 구조가 추가되면 대응 불가

      두 가지 원인은 데이터 수집에 있어 시간적으로 상당히 비효율
      실제로 크롤러 서비스를 제공하고자 한다면, 고객의 만족도가 저하되는 원인이 됨

- 따라서, [DOM Based Content Extraction via Text Density](http://www.ofey.me/papers/cetd-sigir11.pdf) 논문을 읽고 정리한 후, 관련 라이브러리를 공부

- 라이브러리별 한계를 정리하였고, 새로운 **재귀적 DOM 기반의 크롤링 기법**을 개발

## Author

HyoJun Kim / [blog](http://rlagywns0213.github.io/)
