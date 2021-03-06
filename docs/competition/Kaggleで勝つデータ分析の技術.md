# 分析コンペとは
* ポイント
    - タスクと評価指標
        * 探索的データ分析(Exploratory Data Analysis, EDA)
            - データの性質を把握する．
    - 特徴量の作成
    - モデルの作成
        * GBDTが主流
    - モデルの評価
    - モデルのチューニング
    - アンサンブル
* shake up: public leaderboardとprivate leaderboardで順位がガラっと入れ替わること．
    - リークも含めて，public leaderboardに過学習している人たちが死んでいく．



# タスクと評価指標

## タスクとその評価指標
* 回帰
    - RMSE, MAE
* 分類
    - ラベル予測: F1, mean-F1, macro-F1
    - 確率予測: logloss, AUC

## 評価指標
* RMSE
    - 外れ値の影響を受けやすい(外れ値に適合したモデルができてしまう)ので，外れ値を除く必要がある．
* MAE
* accuracy
    - あまり使われない．不均衡なデータの場合に，モデルの性能を評価しずらいから．
* precision/recall/Fbeta
* logloss
* AUC
logloss/AUCのように確率値の予測ではなく，Fbetaのようにラベルの予測値の場合，閾値の設定が重要になる．

## 評価指標と目的関数
* 回帰ではRMSEが使われることが多い．
* 分類ではloglossが使われることが多い．
* 目的関数と評価指標が違う場合，評価指標に最適になるような処理を加える必要がある．

## 評価指標の最適化
* 手法
    - 単に，評価指標をロスにして，学習する．
        * ex.) RMSE, logloss
    - 異なる評価指標によって学習し，後段に追加の最適化処理を設ける．
        * ex.) F値が評価指標の場合，まずloglossで学習を行い，後段で閾値の最適化を行う．
    - 異なる評価指標によって学習し，early stoppingで真の評価指標を最適化する．
        * ex.) loglossで学習し，F1でearly stoppingする．
* 閾値の最適化
    - accuracy: モデルに予測確率が正しいという仮定の元では，argmaxが最適である．
    - F1: 正例の割合や正しく予測できている割合によって，最適閾値が異なる．
        * grid search / scipy.optimize
        * マルチクラスの場合は，線形回帰によるスタッキングが，自然な拡張になっている．
    - 万全を期すなら，out-of-foldで行うべきである．
        * validで閾値を最適化するのはダメ．validは，その結果を(例えばearly stoppingを通して)「少し知っている」状態から始まるので．
* 予測確率の調整
    - ある程度データ量があり，loglossで学習している場合，対応は不要．
    - 手法: スタッキングアンサンブル
* 実例
    - balanced accuracy
    - レーティングを当てるタスクでの閾値の最適化

## リーク
- バリデーションの方法を間違えたため，テスト時には使えない情報を使って，予測していること．バリデーションでは性能が出るが，テストでは出ない，という問題を引き起こす．
- 例
    * テストデータが学習データに入っている．
    * テストデータの特徴量に予測対象の値が入っている．
    * 将来の情報が過去のデータに入っている．
    * 利用できないように削除(あるいは，匿名化，ランダム化)した変数の代理となる変数が残っている．
    * モデルを実際に学習・予測する時に利用できない情報が含まれている．
    * 第三者のデータに上記の情報が含まれている．



# 特徴量の作成
* 未読．ニューラルを使うタスクをやっているため．



# モデルの作成

## モデルとは何か
* 分析コンペの流れ
    - 特徴量の変更
        * 最も重要
    - ハイパラチューニング
    - モデルの変更
* クロスバリデーション
    - テストデータでどう予測するか？
        * 各foldで学習したモデルの出力を平均する．
        * 学習データ全体で学習し直す．
            - ニューロだと，early stoppingをするためにバリデーションデータが必要となる．よって，こちらの手法は難しい．
