<!---
状態遷移図と状態遷移表を描く
--->
# 状態遷移分析
| システムID | システム名称 |
| ------ | ------ |
| phone | 電話システム ｜


## 状態遷移図

```plantuml
@startuml
state 電源オフ
state 電源オン {
  state 待機中
  state 着信中
  state 通話中
  state 発信中

  [*] --> 待機中
  待機中 --> 着信中 : 着信
  着信中 --> 待機中 : 切断
  着信中 --> 通話中 : 応答
  待機中 --> 発信中 : 発信
  発信中 --> 待機中 : 切断
  発信中 --> 通話中 : 接続
  通話中 --> 待機中 : 切断
}

[*] --> 電源オフ
電源オフ --> 電源オン : 電源オン
電源オン --> 電源オフ : 電源オフ
@enduml
```

## 状態遷移表
| 状態\イベント | 着信  | 応答  | 発信  | 接続  | 切断  |
| ------- | --- | --- | --- | --- | --- |
| 待機中     | 着信中 | -   | 発信中 | -   | -   |
| 着信中     | -   | 通話中 | -   | -   | 待機中 |
| 発信中     | -   | -   | -   | 通話中 | 待機中 |
| 通話中     | -   | -   | -   | -   | 待機中 |
