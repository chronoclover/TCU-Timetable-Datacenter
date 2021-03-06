# 概要
[東京都市大学のシラバス](https://websrv.tcu.ac.jp/tcu_web_v3/slbsskgr.do)(現在は横浜キャンパス限定)をjsonデータとしてまとめたものです。  

**API化やシステムに取り組む等自由に使用していただいて問題ないです。**  

## 要望・不具合について

jsonのデータ形式についてやシステム自体について改善・不具合等の要望があればissueにて受け付けます。お気軽にどうぞ

## システムの改変とプルリクについて

システム自体の改変は自由です。また他の人にも役に立ちそうな追加機能ができた場合にはプルリクしていただけると嬉しいです。


# jsonについて

jsonファイルの場所：`/data/LectureList.json`  

LectureList.jsonの形式は各講義情報のjsonを配列にしたものです。


## json format

- string `code` 講義コード
- string `name` 授業名
- string `targetyear` 対象学生の入学年度
- string `targetdepart`   対象学生の学科  
- Array[Object] `time` 開講時期  
  - string `period` 開講期間  
  - string `dow` 開講曜日  
  - string `thclass` 開講時限  
- Array[string] `instructor`  担当講師  

### example1
>
>[講義情報]
>yaa612201	環境モニタリング技術	2018年度環境創生学科入学生　他	 前期前半　火曜日　２時限　前期前半　火曜日　３時限 	史　中超
>
>[json形式]
>{
    "code": "yaa612201",
    "name": "環境モニタリング技術",
    "targetyear": "2018",
    "targetdepart": "環境創生",
    "time": [
      {
        "period": "前期前半",
        "dow": "火",
        "thclass": "2"
      },
      {
        "period": "前期前半",
        "dow": "火",
        "thclass": "3"
      }
    ],
    "instructor": [
      "史　中超"
    ]
  }  

### example2
>
>[講義情報]
>yzz617001	事例研究	2018年度環境創生学科入学生	通年（事例）　その他	飯島　健太郎
>
>[json形式]
>{
    "code": "yzz617001",
    "name": "事例研究",
    "targetyear": "2018",
    "targetdepart": "環境創生",
    "time": [
      {
        "period": "通年（事例）",
        "dow": "",
        "thclass": ""
      }
    ],
    "instructor": [
      "飯島　健太郎"
    ]
  }


# その他

- **講義情報からシラバスを逆引きしたい場合**
各講義情報のjsonからシラバスを逆引きすることが可能です。  
以下のURLの様式どおりにアクセスするとシラバスの逆引きをすることができます。  

`https://websrv.tcu.ac.jp/tcu_web_v3/slbsskgr.do?value(risyunen)=2020&value(semekikn)=1&value(kougicd)=[逆引きしたい講義のコード]`

example.  
[調べたい講義]  
yaa612201	環境モニタリング技術	2018年度環境創生学科入学生　他	前期前半　火曜日　２時限　前期前半　火曜日　３時限	史　中超  
[逆引きURL]  
`https://websrv.tcu.ac.jp/tcu_web_v3/slbssbdr.do?value(risyunen)=2020&value(semekikn)=1&value(kougicd)=yaa612201` 
