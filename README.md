# Pythonで学ぶ強化学習 -入門から実践まで-

[Pythonで学ぶ強化学習 -入門から実践まで-](https://www.amazon.co.jp/dp/4065142989/)の実装コードリポジトリです。

## Index

* [Setup](https://github.com/icoxfog417/baby-steps-of-rl-ja#setup)
* [Day1: 強化学習の基礎](https://github.com/icoxfog417/baby-steps-of-rl-ja#day1-%E5%BC%B7%E5%8C%96%E5%AD%A6%E7%BF%92%E3%81%AE%E5%9F%BA%E7%A4%8E)
* [Day2: 強化学習の解法(1): 環境から計画を立てる](https://github.com/icoxfog417/baby-steps-of-rl-ja#day2-%E5%BC%B7%E5%8C%96%E5%AD%A6%E7%BF%92%E3%81%AE%E8%A7%A3%E6%B3%951-%E7%92%B0%E5%A2%83%E3%81%8B%E3%82%89%E8%A8%88%E7%94%BB%E3%82%92%E7%AB%8B%E3%81%A6%E3%82%8B)
* [Day3: 強化学習の解法(2): 経験から計画を立てる](https://github.com/icoxfog417/baby-steps-of-rl-ja#day3-%E5%BC%B7%E5%8C%96%E5%AD%A6%E7%BF%92%E3%81%AE%E8%A7%A3%E6%B3%952-%E7%B5%8C%E9%A8%93%E3%81%8B%E3%82%89%E8%A8%88%E7%94%BB%E3%82%92%E7%AB%8B%E3%81%A6%E3%82%8B)
* [Day4: 強化学習に対するニューラルネットワークの適用](https://github.com/icoxfog417/baby-steps-of-rl-ja#day4-%E5%BC%B7%E5%8C%96%E5%AD%A6%E7%BF%92%E3%81%AB%E5%AF%BE%E3%81%99%E3%82%8B%E3%83%8B%E3%83%A5%E3%83%BC%E3%83%A9%E3%83%AB%E3%83%8D%E3%83%83%E3%83%88%E3%83%AF%E3%83%BC%E3%82%AF%E3%81%AE%E9%81%A9%E7%94%A8)
* [Day5: 深層強化学習の弱点](https://github.com/icoxfog417/baby-steps-of-rl-ja#day5-%E6%B7%B1%E5%B1%A4%E5%BC%B7%E5%8C%96%E5%AD%A6%E7%BF%92%E3%81%AE%E5%BC%B1%E7%82%B9)
* [Day6: 強化学習の弱点を克服するための手法](https://github.com/icoxfog417/baby-steps-of-rl-ja#day6-%E5%BC%B7%E5%8C%96%E5%AD%A6%E7%BF%92%E3%81%AE%E5%BC%B1%E7%82%B9%E3%82%92%E5%85%8B%E6%9C%8D%E3%81%99%E3%82%8B%E3%81%9F%E3%82%81%E3%81%AE%E6%89%8B%E6%B3%95)
* [Day7: 強化学習の活用領域](https://github.com/icoxfog417/baby-steps-of-rl-ja#day7-%E5%BC%B7%E5%8C%96%E5%AD%A6%E7%BF%92%E3%81%AE%E6%B4%BB%E7%94%A8%E9%A0%98%E5%9F%9F)

[Support Content](https://github.com/icoxfog417/baby-steps-of-rl-ja#support-content)

## Setup

サンプルコードをダウンロードするのにGit、実行をするのにPythonの環境が必要です。そのため、以下2つのソフトウェアをダウンロードし、インストールしてください。なお、本書ではPythonの環境を作成するのにMinicondaを使用します。

1. [Git](https://git-scm.com/)
2. [Python (Miniconda)](https://conda.io/miniconda.html)
   * ダウンロードするのは、Python3の方です

インストールが終了したら、まずソースコードのダウンロードを行います。ターミナル/コマンドプロンプトを開き、作業するディレクトリで以下のコマンドを実行してください。

```
git clone https://github.com/icoxfog417/baby-steps-of-rl-ja.git
```

コマンドを実行すると、`baby-steps-of-rl-ja`というディレクトリが作成されていると思います。これで、ダウンロードは完了しました。ダウンロードしたフォルダに移動しましょう。

```
cd baby-steps-of-rl-ja
```

続いて、ソースコードの実行環境を作成します。実行環境を作成するのに、Minicondaをインストールすることで使えるようになる`conda`コマンドを使用します。これから、本書の実行環境である`rl-book`という環境を作成します。

```
conda create -n rl-book python=3.6
activate rl-book  # Mac/Linuxの場合 source activate rl-book
```

`activate`を実行することで、ターミナルの先頭に`(rl-book)`がついたでしょうか。これが、実行環境が有効化されているサインです。本書のソースコードを実行する際は、まず実行環境が有効化されているか=`(rl-book)`が先頭についているか、を確認してください。なお、無効化する際は`deactivate`のコマンドを実行します。

(なお、`python=3.6`と指定しているのは、執筆時点のTensorFlowがPython3.6でしか動かないためです。[#20517](https://github.com/tensorflow/tensorflow/issues/20517)がCloseされればこの指定は不要になります)。

実行環境に、実行に必要なライブラリをインストールします(`(rl-book)`が先頭についているか確認して実行してください)。

```
pip install -r requirements.txt
```

以下のように、`welcome.py`を実行してみてください。ゲーム画面が立ち上がればセットアップは完了です。

```
python welcome.py
```

## Day1: 強化学習の基礎

**Day1's Goals**

* 強化学習と、機械学習、人工知能といったキーワードの関係を理解する
* 強化学習以外の学習法に対する、強化学習のメリット・デメリットを理解する
* 機械学習の基本的な仕組みを理解する

**Summary**

* 強化学習とは?
  * 強化学習 ⊂ 機械学習 ⊂ 人工知能
  * 機械学習 = 「機械」(=モデル)を「学習」させる手法
  * 強化学習 = 「学習」方法の一種
  * 強化学習は、連続した行動を通じて獲得できる「報酬の総和」を最大化することを目的とする
  * 行動の評価方法と、(評価に基づく)行動の選び方(=戦略)を学習する
* 強化学習のメリット・デメリット
  * メリット: 評価尺度の定義が難しいタスクでも扱うことができる(行動の評価方法を学習するため)
  * デメリット: どんな評価を元に、どんな行動を学習するのかはモデル任せになる
* 強化学習の基本的な仕組み
  * 強化学習では、与えられる「環境」が一定のルールに従っていることを仮定する。そのルールを、 **マルコフ決定過程(Markov Decision Process: MDP)** という。
  * MDPの構成要素とその関係は、以下のように図式化できる。
  * MDPにおける報酬は、「直前の状態と遷移先」に依存する。この報酬を **即時報酬(Immediate reward)** という。
  * 報酬の総和(=即時報酬の合計)は、当然事前には知ることができない。そのため見積りを行うが、見積もった値を **期待報酬(Expected reward)** 、また **価値(Value)** と呼ぶ。
  * 見積もる際に、将来の即時報酬については割り引いて考える。割り引くための係数を **割引率(discount factor)** と呼ぶ。

<p align="center">
  <img src="./doc/mdp.PNG" width=800 alt="mdp.PNG"/>
  <p align="center">MDPの構成要素とその関係</p>
</p>

**Exercises**

* [MDPの実装](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/DP/environment.py)

## Day2: 強化学習の解法(1): 環境から計画を立てる

**Day2's Goals**

* 行動評価の指標となる「価値」の定義を理解する
* 「状態評価」を動的計画法で学習する手法と実装方法を理解する
* 「戦略」を動的計画法で学習する手法と実装方法を理解する
* モデルベースの手法とモデルフリーの手法の違いを理解する

**Summary**

* 「価値」の定義
  * Day1で定義した「価値」を計算するには、(割引率をかける)将来の即時報酬が判明している必要がある
  * これは、当然実際にはわからない。そこで、式を再帰的に定義することで計算を持ち越しできるようにする
  * また、実際の報酬は確率的に発生する。そのため、報酬の値は期待値(確率x値)で表すようにする。確率x値とは、行動確率(戦略) x 行動の結果得られる報酬、となる
  * 「価値」を再帰的かつ期待値で計算した式を、 **Bellman Equation** と呼ぶ。
* 状態評価の学習と、戦略の学習
  * **Bellman Equation** では期待値の計算に戦略を使用する。このため、価値を計算=>得られる価値が高くなるよう、戦略を更新=>戦略が更新されたため、価値を計算し直す=>計算し直した価値で戦略を更新・・・というプロセスを繰り返していくことになる。
  * 動的計画法において、戦略と価値を相互に更新するプロセスを **Policy Iteration** と呼ぶ
  * 一方、価値が計算できるなら価値が一番高いところを選べばいい、という素朴な考えもある。この場合、価値=戦略となるため、戦略が不要になる。
  * 動的計画法において、価値=戦略とし価値のみ更新するプロセスを **Value Iteration** と呼ぶ
  * 戦略を持つか(Policyベース)価値=戦略とするか(Valueベース)は、強化学習の手法分類する際の重要な観点となる
* モデルベースとモデルフリー
  * 動的計画法では、エージェントを一切動かさずに戦略/価値を学習した。このような芸当が可能なのは、遷移関数と報酬関数が明らかであり、シミュレーションが可能であるため。
  * こうした、環境の情報を元に学習する手法を **モデルベース** の手法と呼ぶ。遷移関数と報酬関数がわかっていることは少ないため、実際は推定を行うことになる
  * 一方、シミュレーションではなく実際にエージェントを動かすことで得られた経験を元に学習する方法を **モデルフリー** の手法と呼ぶ。モデルの情報(遷移関数/報酬関数)が必要ないため、モデル「フリー」と呼ばれる
  * 環境が高度になるほどモデルの推定が困難になるため、一般的にはモデルフリーが用いられることが多い。しかし、表現力の高いDNNの登場によりこの限りではなくなっているほか、モデルフリーとモデルベースを併用する試みも行われている。

**Exercises**

* [価値の定義: Bellman Equationの実装](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/DP/bellman_equation.py)
* [価値反復法(Value Iteration)、戦略反復法(Policy Iteration)の実装](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/DP/planner.py)

価値反復法、戦略反復法について実行結果を試せるシミュレーターを用意しています。以下のスクリプトを実行し、立ち上がったサーバーにアクセスしてみてください。

```
python DP/run_server.py
```

http://localhost:8888/

<img src="./doc/application.PNG" width=600 alt="application.PNG"/>

* Areaで行・列を指定し、Drawのボタンを押すことで指定したサイズの迷路を作成できる
* 迷路内のセルを選択した後、Cell SettingにあるTreasure/Danger/Blockのボタンを押すことで、迷路のマスの設定を行うことができる。Treasureはプラスの、Dangerはマイナスの報酬のゴール。Blockは、移動できないセルとなる
* 迷路の設定ができたら、SimulationにあるValue Iteration/Policy Iterationどちらかのボタンを押すと、ボタンに応じたアルゴリズムで解いた結果が参照できる

## Day3: 強化学習の解法(2): 経験から計画を立てる

Day3では経験から計画を立てる方法を学びます。経験から計画を立てる際は、3つの観点がありました。

* 経験の蓄積と活用のバランス
  * [Epsilon-Greedy法](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/EL/notebooks/Epsilon%26Greedy.ipynb)
* 実績から計画を修正するか、予測で行うか
  * [Monte Carlo](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/EL/notebooks/Monte%20Carlo.ipynb)
  * [Temporal Difference](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/EL/notebooks/Q-learning.ipynb)
* 経験を状態評価、戦略どちらの更新に利用するか
  * [On policy: SARSA](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/EL/notebooks/SARSA.ipynb)
  * [Off policy: Q-learning](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/EL/notebooks/Q-learning.ipynb)
  * [Actor Critic](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/EL/notebooks/Actor%26Critic.ipynb)

「経験」とは、具体的には見積もった価値と実際の価値との差異でした。この差異(=誤差)を小さくすることが学習の本質となります。

<img src="./doc/td.PNG" width=800 alt="td.PNG"/>

## Day4: 強化学習に対するニューラルネットワークの適用

Day4では、強化学習をパラメーターを持った関数=ニューラルネットワークで実装する手法を学びます。Day3まで行動は状態/行動のテーブルから決定されていました(Q-Table)。Day4では状態を入力、行動や行動価値を出力とする関数で決定を行います。この関数としてニューラルネットワークを使用します。

* [ニューラルネットワークの仕組み](https://github.com/icoxfog417/baby-steps-of-rl-ja/tree/master/FN/nn_tutorial)
* [価値を関数から算出する](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/FN/value_function_agent.py)
  * [価値をDNNで算出する(DQN)](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/FN/dqn_agent.py)
* [行動を関数から決定する(戦略の関数化)](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/FN/policy_gradient_agent.py)
  * [戦略をDNNで算出する(A2C)](https://github.com/icoxfog417/baby-steps-of-rl-ja/blob/master/FN/a2c_agent.py)

これまでの手法、またDNN(ディープニューラルネットワーク)を利用した手法、双方を含めた手法の系統図は以下のようになっています。

<img src="./doc/rl_ways.PNG" width=800 alt="rl_ways.PNG"/>

## Day5: 深層強化学習の弱点

強化学習に対するDNNの適用は、良いことばかりではありません。具体的には、以下のような問題が現れます。

* サンプル効率が悪い
* 局所最適な行動に陥る、過学習することが多い
* 再現性が低い

Day4の実装では、こうした現実に対応するため、実装を工夫していました。端的には、「１回の学習結果を無駄にしない」ための工夫です。再現性が低いため何度も実験が必要ですが、サンプル効率が悪いため1回の実験に多くの時間がかかります。そのため、「1回」の実験の重みは大きく、これを無駄にしないための工夫が必要です。

具体的には、以下の対策を取っています。

* モジュール化することでテストしやすくする
* ログをしっかりとる

<img src="./doc/train_architecture.PNG" width=800 alt="train_architecture.PNG"/>


## Day6: 強化学習の弱点を克服するための手法

Day6では、Day5で紹介した弱点に対する根本的な対処方法(アルゴリズム的な改良)を扱います。

* サンプル効率が悪い
  * 環境/状態の学習と、そこでの行動方法の学習との分離:「環境認識の改善」
  * [モデルベースとの組み合わせ(Dyna)](https://github.com/icoxfog417/baby-steps-of-rl-ja/tree/master/MM)
* 局所最適な行動に陥る、過学習することが多い
  * 人がある程度誘導してやる: 模倣学習・逆強化学習
  * [模倣学習 (DAgger)](https://github.com/icoxfog417/baby-steps-of-rl-ja/tree/master/IM)
  * [逆強化学習](https://github.com/icoxfog417/baby-steps-of-rl-ja/tree/master/IRL)
* 再現性が低い
  * 新しい学習方法: [進化戦略](https://github.com/icoxfog417/baby-steps-of-rl-ja/tree/master/EV)

なお、サンプル効率については「環境認識の改善」以外に多くの方法があります。以下が、様々な手法をまとめたものになります。

<img src="./doc/sample_improve.PNG" width=600 alt="sample_improve.PNG"/>

## Day7: 強化学習の活用領域

Day7では強化学習を活用する方法を探ります。具体的には、強化学習を活用する観点を整理し、観点ごとの事例、開発を支援ツールなどをまとめています。

<img src="./doc/rl_application.PNG" width=800 alt="rl_application.PNG"/>


## Support Content

プログラミングが初めて、という方のために参考になるコンテンツを用意しています。最近はプログラムを学ぶ書籍などは充実しているため、もちろんそれらで補完して頂いて構いません。

* Python
  * [python_exercises](https://github.com/icoxfog417/python_exercises)
* Git
  * [使い始めるGit](https://qiita.com/icoxfog417/items/617094c6f9018149f41f)
