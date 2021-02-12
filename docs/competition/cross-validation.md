# Cross Validation

## Kaggle本まとめ
* cross validationは，以下の２つの良いとこ取りを目指す．
    - できるだけ多くのデータを学習用に回すことで，モデルの性能を向上させたい．
    - できるだけ多くのデータをvalidation用に回すことで，モデルの性能評価を正確に行いたい．
* モデルの性能評価
    - 各foldのスコアから計算する．平均等．
        * RMSEは単なる平均ではないことに注意
    - 各foldの予測値から計算する．
* モデルによる予測
    - 各foldで学習したモデルの出力を平均する．
    - 学習データ全体で学習し直す．
* 実装
    - `sklearn.model_selection.cross_val_predict`

## 方針
* fold数の選定
    - 「devも減らしすぎない程度にtrainをできるだけ多くする」になるようなfold数にする．
        * ex) データ数10000なら，dev=1500程度になるように，fold数=6 にする．
* ハイパラ探索との統合: **3を採用．**
    1. ハイパラ固定 -> n-fold全てで評価 -> feedback ..
        * Pros: 完全
        * Cons: 実行時間がfold数倍になってしまう．
    2. ハイパラ固定 -> n-foldからm個をランダムサンプルし，評価 -> feedback ..
        * Pros:
            - 実行時間はm倍にしかならない．
            - 時間方向に伸ばせば，乱数によって，cvの方よりもなくなる．
        * Cons: 
            - **Stackingと相性が悪い．なぜなら，モデルによって，validationデータが変わってしまうから．**
        * 備考
            - m=1でも収束はするが，速度は遅くなるだろう．
    3. ハイパラ固定 -> n-foldからm個(固定)を取得し，評価 -> feedback ..
        * Pros:
            - 実行時間はm倍にしかならない．
            - Stackingとの相性が良い．
        * Cons: 
            - mが小さいと，validationが偏る．



# CVはいつ必要か？
* validationが必要な場合
    - 一般論
        * モデル選択をする場合
        * stackingをする場合
    - 今回の場合
        * すべてのメソッドで必要となる．ベースモデル数の選択をするから．
        * もちろん，stackingでは特に重要．
* Cross validationが必要な場合
    - 一般論
        * validationが必要な場合 & fold-outだとvalidation dataが少ない場合
    - 今回の場合
        * validation foldのデータ数が10k以下になる場合(この基準は適当に決めた)

上記までだと，stacking/votingの両方の場合で，どのタスクでも必要なCVは同じとなる．
しかし，votingで必要なのはモデル数の選択だけであるため，stackingよりは必要はvalidation dataの数が少ないと考えられる．
つまり，フェアでない．
よって，votingの場合はCVの数を減らして実験をするか，「一般にはハイパラ等も選ぶため，votingでもCVは必要」と強弁してしまうかのどちらかが必要となる．
