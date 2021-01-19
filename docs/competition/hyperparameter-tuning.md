# ハイパラチューニング

## 前提
* 「ensembleを行う前提であれば，個々のモデルは過学習気味の方が良いという意見がある」(Kaggle本)

## 手法
* 手順
    1. まず，ベースラインパラメータ で実験を行う．
        * 簡単な調節として，グリッドサーチを行ってもよい．
    2. 次に，ベイズ最適化を施す．
        * パラメータ数が少ない場合は，gridで良いかも．
        * Optunerを使う．
            - 乱数シードは固定すること．再現性のため．
    3. 探索範囲の端に最良の結果がある場合は，探索範囲を広げる．
* チューニングパラメータ(重要度順)
    - **まずTensorboardで学習曲線を見ることにより，上手くいっているかをつかめ．**
    - optimizer
        * 探索範囲: ["adam", "bert_adam"]
        * ベースライン: adam
        * 分布: 一様分布
        * 備考
            - bert_adamは，warm up付きのscheduler
                * **max_epochs=3** と組み合わせること．
    - lrate
        * 探索範囲: [0.00001, 0.01, log-uniform]
        * ベースライン: jiantに従う．
        * 分布: 対数一様分布
        * 備考
            - "early stopping"や"lrate scheduler"を参考にすること．
    - drop-out率
        * 探索範囲: [0, 0.3, 0.05]
        * ベースライン: 0.2
        * 分布: 一様分布
    - 中間層の数
        * 探索範囲: [1, 3, uniform]
        * ベースライン: 1
        * 分布: 一様分布
    - 中間層のユニット数
        * 探索範囲: [256, 2048, uniform]
        * ベースライン: 1024
        * (森尾) bi-directionalで1024は大きいかもしれない．
        * 分布: 一様分布
    - optimizer:
        * 基本はAdam．
        * 言語モデルの場合，適したやつに固定 (ex. BERT Adam)． jiantに従う．
    - batch size: 16固定 (32だと，xlnetとかでメモリエラー)
    - epoch数: 大きい値に固定．early stoppingで決める．
    - early stopping: official metricによって，early stoppingを行う．
    - 活性化関数: ReLUで固定
* (森尾)チューニング
    - devは決め打ち
    - Optunerで20回探索．1回の探索で3並列ぐらい．
        * lrate, drop-out, lstmの層, attentionで引っ張るBERTのlayer
        * **devで10ポイントくらい上がる．**
            - テストデータだともっと小さいと予測される．なぜならば，Optunerは，最初はランダムモデルから始まるので，上がり幅が大きい．

## ノウハウ
* regressionタスクでは，classificationに比べて，最適なlrateが低い．
    - task8では２桁下であった．
    - また，regressionでlrateを上げすぎると，lossが発散する．
* lrateが大き過ぎると...
    - 現象: train/valid 両方とも，lossは下がらず一定値 + 揺らぎ という挙動をする．
    - 解釈: lrateが大き過ぎるので，あっちこっちさまよっている．
    - 備考: よくある現象らしい(by 堀口)
* lrateが小さすぎると...
    - 現象: train lossは下がる．valid lossは上がる．
    - 解釈: 局所最適解に陥りやすいため(過学習しやすいため．)．
    - 備考: よくある現象らしい(by 堀口)
* データセット小さすぎると...
    - **どのようなlrateを選んでも，** 過学習してしまう(train lossは下がり，valid lossは上がる)． 汎化特徴量を学習するほどのデータ量が無いため．
    - この場合，「過学習させて，予測できるサンプルだけで性能指標での評価値を稼ぐ」ことが解となる．
        * valid lossは下がるが，性能が下がるとは限らない．予測できるサンプルだけを当てに行き，それ以外はrandomに予測すれば，性能を上げることもできうる．

## Optuna
* todo
    - 並列実行
    - 先読みstop
* [Optuna](https://preferred.jp/ja/projects/optuna/)
* [ハイパーパラメータ自動最適化ツール「Optuna」公開](https://tech.preferred.jp/ja/blog/optuna-release/)
* [Tutorial](https://optuna.readthedocs.io/en/stable/tutorial/index.html)
* [GridSearchCVはもう古い！Optunaでサポートベクターマシンもラクラクチューニング - Qiita](https://qiita.com/koshian2/items/1c0f781d244a6046b83e)
* [optuna入門 - Qiita](https://qiita.com/studio_haneya/items/2dc3ba9d7cafa36ddffa)
* [src/cmds/opt](https://gitlab.rdcloud.intra.hitachi.co.jp/70727303/semeval11/tree/master/src/cmds/opt)
* [Optunaで特定の初期値から最適化を開始する - Qiita](https://qiita.com/tmitani/items/c0acd198788089786e29)




# Scikit-Learn
* [scikit-learnでsvm 基本的な使い方 - 備忘録とか日常とか](http://may46onez.hatenablog.com/entry/2016/02/19/152532)
    - GridSearchCVで行う．



# Early stopping
* ロスで止めるべきか，指標で止めるべきか．
    - 結論
        * 指標で止める．
    - 理由
        * semeval2020 task8 image classifierの実験から．
    - 実験
        * nll vs F
    - 結果&考察
        * Fの方が圧倒的に良い．
            - Fが最適になるポイントとnllが最適に成るポイントが，ずれている．
                * Fはずっと上がっていく．nllは途中から上昇に転じる．
* 「ロスを見ると過学習を始めている(ロスが大きくなり始めている)が，F値はまだ上昇し続けている．」
    - よく起こる．(堀口)
* egniteのearly stoppingは，通常の実装とは異なるので注意．
    - 「esの回数だけロスが上がる事象が起きたら，学習をやめる」という実装になっている．ロスが下降曲線に戻っても，失ったバジェットは戻ってこない．




# lrate scheculer/optimizer
* [optimizerごとの，lrate初期値の値](https://medium.com/octavian-ai/which-optimizer-and-learning-rate-should-i-use-for-deep-learning-5acb418f9b2)
* [Optimizer入門＆最新動向](https://www.slideshare.net/MotokawaTetsuya/optimizer-93979393)
* **画像の場合(言語の場合も？)，「momentum + SGD + 手動で下げていく」が強い．詳しくは，"$PROJECTS/image-recognition/README.md"を見よ．**
