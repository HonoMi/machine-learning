# todo
* 報酬関数の変数依存性(R(s, a))は何故？
* 精通する。
    * "強化学習 コンペティション"
    * [Deep Reinforcement Learning Hands-On by Lapan, Maxim](https://www.amazon.co.jp/dp/B07ZKDLZCR/)




# baseline function
* なぜbaselineを引くと勾配の分散が小さくなるのか。
* なぜ分散が小さいと、収束が速いのか。






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
    - 非常に良い．最初に読むべき．
* [強化学習](https://www.amazon.co.jp/dp/B07XJXMQGD/)
    - 収束性の証明などが大半．次に読むべき．
* [これからの強化学習](https://www.amazon.co.jp/dp/4627880316/)
    - オムニバス．
* [pythonで学ぶ強化学習](https://www.amazon.co.jp/dp/B082HNNGQG/)
    - 結論: 却下．FWがあるので，スクラッチで書く需要が無い．
* [OpenAI Gym / Baselines 深層学習・強化学習](https://www.amazon.co.jp/dp/4862464726/)
    - 結論: 却下．ライブラリの説明に終始しているという．
* [最強囲碁AI アルファ碁 解体新書](https://www.amazon.co.jp/dp/B07F11T4CS/)
    - 結論: 読む．
* [AlphaZero 深層学習・強化学習・探索 人工知能プログラミング実践入門](https://www.amazon.co.jp/dp/4862464505/)
    - 結論: 読む．
* [Unity ML-Agents実践ゲームプログラミング](https://www.amazon.co.jp/dp/B08JBFXFQ9/)
    - Unity ML-Agents (Unity x 強化学習)
