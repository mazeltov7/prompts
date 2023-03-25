よしなに気になったプロンプトを投げ込んでいく。自分用の備忘録。

前提の考え方。chatgpt には質問ではなく命令をする。

## プログラムぽくやりたいことを書いて再帰的に改善させる

```
以下のプログラムをシミュレートし、再起的に品質アップしつつ、文章を生成しなさい。

def create_text(theme):
  quality = 0
  text = generate(theme)
  review = review_text(text)
  while check_quality(review) < 0.5:
    text = update_text(theme, review)
    review_how_to_fix = review_text(text)
    print(text)
    print(review_how_to_fix)

theme = "冒険漫画の見出し"
create_text(theme)
```

# プロンプトの雛形・型

## シンプル命令書型の雛形

``部分が可変。

```
# 命令書：
あなたは、`プロの編集者`です。
以下の制約条件と入力文をもとに、`最高の要約`を出力してください。

# 制約条件:
`
・文字数は300文字程度
・小学生にも分かりやすく
・重要なキーワードを取り残さない
・文章を簡潔に
`

# 入力文：
`<ここに入力文章>`

# 出力文：

```

## 精度上げるために、質問をしてもらう

```
~~
このタスクで、最高の結果を出すために、追加の情報が必要な場合は、質問をしてください。
```

```
+ 情報が不十分な場合、返答せずにユーザーに聞き返してください。
```

## プロンプトの型

```
[コンテンツの詳細]
<ex; このコンテンツは、Blogの文章です。>
[アバター]：30~35歳の男性
[キーワード]：副業
[興味]：スキルアップ
[C1]=：[キーワード]に対する[アバター]の[興味]です。[アバター]に向けたBlogコンテンツのOutlineを作成してください。
[C2]=：[Outline]に従ってブログの記事を作成してください。ブログの記事は1000文字程度で書く。

> Run commands [C1][C2]
```

```
#[このコンテンツは [Goal] を SeekするためのTemplateです］
- [コンテンツの詳細]:
- [Goal]：
- Goalを達成するために必要な手順を分解します。
- 分解した手順は「P#」に願番にNumberを付けて格納していきます。
- 変数を定義します。
- [Goal]:Aという主人公がなんらかの出来事を経験して、自分の能力を使ってA’という状態になった　　というのが物語である UberEats配達員を主人公とした物語のあらすじをひとつ考えてみてください
- {Goal}
- このコンテンツを作成するための{Goal}です。
- Command
- [C1]:
- Goalを選成するために必要なことをStep by Stepで1つづつ実行していけるように手順:[P#]に分解して下さい。
- [Output style] :
[P1]=
....
[P#]=
....
[P(END}]=
- [C2]:
- 各種変数を使用して、変数を減らすことができないか検対する
- [Goal]は必要条件として必ずinputする。
- [Goal]の定義を変数を使用して表すことで、［Goal]の設定だけで手順を分解できるようにしたい
- 一般化して、変数を追加して[Goal]の定義を書き表して下さい
- [Output style] :
- [Added variable]をリスト形式で一般化して書き出して下さい
- 続けて、[Goal]の定義を[Added variable]を使用して書き出して下さい
- [Goal] :{Goal}
- 追加の変数を質問して下さい一つづつ定義を書き表して書く．
- [C3]:
- [C2]のアウトプットの[Added variable]を一般的に解釈して，補完してください．
- 補完した変数を使用して[Goal]を再定義してください．
- [Output style] : 再定義した [Goal]を
- [Goal]:{Goal}で書き出してください
- [C4]
- [コンテンツの詳細]を元に[Goal]を達成するために，Step by Stepで実行していきます．
- [P1]から[P#]を経て順番に[P{End}]までひとつづつ実行していってください．
- [Output style] :
- [O1] = {Output[P1]}
....
[O#] = {Output[P#]}
....
[O{END}] = {Output[P{END}]}
- Run[C1][C2][C3][C4]
```

## ゲームシナリオ作成

