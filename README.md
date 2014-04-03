ifph
====

「関数プログラミング入門 Haskellで学ぶ原理と技法」("Introduction to Functional Programming using Haskell")への私的メモ。

## 第１０章　モナド

機能。

| 機能 | 説明 | 登場人物 |
|--------|--------|--------|
| 基本 | 基本となる評価器(10.2.1) | Term, eval |
| 例外 | エラー処理(10.2.2) | Exc(Raise Exception, Return a), Exception |
| 状態 | 計算回数のカウント(10.2.3) | St, MkSt(State -> (a, State)), State |
| 出力 | 実行ステップのトレース(10.2.4) | Out, MkOut (Output, a), Output |


