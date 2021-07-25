> 2021년 7월 25일 - 효율적인 디자인을 돕는 Figma의 기능

## 효율적인 디자인을 돕는 Figma의 기능

### Constraint

- Object 제약을 둬서 여러 상황에 맞게 Object가 대응할 수 있도록 하는 것
  - 다양한 해상도의 디바이스에 맞춰서 요소가 대응하도록 할 수 있음
  - 반응형 디자인을 할 때 매우 유용하다!
- Frame에서 Object가 위치하는 축을 상하좌우로 지정 가능
  - Left / Right
  - Top / Bottom
  - Center
  - 섞어서도 사용 가능
- Frame에서 Object가 차지하는 크기를 비율 또는 크기로 지정 가능
  - Scale (Horizontal / Vertical)
  - Left & Right
  - Top & Bottom
- Fix Position 🍯
  - 프로토타입으로 보여줄 때 위치를 고정
  - 스크롤 하더라도 같은 위치에 있음

### Auto Layout

- 여러 개의 아이템을 그룹화 해서 그 사이의 간격을 자동으로 조절할 수 있음
  - 버튼을 만들 때 Auto Layout 이용하면 글자에 따라 버튼 크기 알아서 맞춰줌
- 아이템 간의 간격을 일정하게 유지해주고 간격은 오른쪽에서 설정 가능
- Auto Layout이 적용된 아이템끼리 또 Auto Layout을 적용할 수도 있음

### Style

- 저장한 Style의 속성을 바꾸면 Style이 적용 되어있는 아이템에 변경사항이 모두 반영됨
  - 수정사항 있을 때 반영하기 편리~
- 여러 화면에서 일관된 값으로 Style을 보여줄 수 있어서 좋음

- Text
  - H1, H2, H3, Body 등
- Color
  - Grey, White, Purple, Yellow 등
- Effect
  - Dropshadow-1, Dropshadow-2 등
- Grid
  - Mobile, iPhone11, Desktop 등

### Component

- UI/UX에서 Component에 대한 개념
  - 반복적으로 사용되는 Typography + Color + 도형으로 구성된 UI 요소
  - 대표적인 Component 사례를 공부하기 좋은 곳
    - Google Material Design
    - Human Interface Guideline
- 반복작업을 줄이고 디자인을 효율적으로 하게 해주는 기능
- Button, Text Field, Icon, Card Design 등을 각 상태별로 미리 만들어서 저장해두고 사용
- Create Component
  - Component로 등록할 Object를 선택하고 오른쪽 마우스 클릭해서 선택
  - 단축키는 Command + Option + K (Ctrl + Alt + K)
  - Component로 등록하려면 Object가 하나의 Layer에 있어야 함

- 사용할 때는 Assets에서 등록된 Component를 드래그로 꺼내서 사용
- 등록된 본체는 Component, 복사한 것은 Instance
  - 본체의 변경사항은 다른 Instance에도 적용됨
- Go to Main Component
  - Instance 선택 후 클릭하면 본체로 이동  
- Detech Instance
  - Instance를 별도의 객체로 분리 시켜줌
  - 커스터마이징 필요할 때 사용
- Component를 정리할 때는 / 를 사용해서 폴더화 할 수 있음

- Swap Instance
  - Component를 지정한 폴더에 있는 다른 Component로 변경 가능

### Library

- 새로운 Figma 파일에서 저장된 Style과 Component를 재사용 할 수 있게 하는 기능
- Team Library
  - 팀원과 공유하고 있는 프로젝트 폴더에서 Library를 팀원들도 접근 및 사용할 수 있게 함
  - 무료 버전에서는 Style만 공유할 수 있음 (Component는 유료...)
