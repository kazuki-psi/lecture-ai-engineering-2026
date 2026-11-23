# 第6回 解答

## 演習
- STEP 1 のツールの名前：[glossary_search_glossary]
- STEP 2 の [tool call]：glossary_search_glossary({'query': '3レベル'})
- STEP 3 の [tool call]：fetch_fetch({'url': 'https://modelcontextprotocol.io/'})
- STEP 4 の [tool call]：aws_aws___search_documentation({'topics': ['general'], 'search_phrase': 'Amazon S3 バージョニング とは'})
- 気づき・疑問：

- `--list-tools` で見えたツール名と、第3回（`--mcp` なし）との違い：見えたツールは以下。
    [glossary_search_glossary]
    講座の用語集から用語を検索し、定義と、どの回で扱うかを返す。
    
    AIエンジニアリングの用語や、この講座（AIE2026）に固有の言葉について
    答える前に使うこと。query には調べたい用語を1つだけ入れる（例: "LoRA"）。
    引数: {"query": {"title": "Query", "type": "string"}}
`--mcp` なしの時は以下で、サーバー名（glossary_）がない。
    モデルに見えているツール: 1 個
    [search_materials]
    第1〜3回の本講義資料を検索し、関連ページの本文・タイトル・ページ番号を返す。
    queryに調べたい内容を指定する。
    引数: {"query": {"type": "string"}}
- `--mcp --trace` で見えたツール呼び出し（ツール名と引数）と、`requests` の回数：ツール名と引数は「glossary_search_glossary({'query': '3レベル'})」。モデル応答は2回。
- fetch サーバーを足したときのツール呼び出し（ツール名と引数）：ツール名と引数は以下。fetch_fetch({'url': 'https://modelcontextprotocol.io/'})
- awsのものは以下。aws_aws___search_documentation({'topics': ['general'], 'search_phrase': 'Amazon S3 バージョニング とは'})


## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

- 取り組んだレベル：基礎
- やったこと：MCP サーバーに公開したツールと、その説明文：ツールは、[glossary_get_lecture_summary]。説明は以下で、
  指定した回（1始まりの整数）の講義の要点を返す。
  
  「第3回では何を学ぶ？」のように、回の内容や関係を聞かれたときに使う。
  引数: {"lecture": {"title": "Lecture", "type": "integer"}}
- 結果：一覧にget_lecture_summaryが表示されるようになった。
- 気づき・疑問：サーバーへの公開はかなり簡単にできる。

- 取り組んだレベル：実装
- やったこと：make_quiz のMCPサーバーでの公開と、存在しない回では作れないことを表示するような実装を行なった。
[glossary_make_quiz]
  指定した回の用語から1つ選び、確認問題と答えを返す。
  
  「第2回の確認問題を出して」のように、講義内容の復習用の問題を
  求められたときに使う。指定した回の用語がない場合は、その旨を返す。
  引数: {"lecture": {"title": "Lecture", "type": "integer"}}
- 結果：make_quizも追加でき、以下のようなメッセージが適切に表示できることを確認できた。
```
第99回の講義は用意されていないため、クイズを作成することができません。

現在ご用意しているのは以下の回です。
- 第1回
- 第2回
- 第3回
- 第4回
- 第6回
どの回のクイズをご希望でしょうか？
```
- 気づき・疑問：こちらもサーバーへの公開はかなり簡単にできる。
