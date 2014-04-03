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

## モナドによる評価器 + モナドの複合

| 型クラス | 定義 | 演算 | 対応する標準ライブラリ |
|--------|-----|----|----|
| モナド | Monad m | return, >>=  |
| 恒等モナド | Id a |      | Control.Monad.Identity |
| 例外モナド | ExMonad m | raise | Control.Monad.Error ? |
| 状態モナド | StMonad m | tick  | Control.Monad.State | 
| 出力モナド | ShowMonad m | showMonad | Control.Monad.Writer ? |
| モナド変換子 | Transformer t | promote | |
| 例外モナドのモナド変換子 | EXC | promote, recover | ErrorT ? |
| 状態モナドのモナド変換子 | STT | promote, apply | StateT |

### 10.4 モナドの複合 

例外処理と状態の両方を使えるようなモナドを、既にある例外モナドと状態モナドを組み合わせることで作る。
ここで、特定のモナド m0 と任意のモナド m を組み合わせるモナド変換子 t を考える。モナド変換子 t は以下のような
性質を持っていて欲しい。
- 任意のモナド m を受けとり、新しいモナド m' を作ることができる。つまり m' は Monad のインスタンス。
- 新しいモナド m' は、モナド m0 の性質を持つ。つまり m' は m0 のインスタンス。
- 新しいモナド m' は、モナド m の性質を持つ。つまり m' は m のインスタンス。

このようなモナド変換子 t がそれぞれの特定のモナドに対して作れれば、任意のモナドを組み合わせることができるようになる。

- 準備: 型クラス ExMonad, StMonad, ShowMonad を定義する。

- 準備: 任意のモナドと例外モナドを複合するモナド変換子 EXC を定義する。(10.4.1)
-- m がモナドのとき、EXC m がモナドであることを要請する。そしてこれは実際に定義できる。(10.4.1 p.341)
-- m がモナドのとき、EXC m が例外モナドであることを要請する。そしてこれは実際に定義できる。(10.4.1 p.342)
-- EXC m が任意のモナド m に対して例外モナドであることを要請する。そしてこれは実際に定義できる。(10.4.1 p.342)




