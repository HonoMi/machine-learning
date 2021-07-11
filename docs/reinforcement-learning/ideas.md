# todo
* sonicなどで「人形を動かす」ことを学習してから、montezmaをやる
* MiniWoB
* black box optimizationの章
* text world
    - 主張: transformerのおかげで、自然言語に起因する部分は解決 => 強化学習的なアルゴリズムに集中できる
* ideaをもう少し詰める。


# 戦略
最初から強化学習ガチの研究に入り込むことはできない。
なので、まずは言語処理との中間領域から入っていく。
例えば、言語処理に、強化学習の最新手法を導入する。




# ideas

## ゲーム
natural language guidedなゲーム攻略の研究が多い。
* コンペなどを探す。
    * [MineRL: Towards AI in Minecraft](https://minerl.io/)
* 既存のゲームを無理矢理 natural language guidedにする。

## 言語処理
* [対話]($PROJECTS/NLP/chatbot/ideas.md)
    - todo: もっと調べる。
    - テーマは好きだが、現状、そこまで良いideaが無い。
    - おそらく、wizard of wikipediaなどは、実際にやってみないと見つからない課題があるだろう。
* query reformation
    * [Ask the Right Questions: Active Question Reformulation with Reinforcement Learning](https://arxiv.org/abs/1705.07830)

## 強化学習一般
* [Google AI Blog: Recursive Classification: Replacing Rewards with Examples in RL](https://ai.googleblog.com/2021/03/recursive-classification-replacing.html)
* R2D2の価値関数をRNNからTransformerにする。
* モデルベース強化学習において、世界モデルをTransformerにして性能を向上させる。



# rejected
* 人狼知能
    * [却下]
        * 人口があまりにも少ない。
        * データが無いので、強化学習できない。
            * まぁ、機械同士を戦わせて性能を上げることはできるかもしれない。
            * 先行研究では、bot同士の対戦で学習している。効果は小さい。
