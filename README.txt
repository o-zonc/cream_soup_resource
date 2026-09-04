Minecraft Java Edition 26.2 — 국물만 틴트되는 아이템 예제

구조
----
assets/cream_soup/items/soup.json
  - minecraft:item_model="cream_soup:soup"가 읽는 클라이언트 아이템 정의
  - tintindex 0을 custom_model_data.colors[0]에서 읽음
  - tintindex 1은 흰색 상수라서 그릇의 원본 색을 유지

assets/cream_soup/models/item/soup.json
  - layer0: soup_liquid.png (국물)
  - layer1: soup_bowl.png   (그릇)

assets/cream_soup/textures/item/soup_liquid.png
  - 국물 부분만 존재하는 흰색/회색 마스크
  - 실제 색은 custom_model_data.colors[0]으로 결정됨

assets/cream_soup/textures/item/soup_bowl.png
  - 그릇 부분만 존재
  - 틴트는 흰색 고정이므로 PNG 원본 색을 그대로 표시


사용 예시
---------
1) 크림색 국물 (#FFFDD0)

give @s minecraft:paper[minecraft:item_model="cream_soup:soup",minecraft:custom_model_data={colors:[16776656]},minecraft:custom_name={text:"크림스프",color:"#FFFDD0",italic:false}]

2) 카레색 국물 (#F2C14E)

give @s minecraft:paper[minecraft:item_model="cream_soup:soup",minecraft:custom_model_data={colors:[15909198]},minecraft:custom_name={text:"크림카레",color:"#F2C14E",italic:false}]

3) 초록 국물

give @s minecraft:paper[minecraft:item_model="cream_soup:soup",minecraft:custom_model_data={colors:[65416]},minecraft:custom_name={text:"수상한 크림슾",color:"#00FF88",italic:false}]


중요
----
- soup_liquid.png를 컬러 그림으로 만들면 원본 색 × tint 색으로 곱연산되어 원하는 색과 달라질 수 있습니다.
  국물 텍스처는 흰색/회색 음영 위주로 제작하는 것이 좋습니다.
- layer0의 생성된 면은 tintindex 0, layer1은 tintindex 1을 사용합니다.
- 이 예제는 Minecraft Java 26.2 Resource Pack 88.0을 대상으로 합니다.

업데이트된 그릇 형태
------------------
- 양쪽에 고리형 손잡이가 있는 수프볼
- 넓고 둥근 몸체
- 아래에 받침 접시 포함
- soup_liquid.png는 그릇 안쪽 국물 면만 포함
- soup_bowl.png는 그릇/손잡이/받침만 포함하므로 국물 색상만 custom_model_data tint로 변경됨
