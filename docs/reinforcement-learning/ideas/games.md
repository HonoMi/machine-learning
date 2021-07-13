# todo
* まとめる。 => (森尾) 相談



# 全般
* 既存のゲームを無理矢理 natural language guidedにする。
* multi modal系ゲームでは、ゲーム画面 + textでpre-trainingする。
* common senseの取り込みをもっと上手くやる。
* multimodal 系タスクで、Unitなどのmultimodal modelでSOTAを出す。




# word craft





# BABY AI (BABY AI ++)
* Pros
    - 現状、人が少ない。
* Cons
    - 人が増えるかもしれない。MiniGridという有名な強化学習のベンチマークから派生しているので。
* babyai++ で、description text を生成することを学習する。。テスト時は、descriptionは自分で生成する。

* baselineは、gold graphを使ってしまっている。これをどうするか？
* 強化学習のSOTAを持ってくる
* baselineではKGがゴールドに近い。これを、in the wildにする。
* depthを広げる
* 3項関係を考える。
    * [Interpretable and Compositional Relation Learning by Joint Training with an Autoencoder](https://arxiv.org/abs/1805.09547)
    * KGの兄弟関係・親子関係を見る。
* 言語モデルで次の候補を生成させる。
* retrieverをrefineする。
    - QA
* モデルベースにして先読みさせる。
    - 「言語による推論が..」などと言って。
* 協調ゲームにする
    - 一緒に何かを作る。
    - 交換はあり。
    - 知識の交換もあり。
        * 例えば、お互いに持っている知識(KG)が違うとする。
* 対立ゲームにする
    - お互いの手は見えない。
    - 交換はできる。
    - 合成しているのは見える。



# 参考資料
* [minqi/wordcraft: A environment for benchmarking commonsense agents](https://github.com/minqi/wordcraft)
    - 過疎ってる!
    * 誰も経験が無いので、簡単なタスクからやっていくべき。丁度良い!!



# gSCAN
* 概要
    - BABY AIをcommand richにした感じ。
* Pros
    - 現状、人が少ない。
* Cons
    - 難しそう。




# gCOMM
* 概要
    - grid gameでかつ、協調ゲーム。speaker + listener




# text world
* Enhancing Text-based Reinforcement Learning Agents with Commonsense Knowledge
    - KB retrieverで解いている。これをNLPのSOTAにする。
        - REALM

## 参考資料
* [TextWorld - Microsoft Research](https://www.microsoft.com/en-us/research/project/textworld/)
* [microsoft/TextWorld](https://github.com/microsoft/TextWorld)





# word craft
* [word craft](./word_craft.md)




# 人狼知能
* [却下]
    - 人口があまりにも少ない。
    - データが無いので、強化学習できない。
        * まぁ、機械同士を戦わせて性能を上げることはできるかもしれない。
        * 先行研究では、bot同士の対戦で学習している。効果は小さい。


