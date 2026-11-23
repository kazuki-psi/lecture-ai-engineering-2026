# 第6回 解答

## 演習

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
- MCP サーバーに公開したツールと、その説明文：ツールは、[glossary_get_lecture_summary]。説明は以下で、
  指定した回（1始まりの整数）の講義の要点を返す。
  
  「第3回では何を学ぶ？」のように、回の内容や関係を聞かれたときに使う。
  引数: {"lecture": {"title": "Lecture", "type": "integer"}}
- fetch サーバーを足したときのツール呼び出し（ツール名と引数）：ツール名と引数は以下。fetch_fetch({'url': 'https://modelcontextprotocol.io/'})
- awsのものは以下。aws_aws___search_documentation({'topics': ['general'], 'search_phrase': 'Amazon S3 バージョニング とは'})
<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->

- STEP 1 のツールの名前：
- STEP 2 の [tool call]：
- STEP 3 の [tool call]：
- STEP 4 の [tool call]：
- 気づき・疑問：

## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

- 取り組んだレベル：基礎 / 実装 / 発展
- やったこと：
- 結果：
- 気づき・疑問：
