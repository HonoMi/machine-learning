# 乱数の固定
* うまくいったパターン
    ```python
    seed = 0
    random.seed(seed)
    np.random.seed(seed)
    torch.manual_seed(seed)
    torch.cuda.manual_seed(seed)
    torch.backends.cudnn.deterministic = True
    torch.backends.cudnn.benchmark = False
    ignite_manual_seed(seed)
    ```
* tensorflow を使う場合は，追加のコードが必要(参考資料参照のこと．)
* 参考資料
    - [機械学習におけるランダムシードの研究 - Qiita](https://qiita.com/si1242/items/d2f9195c08826d87d6ad)
    - [乱数を固定する – スーパー初心者からはじめるDeep Learning](https://wonderfuru.com/乱数を固定する/)
