# 2. GentleStart
* realization assumption: 経験誤差を0にすることができる．
* Finite Hypothesis Space の場合の汎化誤差性能
    - `(汎化誤差) <= (経験誤差) + log(|H|/delta) / m`




# 3. A Formal Learning Model
* PAC learnability
* agnostic PAC learnability: realization assumption 無し
    - いわゆる汎化誤差上限は，この定式化のことである．



# 4. Learning via Uniform Convergence
* Uniform Convergenceを使って，finite hypothesis classの汎化誤差上限を示す．
    - `(汎化誤差) <= sqrt[ (経験誤差) + 2log(2|H|/delta) / m ]`
    - (discretization trick) 計算機による数値の表現は，ビット列のパターン数が上限となる．このパターン数は有限なので，本議論によって汎化誤差上限を導出することができる．



# 5. The Bias Complexity Trade-off

# 6. The VC-Dimension
* VC-dimensionの導入
* finite class
    - `VCdim(H) <= log2(|H|)`
        * これは上限でしかない．実際にはもっと小さい場合もある．
* The fundamental theorem of PAC learnability
    - `const x (VCdim(H) + log(1/delta)) / e^2 <= m <= const x (VCdim(H) + log(1/delta)) / e^2`


# 10. Boosting
* AdaBoostの汎化誤差上限を導出する．
    - AdaBoostでは，stepに対して経験誤差が指数関数的に減少する．これは，前ステップで誤ったサンプルの重みを大きくして学習することに依る．
    - 経験誤差が減少することにより，汎化誤差もある程度のstepまでは，減少することが多い．



# 11. Model Selection and Validation
* ../theory.md
