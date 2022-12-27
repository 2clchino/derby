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
三連単や単勝の予想への活用は想定していませんのでご注意ください

訓練データとして下記パラメータを入力しています。
- frame_number 	        枠番
- aptitude_course 	    コース適性
- aptitude_distance     距離適性
- aptitude_run 	        脚質適性
- aptitude_growth 	    成長適性
- aptitude_ground 	    馬場適性
- weight 	            斤量
- race_count 	        レース数
- jockey_rate 	        ジョッキーのその年の複勝率
- past_rank_ave 	    過去レースの順位平均
- before_race_rank 	    前走着順
- past_rank_std 	    過去レースの順位標準偏差
- med_race_score        後述の基準で定められたレーススコア * (4 - 順位) * 10) / 頭数 の中央値 (独断によって定めたため諸説)

レーススコアは下記のように算出しています
- 100, "G1"
- 70, "G2"
- 50, "G3"
- 40, "L", "OP"
- 30, "3勝", "1600万下"
- 20, "2勝", "1000万下"
- 10, "1勝", "500万下"
- 5, "未勝利", "新馬"

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
│   ├── race
│   │   ├── 2021レース名.csv
│   │   ├── 2021レース名_spread.csv
│   │   └── レース名
│   │       ├── 2000.csv
|   │       |     :
│   │       └── 2020.csv
│   └── jockey
│       ├── jockey_id_1.csv
│       └── jockey_id_2.csv
├── derby_func.py
├── 競馬予想用.xlsm
├── 競馬予想用.xlsx
└── 競馬予想用_ロック.xlsx
```

## Requirement
* Python 3.8
    * requests
    * bs4
    * re
    * os
    * time
    * numpy
    * pandas
    * matplotlib
    * seaborn
    * Enum
    * collections
    * sklearn

## Usage
- Anaconda Navigater で、Requirement に記載したモジュールを導入済みの仮想環境を用意します。
- Jupyter Notebook で、20Race_Scraping.ipynb を開き、スクレイピングを行います。
- 20Race_Learn.ipynb で、学習および予想が行えます。

## Note
20Race_Scrapingでは一回の実行で**過去20年分のレース×出走馬約18頭=400回近いアクセス**を行います.<br>
そのため相手方のサーバーに負担がかかるのを避けるため意図的に遅延を入れていますが、頻繁に実行するのはお勧めできません.

## Author
<p>CL2_CHINO</p>
