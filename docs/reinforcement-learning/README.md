# todo
* 報酬関数 R(s, a)ってなぜ？ R(s') じゃないの？
* 精通する。
    * "強化学習 コンペティション"
    * [Deep Reinforcement Learning Hands-On by Lapan, Maxim](https://www.amazon.co.jp/dp/B07ZKDLZCR/)




# baseline function
* なぜbaselineを引くと勾配の分散が小さくなるのか。
* なぜ分散が小さいと、収束が速いのか。





# POMDP
* POMDPとマルコフ性の関係
    - まず、定義はまったく関係ない。POMDP(Partially Observable MDP)は状態の一部しか観測できないという意味であって、マルコフ性については何も言っていない。一方で、以下のように関係する:
        - マルコフ性が成り立っていない環境(e.g., 2 step前までの過去に依存する。)において、「現在の状態しか見ない」という問題設定にすると、POMDPになる。
        - 環境が決定論的である場合、「a_tの系列」と「s_t」は等価である。つまり、a_tを全て記憶しておけば(=マルコフ性が成り立たないと思って適切なagentを作成すれば)s_tを復元できる。よって、MDPとなる。


# Off-policy vs On-policy
* [原論文](http://proceedings.mlr.press/v32/silver14.pdf)
    - 一番参考になる。
    - 本論文では、deterministic policy gradientを導出した。
    - 背景も含めた結論:
        - stochasticの場合も、off-policy gradientは存在する。ただし、importance sampling ratioをかけ算する必要があり、これが発散したりして厄介。
        - deterministicの場合はimportance sampling ratioが消えるので、うれしい。
* [Doubt: Why is DDPG off-policy?](https://www.reddit.com/r/reinforcementlearning/comments/9dhga2/doubt_why_is_ddpg_offpolicy_is_it_because_they/)
* [Deterministic Policy Gradient Algorithms - Qiita](https://qiita.com/ku2482/items/7fd5fb65666328209ace)
* [Why is DDPG an off-policy RL algorithm? - Artificial Intelligence Stack Exchange](https://ai.stackexchange.com/questions/20773/why-is-ddpg-an-off-policy-rl-algorithm)
* [DDPGでPendulum-v0（強化学習, tensorflow2）](https://horomary.hatenablog.com/entry/2020/06/26/003806)




# 参考資料
* [強化学習](https://www.amazon.co.jp/dp/4627826613/)
    - 聖典。強化学習のお気持ちが分かる。
* [Deep Reinforcement Learning Hands-On](https://www.amazon.co.jp/gp/product/B07ZKDLZCR/)
    - ハンズオンしながら最先端のアルゴリズムまでを解説。有機的に理解できて良い。
    - 各アルゴリズムがどのようなモチベーションで作られたのか。実際の性能はどうか。
* [強化学習](https://www.amazon.co.jp/dp/B07XJXMQGD/)
    - 収束性の証明などが大半．次に読むべき．
* [OpenAI Gym / Baselines 深層学習・強化学習](https://www.amazon.co.jp/dp/4862464726/)
    - Gymの概要。サクッと読んで雰囲気をつかむのに良かった。
* [最強囲碁AI アルファ碁 解体新書](https://www.amazon.co.jp/dp/B07F11T4CS/)
    - Alpha系の概要。サクッと読める。
* [AlphaZero 深層学習・強化学習・探索 人工知能プログラミング実践入門](https://www.amazon.co.jp/dp/4862464505/)
    - Alpha系の概要。サクッと読める。
* [Unity ML-Agents実践ゲームプログラミング](https://www.amazon.co.jp/dp/B08JBFXFQ9/)
    - Unity ML-Agents (Unity x 強化学習)
* [pythonで学ぶ強化学習](https://www.amazon.co.jp/dp/B082HNNGQG/)
    - 結論: 却下．FWがあるので，スクラッチで書く需要が無い．
* [これからの強化学習](https://www.amazon.co.jp/dp/4627880316/)
    - オムニバス．微妙。sketchyで焦点が無い。