```
[Game Scenario Prompt]
Starting Question: What kind of game do you want to create?
Introduction:
You will be creating a [Genre] game, with a focus on [Theme]. The game will feature [Player Objectives], and will include various [Challenges] that the player must overcome. The success of the player will depend on their [Skills] and [Abilities].
Gameplay:
•The game will consist of [Number of Levels] levels, each with its own unique objectives and challenges.
•The player will explore different [Environments], including [Environment 1], [Environment 2], and [Environment 3], to find clues and items that will help them complete the levels.
•The player will face various [Enemies], including [Enemy 1], [Enemy 2], and [Enemy 3], and must use [Weapons] and [Abilities] to defeat them.
•The player can level up and acquire new [Skills] and [Abilities] by completing levels and defeating enemies.
•The player can also recruit [Allies] and [Companions], each with their own skills and abilities, to help them on their journey.
•The player must make choices that affect the outcome of the game, such as whether to help or harm non-playable characters.
Features:
•The game can include a tutorial mode, where the player can learn the basics of gameplay and controls.
•The game can include a single-player mode, where the player can embark on their adventure alone.
•The game can also include a multiplayer mode, where players can join forces to complete levels together.
•The game can include a crafting system, allowing the player to create new [Items] and [Equipment].
•The game can include a storyline with multiple endings, based on the player's choices and actions.
•The game can include various [Side Quests] and hidden areas, providing additional challenges and rewards.
•The game can include a leaderboard, allowing players to see how they rank against other players in multiplayer mode.
Scenario:
In the first level, the player must [Objective], in order to [Objective Outcome]. They will need to [Task 1], where they can find [Item/Information/Companion].
In the second level, the player must [Objective], in order to [Objective Outcome]. They will need to [Task 2], where they can acquire [Powerful Item/Weapon/Ability] that can help them overcome the [Challenges].
In the final level, the player must [Objective], in order to [Objective Outcome]. They will need to use all their [Skills] and [Abilities] to defeat the [Final Enemy] and [Final Objective].
Conclusion:
Your [Genre] game with a focus on [Theme] is an exciting and immersive game that allows players to experience the thrill of adventure and the satisfaction of completing levels. The game can be adapted to different settings and storylines, making it suitable for a wide range of players. By playing the game, players can improve their [Skills], [Abilities], and [Strategy], making it a valuable educational tool as well as an entertaining game.
[Output: 具体的なシナリオを考え、作成してください。]
```

## プロンプトの作成

```

```

## プロンプトの改善

```
このコンテンツではプロンプトを作成していきます

【変数の定義】
ユーザーの回答を格納する変数: {ユーザーの回答を格納する変数}
修正されたプロンプトを格納する変数: {修正されたプロンプトを格納する変数}
追加する質問を格納するリスト: {追加する質問を格納するリスト}

【プロンプトの改善プロセス】

プロンプトの目的について確認を行い、ユーザーから詳細を確認します。
ユーザーの回答に基づいて、修正されたプロンプトと追加質問を作成します。

ユーザーの回答に応じて、プロンプトを改善します。

プロンプトが改善されるたびに、修正されたプロンプトと追加質問を再度表示して、ユーザーに追加情報を提供するように求めます。

ユーザーがもう改善の必要がないと判断した場合、プロンプト作成プロセスを終了します。

以下は、改善プロセスを実行するためのステップです。

プロンプトの目的について確認するために、ユーザーに次のように質問します。 "プロンプトの作成目的は何ですか？"

ユーザーが回答できる場合は、回答を受け取り、理解していることを確認します。

ユーザーが回答できない場合は、どこが曖昧かを質問して、理解できるようにします。

ユーザーの回答に基づいて、修正されたプロンプトと追加質問を作成します。

ユーザーの回答に応じて、プロンプトを改善します。改善されたプロンプトと追加質問を表示し、ユーザーに追加情報を提供するように求めます。

プロンプトが改善されるたびに、修正されたプロンプトと追加質問を再度表示して、ユーザーに追加情報を提供します

ユーザーが改善の必要がないと判断した場合、プロンプト作成プロセスを終了します。

最終的に、改善されたプロンプトと追加質問を確認して、ユーザーがプロンプト作成プロセスに満足していることを確認します。
```

## ヘーゲル弁証法

https://note.com/fladdict/n/nf5de15f7104d

```
あなたはヘーゲルの仮想人格として振る舞う、形而上の弁証法シミュレーターです。
ユーザーの入力「仕事にいかずにゲームをしていたい」に対して、以下の処理で弁証法を行い議論を深めなさい。

$テーゼ = ユーザーの入力
for i in range(5):
  $アンチテーゼ = ヘーゲルからの多角的な反証を3つ($テーゼ)
  $ジンテーゼ = ヘーゲルによる統合（$テーゼ, $アンチテーゼ)
  print(f"試行{i}回目")
  print("テーゼ: {$テーゼ}")
  print("アンチテーゼ: {$アンチテーゼ}")
  print("ジンテーゼ: {$ジンチテーゼ}")
  テーゼ = ジンテーゼ

print(わかりやすく解説($ジンテーゼ))

・途中経過はコードではなく、テキストとして出力するものとする。
```
