# 第3回 解答

## 演習

- 第1回（素のLLM）とエージェントの回答の違い：素のLLMは講座内容におけるレベルを理解していなかったので、一般的な文脈で答えたが、今回は、基礎実装発展という宿題のレベルを正確に答えた。
- `--trace` で見えたツール呼び出し（ツール名と引数）：earch_glossary({'query': 'LoRA'})と、search_glossary({'query': 'QLoRA'})
- 1つの質問での LLM 呼び出し回数（`requests`）：2回
- 追加したツールと、docstring に書いた説明：追加したツールは、[make_quiz]で、説明は以下。
  ```
  指定した回の用語から1つ選び、確認問題と答えを返す。
  
  「第2回の確認問題を出して」のように、講義内容の復習用の問題を
  求められたときに使う。指定した回の用語がない場合は、その旨を返す。
  引数: {"lecture": {"type": "integer"}}
  ```

## 宿題

- 取り組んだレベル：基礎
- やったこと：search_glossary の docstring の「query には調べたい用語を1つだけ入れる」を「まとめて入れる」に変えてみた。
- 結果：同様に、LoRAとQLoRAの違いを求める質問をしてみると、[tool call]は2回だったものが1回になり、search_glossary({'query': 'LoRA QLoRA'})を実行していた。回答内容にはそこまで差は感じられなかった。
- 気づき・疑問：docstringの変更のみで、動きに違いが出ることがわかった。

- 取り組んだレベル：実装
- やったこと：save_learning_log というtoolを作り、この操作は承認を求めるように実装を行った。
- 結果：learning_log/log.md に記録した学習記録が保存されるようになった。
- 気づき・疑問：簡単に機能を追加できることがわかった。

- 取り組んだレベル：発展
- やったこと：Piをインストールして使ってみた。
- 結果：
  - 現在の自分のエージェントは、学習支援のためのものだが、Piは「You are a coding assistant running inside pi, a coding agent harness.
  Help users inspect files, run commands, and modify code.」と書いてあり、一般コーディングアシスタントとして定義されていた。
  - selectedTools: [...(input.selectedTools ?? ["read", "bash", "edit", "write"])],など、ファイルを操作できることが読み取れた。
  - renderProjectContextという機能があり、プロジェクト固有の動きができることが読み取れた。
- 気づき・疑問：特定の機能だけでいいなら、自作のものは軽量で使いやすいと思った。