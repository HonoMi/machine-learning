# インバランスデータ
「正例が多数，負例が少数」の場合で説明する．

## 何が課題か
正例を正例と予測できなくなることが問題となる．
この理由は
* 負例の頻度が高いのでどんなときでも負例と予測することを学習してしまう．
* 上の結果として，正例の特徴量(とおそらく，負例の特徴量も)を学習しない．

結局の所，「どんな時でも負例と予測すればよい」ならば，何も学習する必要が無いのである．

## 結論
* まず，「ロスに重みをつける」手法を試す．
* 次に，時間が会ったら，「オーバーサンプリング」の洗練された手法を貯める．

## 手法
* アンダーサンプリング
    - 概要: 負例を捨てる．
    - Pros: 計算量が小さくなる．
* 特に工夫をしない
    - Pros: コストが無い．
    - Cons: モデルに予測能力が無い場合，単に性能を悪くする可能性がある．
        * モデルに予測能力がない場合(xからyを当てられない場合)，yの周辺分布をそのまま出すのが最も性能が高いかもしれない．その場合，yの周辺分布を変えてしまうと，困る．
* ロスに重みをつける
    - Pros: 実装コストが小さい．
        * `nn.CrossEntropyLoss(weight=weight)`
* オーバーサンプリング
    - 概要
        * 正例を増やす．
        * バッチごとにランダムに増やすのが良い．
        * 単なるコピーではなく，ノイズを加えたり，正例達の特徴ベクトルから特徴ベクトルを生み出す手法もある．
    - Pros: ロスに重みをつけるよりも，洗練された手法がある．
    - Cons: 実装コストが少し高い．
    - 備考
        * [OSS](https://imbalanced-learn.readthedocs.io/en/stable/)
        * 堀口手法
            - 各クラス同じサンプル数にして学習．
            - 推論時には，argmax (閾値の調節はしない．)
        * 実装は[ここ](https://github.com/HonoMi/pytorch-imbalanced-dataset-sampler)
上記の手法は， **閾値を調節する手法と組み合わせること．**




