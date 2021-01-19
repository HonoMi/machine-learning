# 最適化

## 最適化の指標
* loss
    - Pros
        * 微分可能である場合が多く，SGD等での最適化(=モデルの学習)が容易．
    - Cons
        * official metric は別に用意されることが多い．その場合，lossの最適化は，だけでは不十分である．
    - ex.) cross entropy, MSE
* official metric
    - Pros
        * official metricの最適化が，コンペの勝利と直結している．
    - Cons
        * 微分不可能である場合が多いので，最適化ライブラリに頼ることになる．その場合，探索できるパラメータ数に限りがある．
    - ex.) F, macro-F, AUC

## 最適化対象のパラメータ
* 結論
    - どこかでmetricの最適化が入れば良いと思う．
    - パターン:
        1. モデルパラメータをlossで最適化する．
        2. ensemble重みをlossで最適化する．
        3. 閾値をmetricで最適化する．
    - パターン:
        1. モデルパラメータをlossで最適化する．
        2. ensemble重みをmetricで最適化する．
        3. 閾値をmetricで最適化する．
    - パターン:
        1. モデルパラメータをlossで最適化する．
        2. ensemble重みをmetricで最適化する．
    - パターン:
        1. モデルパラメータをlossで最適化する．
        2. Stackをlossで最適化する．
        3. metricで..
    - パターン:
        1. モデルパラメータをlossで最適化する．
        2. モデルパラメータを閾値で最適化し直す．
        3. ensemble重みをmetricで最適化する．
        おそらくこれは， **過学習気味になるだろう．**モデルごとに閾値が調節要素となるから．
* モデルパラメータ
    - 結論: lossにより最適化する．
    - lossによる最適化
        * 通常こちら．
    - official metricによる最適化
        * 微分不可能で使えない場合が多い．
        * early stoppingなどで使える場合もある．
* ensemble重み
    - 結論: 両方やってみるしかなさそう..．
    - lossによる最適化
        * Pros
            - 学習しやすい．
            - 「モデルパラメータのlossと同じloss」を使えるはずなので，常に実行可能．
        * Cons
            - lossなので，コンペの勝利と直結していない．
    - metric最適化: 実行可能．
        * Pros
            - コンペの勝利と直結している．
            - 実績がある．
                - [Optimizing Ensemble Weights using Simple | Kaggle](https://www.kaggle.com/daisukelab/optimizing-ensemble-weights-using-simple#Optimizing-ensemble-weights)
                - Kaggle本 7.2.1 「スコアが最も高くなるように最適化する」
                    * scipy.optimize
                - Kaggle本 7.5.2 「Home Depot Product Search」
        * Cons
            - 多数のパラメータを使えない可能性が高い．
                * simplexの体積は，次元数をdとして，C^d/2
            - Stackingの場合，おそらく，loss最適化のほうが使われる．
        * 実例
* "閾値"
    - 結論: metric最適化を行う．
    - lossによる最適化: 微分不可能になるので，実行不可能．
    - metric最適化: できる．

## 最適化ライブラリ
* sklearn RandomizedSearchCV
* scipy.optimize (Kaggle本 2.5.2) 参照のこと
* [Simple](https://www.kaggle.com/daisukelab/optimizing-ensemble-weights-using-simple#Optimizing-ensemble-weights)

## 参考資料
* [機械学習モデルのハイパパラメータ最適化](https://www.slideshare.net/greetech/ss-110811527)
* [scikit-learnにスタッキングのクラスが追加されたので使ってみる](https://analytics-note.xyz/machine-learning/scikit-learn-stacking-classifier/)









