


# まとめ

## 3. Bagging
* bagging は`unstable learner`に特に有効．

## 4. Combination Methods
* ensembleでなぜ性能が上がるのか，いｋつかの具体例で示している．
    - 例: 回帰問題において，ensembleの仮説空間には，base modelの仮説空間よりも良い仮説が含まれている(=誤差が小さい仮説が含まれている)ことが示されている．
        - この議論は，PAC理論でいうところのbias項のみに注目している．
        - 更に，分類問題には適用できないらしい．
* base modelに相関が無いことが，ensembleが成功する秘訣である．いくつかの具体的において，この主張を確かめている．
    - おそらくこの主張はmisleading．正確な主張は，`base modelが無相関でかつ，それぞれの性能がある程度(少なくともrandom guessよりは)良い`
    - 本主張は，直感的には簡単に理解できる．
        - base modelが同じサンプルで誤るなら(=正の相関がある)，ensembleで性能は上がらない．
        - base modelが同じサンプルで正解/誤りを引くなら(=負の相関がある)，ensembleで性能は上がらない．
        - base modelの正解/誤りに相関がなく，かつそれぞれが誤りよりも正解を引く確率が高いなら，ensembleで性能は上がる．
* なぜensembleで性能が向上するのか，../theory.md にもまとめた．

## 5. Diversity
* ensembleで性能向上をさせるには，base modelがdiverse(independent)でありかつ，accurateである必要がある．
* 前者は大きな課題となる．なぜならば，多くの問題において，base modelは学習データを共有するので，相関が発生しやるいからである．
* diversityは重要だけど，理論的には何も分かっていない．

## 6. Ensemble Pruning
* ensemble pruning (base modelの剪定) を行う理由．
    - 計算論的なもの(空間計算量・時間計算量)
    - pruningした方が，汎化誤差が小さくなることがある．
* いくつかの具体例で，「pruningした方が汎化誤差が小さくなることがある」を確かめている．
* pruningのよくある手法を紹介している．


## 8. Advanced Topics
* Semi-Supervised Ensemble
    - 一般のsemi-supervised learningに見える．



# 参考資料
* [Ensemble Methods: Foundations and Algorithms](https://www.amazon.co.jp/dp/B00A8SNJ7K/)
