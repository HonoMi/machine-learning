# コンペティンション対策
* [コンペ](./docs/competition/README.md)


# 学習曲線
* 学習曲線が周期的にギザギザする．
    - 原因
        * train setではそもそも，epochごとに周期的に同じサンプルが現れる．ここで一気にlossが低く出ている可能性がある．
        * データの並びに特徴がある． -> shuffleするべき．
        * lrateが大きすぎる -> 小さくする．
    - 参考資料
        * [Interpretation for a periodic loss function? - Google グループ](https://groups.google.com/a/tensorflow.org/forum/#!topic/discuss/kSfDMTC6YLY)
        * [machine learning - Periodic/Oscillating Loss Function for Pytorch CCNN - Stack Overflow](https://stackoverflow.com/questions/56794716/periodic-oscillating-loss-function-for-pytorch-ccnn)
        * [machine learning - Periodic Behaviour of Loss function in CNN for Object Detection - Stack Overflow](https://stackoverflow.com/questions/49935907/periodic-behaviour-of-loss-function-in-cnn-for-object-detection)
        * [Loss Function | Loss Function In Machine Learning](https://www.analyticsvidhya.com/blog/2019/08/detailed-guide-7-loss-functions-machine-learning-python-code/)


# パラメータチューニング
* DL
    - まずlr
    - 次に，Dropout
        * 振らないでいいかもしれない． (by 是枝)



# 性能指標
* [マクロ平均，マイクロ平均](https://www.haya-programming.com/entry/2018/03/14/112454#多クラス分類編)


# multi-label 分類
* [1つの画像が複数のクラスに属する場合（Multi-label）の画像分類 - Qiita](https://qiita.com/koshian2/items/ab5e0c68a257585d7c6f)
* [マルチラベル - 機械学習の「朱鷺の杜Wiki」](http://ibisforest.org/index.php?マルチラベル)
* [数えきれないほどの分類を行うExtreme Classification - Technical Hedgehog](https://kamujun.hatenablog.com/entry/2018/06/22/180605)



# Few-shot
* [Meta-Learning: Learning to Learn Fast](https://lilianweng.github.io/lil-log/2018/11/30/meta-learning.html)



# 弱学習(weak supervision)
* [Weak Supervision: A New Programming Paradigm for Machine Learning | SAIL Blog](http://ai.stanford.edu/blog/weak-supervision/)
* [weak Supervision: The New Programming Paradigm for Machine Learning](https://hazyresearch.github.io/snorkel/blog/ws_blog_post.html)
* [snorkel/README.md at master · HazyResearch/snorkel](https://github.com/HazyResearch/snorkel/blob/master/README.md)




# 半教師あり学習(Semi Supervised Learning, SSL)
* [半教師あり学習のモデル仮定 - でかいチーズをベーグルする](http://yamaguchiyuto.hatenablog.com/entry/machine-learning-advent-calendar-2014)
* [半教師あり学習とは結局のところ何なのか? - yasuhisa's blog](https://www.yasuhisay.info/entry/20100118/1263765793)
* [Label propagationとLabel spreading - でかいチーズをベーグルする](http://yamaguchiyuto.hatenablog.com/entry/graph-base-ssl)
* [半教師あり学習_Semi-Supervised Learning (Vol.20)](https://products.sint.co.jp/aisia/blog/vol1-20)
* [snorkel/README.md at master · HazyResearch/snorkel](https://github.com/HazyResearch/snorkel/blob/master/README.md)





# Active Learning(能動学習)
* [能動学習で効率的に教師データを作るツールをGoで書いた - yasuhisa's blog](https://www.yasuhisay.info/entry/2017/05/18/080000)
* [-ε-いつかのブログ-з- : Active Learning Literature Survey のまとめ　1～3章](http://blog.livedoor.jp/itukano/archives/51826566.html)
* [-ε-いつかのブログ-з- : Active Learning Literature Survey のまとめ 4～8章](http://blog.livedoor.jp/itukano/archives/51826569.html)
* [Active Learning 入門](https://www.slideshare.net/shuyo/introduction-to-active-learning-25787487)




# ヒューマンコンピューティング、ヒューマンアノテーション、クラウドソーシング
* [自然言語におけるアノテーションのつらさをまとめる – chakki – Medium](https://medium.com/chakki/自然言語におけるアノテーションのつらさをまとめる-dd441895b464)
* [クラウドソーシング - Qiita](https://qiita.com/ikeyasu/items/4634da545ad7d001bd86)




# LSTM
* [LSTMネットワークの概要 - Qiita](https://qiita.com/KojiOhki/items/89cd7b69a8a6239d67ca)




# Data Visualization
* [HonoMi/Udemy_Python-Data-Science-and-Machine-Learning-Bootcamp](https://github.com/HonoMi/Udemy_Python-Data-Science-and-Machine-Learning-Bootcamp)




# 機械学習一般
* [機械学習をざっくりと理解する - QiitaQiita](https://qiita.com/t-yotsu/items/1a6bf3a4f3242eae7857)
    - 回帰
        * 線形回帰
        * サポートベクター回帰
        * 回帰木
        * ニューラルネットワーク
    - 分類
        * ロジスティック回帰
        * k-nearest
        * SVM
        * 決定木
            - 決定木
            - random forest
        * ニューラルネットワーク
    - クラスタリング
* [scikit-learn cheet sheet](http://scikit-learn.org/stable/tutorial/machine_learning_map/)
* [サイトマップ](http://neuro-educator.com/sitemap/)
    - 下の方に、機械学習器毎の記事がある。




# 回帰問題
* 線形回帰
* サポートベクター回帰
    - [サポートベクター回帰(Support Vector Regression, SVR)～サンプル数10000以下ならこれを使うべし！～](http://datachemeng.com/supportvectorregression/)
* 回帰木
    - [初心者の初心者による初心者のための決定木分析 - QiitaQiita](https://qiita.com/3000manJPY/items/ef7495960f472ec14377)
    - [【Python】回帰木を書いてみる【決定木】 | FiS Project【Python】回帰木を書いてみる【決定木】 – FiS Project](https://fisproject.jp/2016/07/regression-tree-in-python/)
* SGD Regressor
    - [sklearn.linear_model.SGDRegressor — scikit-learn 0.19.1 documentation](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.SGDRegressor.html#sklearn.linear_model.SGDRegressor)




# アンサンブル学習
* [アンサンブル学習 - 機械学習の「朱鷺の杜Wiki」](http://ibisforest.org/index.php?アンサンブル学習)
    - [バギング - 機械学習の「朱鷺の杜Wiki」](http://ibisforest.org/index.php?バギング)
    - [ブースティング - 機械学習の「朱鷺の杜Wiki」](http://ibisforest.org/index.php?ブースティング)
* [LightGBM 徹底入門 – LightGBMの使い方や仕組み、XGBoostとの違いについて](https://www.codexa.net/lightgbm-beginner/)



# 木
* LGBM
    - [勾配ブースティングについてざっくりと説明する - About connecting the dots.](http://smrmkt.hatenablog.jp/entry/2015/04/28/210039)
    - [LightGBM ハンズオン - もう一つのGradient Boostingライブラリ - QiitaQiita](https://qiita.com/TomokIshii/items/3729c1b9c658cc48b5cb)
    - [原論文](https://papers.nips.cc/paper/6907-lightgbm-a-highly-efficient-gradient-boosting-decision-tree.pdf)
    - [anaconda3でgraph_toolを使う - Tamflexの貯蔵庫](http://tamflex.hatenablog.com/entry/2017/02/20/202210)
        * LGBMのインストール時の注意




# パラメータチューニング
* [Scikit learnより グリッドサーチによるパラメータ最適化 - QiitaQiita](https://qiita.com/SE96UoC5AfUt7uY/items/c81f7cea72a44a7bfd3a)
* [ハイパーパラメータの最適化と結果の見方【Pythonとscikit-learnで機械学習：第8回】](http://neuro-educator.com/ml8/)




# 参考資料
* [Kaggle本]($DOCS/books/Kaggleで勝つデータ分析の技術.md)
* [HonoMi/Kaggle_Mercari_Price_Suggestion_Challenge](https://github.com/HonoMi/Kaggle_Mercari_Price_Suggestion_Challenge)
* [ビジネス活用事例で学ぶデータサイエンス入門.md]($DOCS/books/ビジネス活用事例で学ぶデータサイエンス入門.md)
* [HonoMi/Udemy_Python-Data-Science-and-Machine-Learning-Bootcamp](https://github.com/HonoMi/Udemy_Python-Data-Science-and-Machine-Learning-Bootcamp)
* [戦略的データサイエンス入門 —ビジネスに活かすコンセプトとテクニック ](https://www.amazon.co.jpdp//4873116856/)
    - ためにならなかった覚えがある。
* [HonoMi/Udemy_Python-Data-Science-and-Machine-Learning-Bootcamp](https://github.com/HonoMi/Udemy_Python-Data-Science-and-Machine-Learning-Bootcamp)
