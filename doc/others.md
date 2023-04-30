- [一緒にスクラム開発\_\_\_GPT-4 と人間が共創するプロダクトの進化.pdf](https://speakerdeck.com/itohiro73/xu-nisukuramukai-fa-gpt-4toren-jian-kagong-chuang-suruhurotakutonojin-hua)
  - ペアプロ良き
- [ChatGPT によるデータ変換がもたらすインパクト](https://speakerdeck.com/masahiro_nishimi/chatgptniyorudetabian-huan-gamotarasuinpakuto?slide=7)
  - データ変換よき
- [ChatGPT API と Faiss を使って長い文章から質問応答する仕組みを作ってみる](https://qiita.com/sakasegawa/items/16714fa132e874cab069#embeddingsqa%E3%81%AE%E5%AE%9F%E8%A3%85-bertjapanesetokenizer%E3%82%92%E4%BD%BF%E3%81%86)

  - データ食わせて要約とかの時に便利そう
  - この辺りも
    - また、陳述記憶はエピソード記憶と意味記憶に分けられます。○○ に行った、○○ の話をした、というようなエピソード記憶は 1 日単位のサマリ用の embeddings を保管する vector store に格納すると良さそうです。
    - また、意味記憶は知識や概念についての記憶であり、人物や物事について上記とはことなる vector store に格納するべきでしょう。

- 「いつもお世話になってます。」とか丁寧にプロンプト入れると、GPT も返答が丁寧になる説（雑だと、候補 1 個しか返さないところ、個数指示しなくても丁寧にいうと 10 個候補出すなど）

  - [ChatGPT4 はなぜ「お世話になってます」を文面に付けると複数の提案をするのか　-単語と意味と語彙-](https://note.com/nouhuhoumei/n/n1273c335406e?fbclid=IwAR3zarByaRFz9HjpexGY9TTpkiHvXWl5bnkMfdw13NWFlUAY_xrV34KOheY)

- https://github.com/dair-ai/Prompt-Engineering-Guide
-
- [https://github.com/openai/openai-cookbook/blob/main/techniques_to_improve_reliability.md](https://github.com/openai/openai-cookbook/blob/main/techniques_to_improve_reliability.md)
- https://github.com/f/awesome-chatgpt-prompts
- [https://qiita.com/sonesuke/items/981925cfcc610a602e94](https://qiita.com/sonesuke/items/981925cfcc610a602e94)
-

- [Building LLM applications for production](https://huyenchip.com/2023/04/11/llm-engineering.html)

## Thoughts

- ハルシネーションもあるので、「90 点の出来で OK なものは LLM」、「91 点以上それ以上必要なものにはまだ使えない」みたいな形は実感としてもあり得そう。
  - 大枠やたたき台を LLM で準備して、修正・調整を一手でやる、みたいなのはかなりハマる。
- 機械学習エンジニアが「各現場向けにカスタマイズされた LLM ベースの ML プロダクト」を作る必要性

## services

- [ChatPDF](https://www.chatpdf.com/)
-
