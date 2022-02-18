# FAQ Search 

挨拶ができるやつは建築もできる

## yarukoto
[行政対話システムにおける検索エンジンTSUBAKIとBERTを併用したFAQ 検索の高度化](https://www.anlp.jp/proceedings/annual_meeting/2019/pdf_dir/F5-1.pdf)を試す。  
データセットは`子育てオープンデータ協議会`の[自治体におけるAIチャットボットの普及に向けたオープンデータ化についての「報告書」及び「FAQデータセット」を公開](https://www.asukoe.co.jp/kosodate_opendata_report/)を利用しています。

クエリと問い合わせ文は係り受け解析で、クエリと応答文をBERTを使って類似度を計算しているっぽい。

- 登録時: 問い合わせ文の係り受け解析結果と応答文の文書ベクトルを保存
- 検索時: クエリの係り受け解析結果と文書ベクトルをもとに検索を実行する

### To Do
- 係り受け解析の結果をElasticsearchで保存する 
- 

## Step 1: GiNZAで係り受け解析をする
ref:[GiNZA+Elasticsearchで係り受け検索の第一歩 - Taste of Tech Topics](https://acro-engineer.hatenablog.com/entry/2019/12/06/120000)

バージョンのせいか「胃：キリキリ」になって正しく主述がとれてない
FAQの文章にあたっては主述だけでは足りないように感じるので構文片を取るようにした
