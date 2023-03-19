# prompts

よしなに気になったプロンプトを投げ込んでいく

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
