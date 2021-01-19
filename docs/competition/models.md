# モデル

## ベースラインモデル
* 言語処理の場合，bert-base-uncasedがよい．ある程度性能が良く，手元のマシンでも学習できるから．

## 強い言語モデル
* bert-base-uncased
* bert-large-uncased
* gpt2-large
* roberta-large
* xlm-mlm-en-2048
* xlnet-large-cased
* transfo-xl-wt103
* **T5**



# SVM
* [sklearn.svm.SVC](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html)
    - 落とし穴
        * decision_functionは，3クラス以上の場合はクラス数と同一の値が返され，スコアと解釈できる．
        * 2クラスの場合は，1つの値が返され，負のスコアと解釈する．
            - クラス0のスコア: - decision_function
            - クラス1のスコア: + decision_function
