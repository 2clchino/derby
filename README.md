DERBY
====

## Description
スクレイピングで[netkeiba](https://www.netkeiba.com/)からデータベースを取得して、機械学習で予測をする.
機械学習モジュールは
- Passive Aggressive Classifier
- Gradient Boosting Classifier
- Support vector machine(SVM)
- Random Forest Classifier
- K Nearest Neighbor Classifier

を使用.予測するのは「どの馬が1着になるか」ではなく「**その馬が馬券に絡むかどうか**」になります.

## OverView
```
.
├── 20Race_Learn.ipynb
├── 20Race_Scraping.ipynb
├── DB_to_CSV.ipynb
├── Derby_All.ipynb
├── csv
│   ├── horse
│   │   └── 2021レース名
│   │       ├── 馬名.csv
|   |       |     :
│   │       └── 馬名.csv
│   └── race
│       ├── 2021レース名.csv
│       ├── 2021レース名_spread.csv
│       └── レース名
│           ├── 2000.csv
|           |     :
│           └── 2020.csv
├── derby_func.py
├── 競馬予想用.xlsm
├── 競馬予想用.xlsx
└── 競馬予想用_ロック.xlsx
```
- 20Race_Learn.ipynb
    - 学習に使用するソース
- 20Race_Scraping.ipynb
    - スクレイピングに使用するソース
- DB_to_CSV.ipynb
    - スプレッドシート用に変換するソース
- Derby_All.ipynb
    - スクレイピング + 学習（基本はこれを動かす）
- csv/
    - 馬のデータやレースデータの保管場所
- derby_func.py
    - 汎用ソース

## Requirement
* Python 3.8

## Usage
- クローンしてJupyter Notebookで開くだけ.
- スクレイピングしてからじゃないと、もちろん学習側のソースは動きません.

## Note
20Race_Scrapingでは一回の実行で**過去20年分のレース×出走馬約18頭=400回近いアクセス**を行います.<br>
そのため相手方のサーバーに負担がかかるのを避けるため意図的に遅延を入れていますが、頻繁に実行するのはお勧めできません.

## Author
<p>CL2_CHINO</p>
