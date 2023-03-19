# prompts

よしなに気になったプロンプトを投げ込んでいく

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

# 精度上げるために、質問をしてもらう

```
~~
このタスクで、最高の結果を出すために、追加の情報が必要な場合は、質問をしてください。
```

```
+ 情報が不十分な場合、返答せずにユーザーに聞き返してください。
```
