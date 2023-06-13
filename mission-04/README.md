# Mission-04

---

- [Mission-04](#mission-04)
  - [General info](#general-info)
  - [Results](#results)
  - [Description](#description)

---

## General info

피그마로 주어진 Web Cafe 시안의 일부를 구현한 결과물.
그 중에서 새소식(그리드 활용) 부분입니다.

---

## Results

1. Grid

![Grid_result1](./result1.png)
![Grid_result2](./result2.png)

---

## Description

- HTML 돔 트리

```
main
└── section.news
    ├── h2.news-title
    ├── div.news-more-wrapper
    │   └── a.news-more
    │       └── img
    ├── div.divider[aria-label]
    ├── figure.news-image
    │   ├── img
    │   └── figcaption
    └── div.news-contents
        ├── h3
        ├── p
        └── p




```

- 마크업

  - grid container로 뉴스 섹션을 두고, 그 밑에 5개의 grid-area(title / more / divider / more / contents)로 분리하였습니다.
  - divider div는 aria-label을 통해 스크린 리더 사용자에게 구분선이라는 정보를 제공하게끔 했습니다.

- 레이아웃

  - 그리드
    - container
      ```
       .news{
        display: grid;
        grid-template-columns: repeat(12, 1fr);
        grid-template-rows: auto;
        gap: 12px;
        grid-template-areas:
          "title title . . . . . . . . more more"
          "divider divider divider divider divider divider divider divider divider . . ."
          "image image image image contents contents contents contents contents contents contents contents";
          }
      ```
    - item: area 5개
      ```
       .news-title {
         grid-area: title;
       }
       .news-more-wrapper {
         grid-area: more;
       }
       .divider {
         grid-area: divider;
       }
       .news-image {
         grid-area: image;
       }
       .news-contents {
         grid-area: contents;
       }
      ```
  - 기타

    - 공통되는 부분은 변수로 처리해봤습니다.
      (font-size, line-height)

      ```
      :root {
      --main-font-size: 14px;
      --main-line-height: 150%;
      }

      main {
        font-size: var(--main-font-size);
        line-height: var(--main-line-height);
      }
      ```
