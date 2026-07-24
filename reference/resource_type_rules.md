# 資源タイプ 記述ルール（公式準拠）

資源タイプでは、語彙名と、その語彙に対応するURIを組にして記述します。
語彙名が異なっても同じURIを共有する場合があるため、URIだけでは値を決められません。

このファイルは、JPCOARスキーマ **2.0** の公式資料から、資源タイプの定義、属性、統制語彙、記述ルールを整理したものです。
記載内容は、次の公式資料のみを典拠とします。

- [#15 資源タイプ（`dc:type`）](https://schema.irdb.nii.ac.jp/ja/schema/2.0/15)
- [資源タイプ語彙別表【Ver2.0】](https://schema.irdb.nii.ac.jp/ja/2.0/resource_type_vocabulary)

> このファイルには、公式説明ページと公式別表に記載されたスキーマ層の情報だけを収録します。
> DOI登録要件と本ガイド独自の運用方針は含みません。
> 記入レベル記号は [フローチャート共通規約](../decision-trees/CONVENTIONS.md)、実務上の判断手順は [資源タイプ入力フローチャート](../decision-trees/resource-type.md)、DOI登録要件は [JPCOAR、JaLC、Crossref要件対照表](JPCOAR_JaLC_Crossref_requirements.md) を参照してください。

---

## #15 資源タイプ `dc:type`

### 定義

| 項目 | 内容 |
|------|------|
| 要素名 | `dc:type` |
| 記入レベル | M（必須） |
| 繰返回数 | 1（繰返不可：必須） |
| 統制語彙 | [資源タイプ語彙別表【Ver2.0】](https://schema.irdb.nii.ac.jp/ja/2.0/resource_type_vocabulary) |
| 親要素 | なし |

### 属性

| 属性 | 記入レベル | 繰返回数 | 値 |
|------|-----------|----------|-----|
| `rdf:resource` | M（必須） | 1（繰返不可：必須） | 選択した統制語彙に対応する COAR Resource Type の URI |

### 記述ルール

- コンテンツの種類を、資源タイプ語彙別表から選択して記入する。
- `rdf:resource` には、選択した統制語彙に対応する COAR Resource Type の URI を記入する。
- `departmental bulletin paper`（紀要論文）および `article`（記事）には、`journal article`（学術雑誌論文）と同じ URI `http://purl.org/coar/resource_type/c_6501` を記入する。

### 統制語彙

公式別表に掲載されている語彙を、カテゴリ別に示します。
公式別表のカテゴリ見出しは `Conference object` ですが、その配下の現行語彙名は `conference output` です。

| カテゴリ | 語彙 | `rdf:resource` | 定義 |
|----------|------|----------------|------|
| Article | `conference paper` | `http://purl.org/coar/resource_type/c_5794` | 会議に提出され、参加者に発表された論文で、会議録に掲載される。 |
| Article | `data paper` | `http://purl.org/coar/resource_type/c_beb9` | 特定のデータセットやデータセットグループについて記述され、学術雑誌における査読論文の形式で出版されるもの。データ自体に関する記述、取集状況、データの特徴に関する情報、データへのアクセスや再利用の可能性に関して主に記述する。 |
| Article | `departmental bulletin paper` | `http://purl.org/coar/resource_type/c_6501` | 大学や研究所等が発行する紀要類に掲載された論文。表紙や目次はOtherとする。国際的に流通する際は「Journal Article」として出力される。 |
| Article | `editorial` | `http://purl.org/coar/resource_type/c_b239` | 学術雑誌の編集長によって記述された、政治的、社会的、文化的、専門的な問題に関する見解を示したエッセイ。 |
| Article | `journal` | `http://purl.org/coar/resource_type/c_0640/` | ある主題に関する独自の研究や最新の動向を広めることを目的とする逐次刊行物。（出典：ODLIS https://products.abc-clio.com/ODLIS/odlis_jk.aspx [2022-03-14]を一部改変） |
| Article | `journal article` | `http://purl.org/coar/resource_type/c_6501` | 特定の主題に関して研究を実施した1人以上の著者によって執筆され、学術雑誌に掲載された論文。 |
| Article | `newspaper` | `http://purl.org/coar/resource_type/c_2fe3` | 折りたたまれ、ホッチキス止めされていない紙面で構成され、ニュースや記事、広告、通信を含む、印刷された出版物（通常は日刊または週刊）。 |
| Article | `review article` | `http://purl.org/coar/resource_type/c_dcae04bc` | 二次情報であり、他の記事について書かれた論文。オリジナルの研究に関する報告ではない。 |
| Article | `other periodical` | `http://purl.org/coar/resource_type/QX5C-AR31/` | 既存の語彙に該当しない「テキスト」資料。 |
| Article | `software paper` | `http://purl.org/coar/resource_type/c_7bab` | ツールの開発に関する論理的根拠や構築時に使用したコードの詳細情報を含むもの。 |
| Article | `article` | `http://purl.org/coar/resource_type/c_6501` | 上記には含まれない、学術論文以外の記事。国際的に流通する際は「Journal Article」として出力される。 |
| Book | `book` | `http://purl.org/coar/resource_type/c_2f33` | 1巻またはセットで完結する逐次性のない出版物で、原則ISBNで識別される。 |
| Book | `book part` | `http://purl.org/coar/resource_type/c_3248` | 図書の章または一節で、通常は見出しまたは番号で区別される。 |
| Cartographic Material | `cartographic material` | `http://purl.org/coar/resource_type/c_12cc` | 地球全体または一部、あるいは天体を任意のスケールで表現したもの。地図資料には、航空図、航海図、天体図、地図帳、地球儀、ブロックダイアグラム、地区、空中写真、鳥瞰図などの2次元および3次元の地図と図面（想像上の場所の地図を含む）が含まれる。 |
| Cartographic Material | `map` | `http://purl.org/coar/resource_type/c_12cd` | 地球または別の天体の地表に関連する物質や特徴を抜粋し、平面に縮小したもの。 |
| Conference object | `conference output` | `http://purl.org/coar/resource_type/c_c94f` | 会議で発表された、プレゼンテーション資料、会議報告、講義資料、抄録、デモンストレーションなどの電子的な資料全般。会議発表論文や会議発表ポスターは、この語彙ではなく、当該語彙を使用する。 |
| Conference object | `conference presentation` | `http://purl.org/coar/resource_type/R60J-J5BD/` | 会議、シンポジウム、セミナー、講演会、ワークショップ、その他イベントで、参加者にむけてアイデアや研究成果を発表するテキスト、図表などのスライド資料。（出典：FaBiO, the FRBR-aligned Bibliographic Ontology http://purl.org/spar/fabio/Presentation [2022-03-14]を一部改変） |
| Conference object | `conference proceedings` | `http://purl.org/coar/resource_type/c_f744` | 会議で発表された資料の集合であり、付属的な資料も含む会議の公式な記録。 |
| Conference object | `conference poster` | `http://purl.org/coar/resource_type/c_6670` | 会議に提出され、ポスター発表に用いられたポスターで、会議録に掲載される。 |
| Dataset | `aggregated data` | `http://purl.org/coar/resource_type/ACF7-8YT9/` | 広範な分類、集団、あるいは範疇に関する統計。個人レベルのデータから平均、合計等の数値が導出されており、それらの分類、集団あるいは範疇に属する個人の特性を判別することは不可能である。例えば、失業者数とその年齢層に関する特定の地域の統計、各警察管区の統計から導かれた特定の犯罪の発生件数についての全国統計等があげられる。（出典：人文学・社会科学総合データカタログ（JDCat）統制語彙「調査方法」https://www.jsps.go.jp/j-di/data/Collection_Method.xlsx [2022-03-14]） |
| Dataset | `clinical trial data` | `http://purl.org/coar/resource_type/c_cb28/` | 臨床試験（介入についての生物医学的または行動学的な有効性を評価するために、被験者であるヒトに介入（プラセボなどのコントロールを含む場合がある）を割り付けて行う前向き研究）で得られたデータ。（出典：National Institutes of Health (NIH) https://grants.nih.gov/policy/clinical-trials/definition.htm [2022-03-14]を一部改変） |
| Dataset | `compiled data` | `http://purl.org/coar/resource_type/FXF3-D3G7/` | 複数の情報源、たいてい少なくとも1つの点を共有した多様な情報源から収集・整理されたデータで、少なくとも1つの情報源は他の目的のために作成されたものである。集めたデータを統合することで、新しく統一的な情報が生みだされる。例えば、様々な入手可能な情報源（例えば会計書類、公的統計、大学の登録簿）を使って過去150年間の大学に関するデータを提供すること、調査データと公的統計から得られる地域情報の連結（例えば、人口密度、千人あたり医師の数等）、あるいは、RSSを利用してブログの投稿やツイートを集めること等があげられる。（出典：人文学・社会科学総合データカタログ（JDCat）統制語彙「調査方法」https://www.jsps.go.jp/j-di/data/Collection_Method.xlsx [2022-03-14]を一部改変） |
| Dataset | `dataset` | `http://purl.org/coar/resource_type/c_ddb1` | 関連するファクトデータを集めたもの。数値形式で表現され、構造化されているものが多い。 |
| Dataset | `encoded data` | `http://purl.org/coar/resource_type/AM6W-6QAW/` | 本来他の目的のために作られた定性的データ(文字、映像、音声、静止画)を定量的データ(変数単位のマトリックスで表現)に、あらかじめ定義済の分類基準に従ってコーディング手法で変換したもの。例えば、"European Parliament Election Study 2009, Manifesto Study" (doi:10.4232/1.10204)のような、分類（コーディング）された政党マニフェストデータがそれに当たる。（出典：人文学・社会科学総合データカタログ（JDCat）統制語彙「調査方法」https://www.jsps.go.jp/j-di/data/Collection_Method.xlsx [2022-03-14] を一部改変） |
| Dataset | `experimental data` | `http://purl.org/coar/resource_type/63NG-B465/` | 仮説に含まれる一部あるいは全部の独立変数を操作して行う実験的研究方法で得られたデータ。（出典：人文学・社会科学総合データカタログ（JDCat）統制語彙「調査方法」https://www.jsps.go.jp/j-di/data/Collection_Method.xlsx [2022-03-14] を一部改変） |
| Dataset | `genomic data` | `http://purl.org/coar/resource_type/A8F1-NPV9/` | ゲノムやDNA由来のデータ。生物情報学で生物のゲノムの収集・保存・加工する際に使用されるもの。ゲノムシーケンスから得られたデータに限らず、マイクロアレイやリアルタイムPCR、ゲノム薬理学の研究の過程で得られたデータも含む。（出典：techopedia https://www.techopedia.com/definition/31247/genomic-data [2022-03-14]を一部改変） |
| Dataset | `geospatial data` | `http://purl.org/coar/resource_type/2H0M-X761/` | 地表上の特定の地点または範囲に関連付いた様々な種類のデータ。物体や離散的な領域、連続的な面を表現する。（出典：DDI Alliance https://ddialliance.org/Specification/DDI-CV/GeneralDataFormat_2.0.html [2022-03-14]を一部改変） |
| Dataset | `laboratory notebook` | `http://purl.org/coar/resource_type/H41Y-FW7B/` | 研究の過程において仮説、実験および実験結果の初期段階の解析または解釈を文書化した研究ノート。紙媒体か電磁媒体かは問わない。（出典：Wikipedia https://en.wikipedia.org/wiki/Lab_notebook [2022-03-14]を一部改変） |
| Dataset | `measurement and test data` | `http://purl.org/coar/resource_type/DD58-GFSX/` | 事前に定められた基準や専用の測定方法や技術を適用することで、対象となる存在、物事、現象（あるいはプロセス）の特性（あるいは特徴）を評価することにより得られたデータ。（出典：人文学・社会科学総合データカタログ（JDCat）統制語彙「調査方法」https://www.jsps.go.jp/j-di/data/Collection_Method.xlsx [2022-03-14] を一部改変） |
| Dataset | `observational data` | `http://purl.org/coar/resource_type/FF4C-28RK/` | 独立変数を操作することなく、事象が発生したらそのまま観察結果を収集する観察研究によって得られるデータ（例えば、行動、イベント、状況や病気の進行の観察等）（出典：人文学・社会科学総合データカタログ（JDCat）統制語彙「調査方法」https://www.jsps.go.jp/j-di/data/Collection_Method.xlsx [2022-03-14] を一部改変） |
| Dataset | `recorded data` | `http://purl.org/coar/resource_type/CQMR-7K63/` | 情報を検索、複製できる形式で機械的あるいは電子的手段により記録されたデータ。例えば、画像や音のディスクや磁気テープへの記録。（出典：人文学・社会科学総合データカタログ（JDCat）統制語彙「調査方法」https://www.jsps.go.jp/j-di/data/Collection_Method.xlsx [2022-03-14] を一部改変） |
| Dataset | `simulation data` | `http://purl.org/coar/resource_type/W2XT-7017/` | 主にコンピュータプログラムを使い、現実世界のプロセス、イベント、システムのモデルを構築する、あるいは模倣することで得られたデータ。例えば、間接税の税率変更に伴い家計の消費がどう変わるのかをモデル化するプログラムや、仮想の患者と彼らの薬物服用、背景条件、既知の有害作用に関するデータセット等があげられる。（出典：人文学・社会科学総合データカタログ（JDCat）統制語彙「調査方法」https://www.jsps.go.jp/j-di/data/Collection_Method.xlsx [2022-03-14] を一部改変） |
| Dataset | `survey data` | `http://purl.org/coar/resource_type/NHD0-W6SY/` | 調査によって得られたデータ。ここでいう調査とは、一定の人々の中からサンプルのデータを収集して、統計手法を系統的に用いて推測することによって、その人々の特徴を調査するものと定義される。国勢調査、標本調査、行政記録及び派生した統計的作業からのデータ収集、アンケート調査が含まれる。（出典：OECD Glossary of Statistical Terms "SURVEY" https://stats.oecd.org/glossary/detail.asp?ID=2620[2022-03-14]を一部改変） |
| Image | `image` | `http://purl.org/coar/resource_type/c_c513` | 画像や映像を含む、文字以外で視覚的に表現されたもの。 |
| Image | `still image` | `http://purl.org/coar/resource_type/c_ecc8` | 静的に記録された画像で、ダイアグラム、図面、グラフ、グラフィックデザイン、図面、地図、写真、印画を含む。 |
| Image | `moving image` | `http://purl.org/coar/resource_type/c_8a7e` | コンピュータプログラムによって動的に生成されたり、事前に記録された静止画像の連続表示によって表現された動的な映像。アニメーション、映画フィルム、ビデオ、コンピュータシミュレーションを含み、動画の表現として映像と一体となったサウンドトラックを含む場合もある。 |
| Image | `video` | `http://purl.org/coar/resource_type/c_12ce` | テレビまたは電子機器を介して再生されるように設計されている、何らかの動きと音楽を伴う視覚的な画像の記録資料。 |
| Lecture | `lecture` | `http://purl.org/coar/resource_type/c_8544` | 就任記念講演などの学術的なイベントにおいて用いられた講演資料およびプレゼンテーション資料。会議で用いられた講演資料は含まない。 |
| Patent | `design patent` | `http://purl.org/coar/resource_type/C53B-JCY5/` | 新規かつ自明でない工業製品の装飾的なデザインを発明した人に与えられる特許。意匠特許は商品の外観のみを保護し、その構造的・機能的特徴を保護するものではない。（出典：Design Patent Application Guide https://www.uspto.gov/patents/basics/types-patent-applications/design-patent-application-guide#def [2022-03-14]を一部改変） |
| Patent | `patent` | `http://purl.org/coar/resource_type/c_15cd` | 特許または特許出願書類。 |
| Patent | `PCT application` | `http://purl.org/coar/resource_type/SB3Y-W4EH/` | PCT国際出願制度で申請された特許および出願願書。PCT国際出願制度は世界知的所有権機関（WIPO）が管理する特許協力条約（PCT）を通じて行われる特許出願で、国際出願とも呼ばれる。（出典：World Intellectual Property Organization(WIPO) https://www.wipo.int/edocs/pubdocs/en/wipo_pub_943_2018.pdf [2022-03-14]を一部改変） |
| Patent | `plant patent` | `http://purl.org/coar/resource_type/Z907-YMBB/` | 変種、突然変異体、雑種、新発見された苗を含む新品種の植物（塊茎繁殖植物や未栽培状態で発見された植物を除く）を発明または発見して無性生殖に成功した人に与えられる特許。（出典：General Information About 35 U.S.C. 161 Plant Patents https://www.uspto.gov/patents/basics/types-patent-applications/general-information-about-35-usc-161#heading-1 [2022-03-14]を一部改変） |
| Patent | `plant variety protection` | `http://purl.org/coar/resource_type/GPQ7-G5VE/` | 育成者権（PBR）とは、新しい植物品種の育成者に与えられる知的財産権の一つである。この権利により、保護された品種の利用に関する一定の行為は、育成者の事前の承認が必要となる。育成者権は、新しい植物品種を保護するために作られた独立した独自の保護形態であり、他の知的財産権と共通するいくつかの特徴を持つ。（出典：WIPO IP Facts and Figures 2018 https://www.wipo.int/edocs/pubdocs/en/wipo_pub_943_2018.pdf [2022-03-14]を一部改変） |
| Patent | `software patent` | `http://purl.org/coar/resource_type/MW8G-3CR8/` | ソフトウェア発明の対象とならない抽象概念や数学理論等に該当せず、実質的な特許基準（例：新規性、進歩性、産業上の利用可能性）を満たすソフトウェアを保護対象とする特許またはその特許出願書類。（出典：World Intellectual Property Organization(WIPO) https://www.wipo.int/patents/en/faq_patents.html [2022-03-14]を一部改変） |
| Patent | `trademark` | `http://purl.org/coar/resource_type/H6QP-SC1X/` | 商標（ある企業の商品またはサービスを他の企業のものと区別することができる標識）に関連するデータ（文字、ロゴ、図、画像、音、動画などの組み合わせ）（出典：World Intellectual Property Organization(WIPO) https://www.wipo.int/trademarks/en [2022-03-14]を一部改変） |
| Patent | `utility model` | `http://purl.org/coar/resource_type/9DKX-KSAF/` | 実用新案(保護期間が短い、特許性の要件が緩いといった通常の特許権とは異なる性質を持つ特許）または実用新案登録願書類。（出典：World Intellectual Property Organization(WIPO) https://www.wipo.int/edocs/pubdocs/en/wipo_pub_943_2018.pdf [2022-03-14]を一部改変） |
| Report | `report` | `http://purl.org/coar/resource_type/c_93fc` | 研究成果、進行中の研究内容、その他の技術的知見を個別に公表したもの。通常は報告書番号が付与され、報告書によっては助成機関によって割り当てられた助成番号が付与されるものもある。通常は何らかの上位機関に自主的あるいは強制的に保管・提出される、公開・非公開の委員会または法人組織の公式な活動記録、政府機関の会議録、調査報告を含む。より一般的には、特定の出来事に関連する事実や情報を正式に記録したものであり、定期的に提供される場合もある。 |
| Report | `research report` | `http://purl.org/coar/resource_type/c_18ws` | 特定のトピックに関する詳細な研究や、ある研究プロジェクトでの結果が記述された報告書。 |
| Report | `technical report` | `http://purl.org/coar/resource_type/c_18gh` | 技術的・科学的研究および研究課題のプロセス、進捗状況や結果を記述した文書。研究勧告や研究結果が含まれる場合もある。 |
| Report | `policy report` | `http://purl.org/coar/resource_type/c_186u` | 主要なポリシーの策定やイベントの詳細が記載された報告書。 |
| Report | `working paper` | `http://purl.org/coar/resource_type/c_8042` | 編集上の改善提案や情報提供を受けるため、少人数のグループで私的に閲覧される未発表の論文。 |
| Report | `data management plan` | `http://purl.org/coar/resource_type/c_ab20` | 研究プロジェクトの期間中および終了後におけるデータの収集・管理方法および場所の概要を示した正式な文書。 |
| Sound | `sound` | `http://purl.org/coar/resource_type/c_18cc` | 音楽再生ファイルフォーマット、オーディオコンパクトディスク、録音されたスピーチや音楽などの聴覚的な資料。 |
| Thesis | `thesis` | `http://purl.org/coar/resource_type/c_46ec` | 研究と知見を表現することにより、学位または専門資格の候補者であることを示すために提出された文書。 |
| Thesis | `bachelor thesis` | `http://purl.org/coar/resource_type/c_7a1f` | 学士号の取得につながる学部・学科教育の一環として実施された、研究プロジェクトを報告する論文。 |
| Thesis | `master thesis` | `http://purl.org/coar/resource_type/c_bdcc` | 修士号の取得につながる大学院教育の一環として実施された、研究プロジェクトを報告する論文。 |
| Thesis | `doctoral thesis` | `http://purl.org/coar/resource_type/c_db06` | 博士課程期間中に行われた研究を報告する論文。 |
| Multiple | `commentary` | `http://purl.org/coar/resource_type/D97F-VB57/` | 既存の出版物に注目を集めるために執筆される深い分析。執筆者が作品の分析を行い、なぜその作品が特定の読者の興味を引くのかを示すという点で「レビュー」に似ている（出典：Perspective, Opinion, and Commentary Pieces https：//www.enago.com/academy/perspective-opinion [2022-03-14]を一部改変） |
| Multiple | `design` | `http://purl.org/coar/resource_type/542X-3S04/` | 特定の対象（建造物、工業製品など）についての作り方や仕組み、完成図を示す設計書や図面一式。（出典：Cambridge Dictionary https://dictionary.cambridge.org/dictionary/english/design [2022-03-14]を一部改変） |
| Multiple | `industrial design` | `http://purl.org/coar/resource_type/JBNF-DYAD/` | 工業デザインは、広く様々な工業製品や工芸品に適用される。有用な品物の装飾的・美的な側面であり、線や色の構成や、製品や工芸品に特別な外観をもたらす三次元的形状を含む。（出典：WIPO IP Facts and Figures 2018. p49. https://www.wipo.int/edocs/pubdocs/en/wipo_pub_943_2018.pdf [2022-03-14]） |
| Multiple | `interactive resource` | `http://purl.org/coar/resource_type/c_e9a0` | ユーザの理解、実行、経験を促すために、ユーザーとの相互作用を必要とするリソース。Webページ、アプリケーション、マルチメディア学習資料、チャットサービス、バーチャルリアリティ環境など。 |
| Multiple | `layout design` | `http://purl.org/coar/resource_type/BW7T-YM2G/` | レイアウト設計（トポグラフィ）は、集積回路の素子（うち少なくとも1つは能動素子）や、集積回路の配線の一部または全部の、表現方法を問わない三次元配列や、製造業向け集積回路のために準備される三次元配列である。（出典：WIPO. Layout-Design (Topography) of Integrated Circuits Ordinance (Chapter 445). https://wipolex.wipo.int/en/text/182020 [2022-03-14]） |
| Multiple | `learning object` | `http://purl.org/coar/resource_type/c_e059` | 授業等で用いられる資料。 |
| Multiple | `manuscript` | `http://purl.org/coar/resource_type/c_0040` | 全体が手書きされた様々な種類の著作物（テキスト、題辞、楽譜、地図など）。 |
| Multiple | `musical notation` | `http://purl.org/coar/resource_type/c_18cw` | 伝統的または現代の演奏記号によって記述され、聴覚的に認識される音楽を視覚的に表現したもの。 |
| Multiple | `peer review` | `http://purl.org/coar/resource_type/H9BQ-739P/` | 同分野の他の研究者による科学的、学術的もしくは専門的な成果物への評価。（出典：DataCite Metadata Schema Documentation for the Publication and Citation of Research Data and Other Research Outputs https://schema.datacite.org/meta/kernel-4.4/doc/DataCite-MetadataKernel_v4.4.pdf [2022-03-14]を一部改変） |
| Multiple | `research proposal` | `http://purl.org/coar/resource_type/c_baaf` | 助成金の申請に用いる文書。データ管理計画書も含む。 |
| Multiple | `research protocol` | `http://purl.org/coar/resource_type/YZ1N-ZFT9/` | プロジェクトの概要、根拠に基づくプロジェクトの説明、目的、方法論、データ管理および分析、倫理的配慮、ジェンダー問題、参考文献を示した研究調査の詳細な計画書。（出典：WHO https://www.who.int/publications/i/item/a-practical-guide-for-health-researchers [2022-03-14]を一部改変） |
| Multiple | `software` | `http://purl.org/coar/resource_type/c_5ce6` | ソースコード（テキスト）またはコンパイルされた形式のコンピュータプログラム。 |
| Multiple | `source code` | `http://purl.org/coar/resource_type/QH80-2R4E/` | 人間が読める形式のプログラミング言語で書かれたコード（通常、プレーンテキスト形式）。（出典：Wikipedia https://en.wikipedia.org/wiki/Source_code [2022-03-14]を一部改変） |
| Multiple | `technical documentation` | `http://purl.org/coar/resource_type/c_71bd` | 開発中または使用中の工業製品について、取扱いや機能および構造を記述した文書全般。 |
| Multiple | `transcription` | `http://purl.org/coar/resource_type/6NC7-GK9S/` | 公判、スピーチ、インタビュー、放送、録音から書き起こした記録。（出典：Online Dictionary for Library and Information Science https://products.abc-clio.com/ODLIS/odlis_t.aspx [2022-03-14]を一部改変） |
| Multiple | `workflow` | `http://purl.org/coar/resource_type/c_393c` | 特定のジョブを実行する際に自動または確実に実行される一連の手順を記録したもの。複数の生物情報科学のデータベースから情報を抽出して処理するin silico調査など。 |
| Multiple | `other` | `http://purl.org/coar/resource_type/c_1843` | 上記で明示的に取り上げられていない、その他全ての概念をカバーするもの。紀要等の表紙や目次を含む。 |

> 公式別表【Ver2.0】には74語が掲載されています。
> 2026年7月16日に取得したHTMLを対象に、各語彙に一つずつある `rdf:resource` の項目を計数しました。
> 別表には、COAR Resource Types Vocabulary自体の版番号は明示されていません。

### 非推奨

`rdf:resource` を省略した次の記述は、使用できません。

```xml
<dc:type>departmental bulletin paper</dc:type>
```

### 入力例

```xml
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_6501">journal article</dc:type>
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_6501">departmental bulletin paper</dc:type>
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_db06">doctoral thesis</dc:type>
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_ddb1">dataset</dc:type>
<dc:type rdf:resource="http://purl.org/coar/resource_type/c_6501">article</dc:type>
```

### マッピング

| 要素 | junii2 |
|------|--------|
| `dc:type` | NIItype（NII資源タイプ） |

> 出典：上記のJPCOARスキーマ 2.0 公式説明ページ（#15）および資源タイプ語彙別表【Ver2.0】
