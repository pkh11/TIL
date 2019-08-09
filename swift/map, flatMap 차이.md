# map과 flatMap 차이
1. map </br>
클로저 함수로 특정 항목들을 포함한 결과물을 알려준다.

```Swift
let fruits: [String?] = ["Apple", "Banana", nil, "Orange", "Grape", nil ,"Melon","Pineapple", nil]

let valid_map = fruits.map { $0 }
// [Optional(\"Apple\"), Optional(\"Banana\"), nil, Optional(\"Orange\"), Optional(\"Grape\"), nil, Optional(\"Melon\"), Optional(\"Strawberry\"), Optional(\"Pineapple\"), nil]
```
2. flatMap -> compactMap으로 변경 (Swift 4.1) </br>
클로저 함수로 nil값을 제거한 후 특정 항목을 포함한 결과물을 알려준다.

```Swift
let fruits: [String?] = ["Apple", "Banana", nil, "Orange", "Grape", nil ,"Melon","Pineapple", nil]

let valid_flatMap = fruits.flatMap{ $0 }
// [\"Apple\", \"Banana\", \"Orange\", \"Grape\", \"Melon\", \"Pineapple\"]
let valid_compactMap = fruits.compactMap { $0 }
// [\"Apple\", \"Banana\", \"Orange\", \"Grape\", \"Melon\", \"Pineapple\"]
```