* オーバーフィッティング
    - バリデーションデータのスコアと，テストデータのスコアが違う場合は要注意．
        * バリデーションデータとテストデータの分布が違う
            - これは，全参加者が同じ条件なので，そこまで気を使う必要は無い．
        * バリデーションの枠組みが間違っている．

## 分析コンペで使われるモデル
以下，未読．




# モデルの評価

## hold-out
- Pros
    * 実装が楽．
    * 計算コストが低い．
- Cons
    * データを有効に使えない．
        - 結果の信頼性のためにはhold-outを増やすしか無いが，そうすると学習データが減る．
## CV
* Pros/Consはhold-outの逆．
* 学習データ量が多い場合は，CVが不要になる．
    - hold-out方で一部データを使ってvalidationを行うだけで，十分信頼がおけるため．
* fold数を増やすと
    - 学習データ量が増える．
    - 計算時間も増える．
    - 4/5 foldがよく用いられる．
* モデルの評価
    - foldごとのモデルの評価指標の平均でおこなう．
    - ただし，RMSEのように加法性が成り立たない場合は別途，考えること．
* 分類タスクの場合，層化抽出(各foldのクラス分布を全体のそれに合わせる)を行うこと．
* テストデータでどう予測するか？
    - 各foldで学習したモデルの出力を平均する．
    - 学習データ全体で学習し直す．
        - ニューロだと，early stoppingをするためにバリデーションデータが必要となる．よって，こちらの手法は難しい．

## 時系列データのバリデーション
* 読んだがまとめはスキップ

## バリデーションのポイントとテクニック
* バリデーションの目的
    - モデルを改善するための指標
    - テストデータに対するスコアのばらつきを見積もるための指標
* 学習データとテストデータの分割をまねる．
    - **特に，抽出がランダムに行われてない場合に注意せよ．**

## 学習データとテストデータの分布が違う場合
* EDAで違いを掴む．
* **adversarial validationを行う．**
* モデルを複雑にしすぎない．
* ensembleを行う．

## Leaderboardの情報を利用する．
* "Trust your CV" という格言があるが．うまくやればLeaderboardの情報も利用できる．
* バリデーションデータでの性能と，Leaderboard上での性能の差異をみる．
    - 同じ -> テストデータとバリデーションデータが近い．心配がいらない．
    - 違う
        * 送られてきたデータとテストデータの分布が異なる．
        * バリデーションデータの設計が不適切．
            - リーク
* shake up
    - public leaderboard とprivate leaderboardで順位が大きく変わること．
        * 過学習による．

## 過剰な適合
* パラメータチューニング




# モデルのチューニング
スキップ



# アンサンブル
## シンプルなアンサンブル手法
* モデル
    - ハイパラの変更
    - 乱数シードの変更
        * これだけで十分，多様性が出る．
        * ニューロは，学習ごとに精度が変わりやすいので，有効．
* スコアの混合方法
    - 回帰
        * 平均
        * 加重平均
    - 分類
        * 多数決，重み付け多数決
            - 分類タスクの場合
* アンサンブルをするなら，過学習気味のモデルを持ってきても良い，という意見もある．

## スタッキング
* スタッキングは学習データの情報を使い尽くそうとする性質がある．よって，学習データとテストデータの分布が同じで，学習データが大量にあるコンペでは，有効．
* 一方，時系列データなど，分布が違う場合は，加重平均の方がよいかもしれない．
* ニューロ + GDBTでとても効果が高かった，Kaggleコンペが存在する．
    - log lossが性能指標だったので，スコアの細かい調節が効いた．cf. accuracy

## どんなモデルをアンサンブルすれば良いか
* 多様性に富んだモデル
* 性能が低くても，多様性に寄与するなら，性能が向上することもある．
* モデルの多様性
    - GBDT
    - ニューロ
    - 線形
    - k近傍
    - ..
* ハイパラ
* 特徴量
* 問題の捉え方を変える
    - ２人以上で独立に問題を解いておき..
