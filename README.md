# ProcurementOrderCheck 下請法チェックエージェント
調達時に発注先の会社が自社から見て下請法対象かどうかをチェックしてくれるエージェントです。

以下のように、企業名から資本金を調べ、取引内容から自動的に下請法の対象の企業かどうかを判定してくれます。

![image](https://github.com/user-attachments/assets/37cf0788-82d0-4b8f-89b9-fe0ec03bb9d6)

## 自律型エージェントでの動作

https://github.com/user-attachments/assets/ecd013c2-3f23-49d8-8718-3cbd12f1b8c2

## Copilot Chat での動作

https://github.com/user-attachments/assets/78ca9550-21a5-4ae2-b359-d5b1e6ebb85b

## 前提条件
以下のライセンスが必要です。

* Power Apps Premium 
* Copilot Studio

## インポート方法
[最新のソリューション](https://github.com/geekfujiwara/ProcurementOrderCheck/releases/tag/ProcurementOrderCheck)をダウンロードします。

[Power Apps ポータル](https://make.powerapps.com/)にアクセスします。

ファイルをアップロードしてインポートします。

![image](https://github.com/user-attachments/assets/82853c31-0788-427b-81f4-55d9e4f3f9db)

接続が作成されるまで待ち、完了したらインポートします。

![image](https://github.com/user-attachments/assets/829095b4-bcb8-4bc1-9599-40de534e46d1)

>[!Note]
>もしこのような警告が表示されても大丈夫です。これはCopilot Studio のライセンスが不足しているという警告であり、インポート自体に問題があるわけではありません。 Copilot Studio のトライアルを行うこともできますのでこのまま進めます。
>
>![image](https://github.com/user-attachments/assets/0768bc6d-13c4-4e23-8a2d-9351852353f5)

ソリューションにアクセスします。

![image](https://github.com/user-attachments/assets/30c4fce0-1208-44dc-ad4e-ba9abf8dca7d)

すべてのクラウドフローをオンにします。

すべてのカスタマイズを公開します。

![image](https://github.com/user-attachments/assets/0cb8ab19-4a75-4afd-841a-ff9e5c6df7f9)

さらに、エージェントに移り、エージェントの公開を行います。

![image](https://github.com/user-attachments/assets/5e8158b1-def1-4007-80c8-3a0aa3c701aa)

公開が完了したらトリガーされるようになります。

これでソリューションのインポートが完了しました。

## 利用方法

ソリューションには企業名と取引内容を入力する Power Apps モデル駆動型アプリと、その判定をするエージェントが含まれています。

![image](https://github.com/user-attachments/assets/706d3a1d-970f-4a17-a88a-c27e55d5ecb1)

まずはモデル駆動型アプリにて、企業名と取引内容を登録します。

![image](https://github.com/user-attachments/assets/ddbee379-ad0d-456c-9f96-a1c81b7d14de)

するとエージェントが自動的に起動して、下請法チェックを行い、その判定結果と理由を登録してくれます。

![image](https://github.com/user-attachments/assets/7b3da9d3-dd90-4582-b702-0e5ed4458f5b)

## 仕組み
### 指示
エージェントは以下の指示に基づいて動作します。

```
### タスク
- 下請法判断に必要な企業の資本金額を取得します。
- 資本金額と取引内容を元に、公的機関であるJFTCが説明する 下請法ガイドラインに基づき、下請法対象の取引かどうかを推論して判定します。
- 判定結果とその理由をガイドラインに基づき明確にし、その内容を登録します。

### 前提条件
- エージェントは、企業名とその資本金額をインターネットで検索し、その企業が下請法の対象かどうかを判断します。資本金の金額が検索結果から見つけられない場合、開示されていないほどの小規模な企業である可能性があるため、下請法対象として判断します。
- 自社は資本金が3億円以上の企業です。
- 下請法の対象かどうかの判断は、ファイルのナレッジの下請法判断ガイドラインに則って適切に判断します。
```

### ナレッジ

エージェントには以下のナレッジが追加されています。

![image](https://github.com/user-attachments/assets/fb32dd94-53e3-49b8-927e-d0b55e9dc797)

```
https://irbank.net/
https://www.buffett-code.com/
JFTC下請法ガイドライン.pdf
```

### アクション

![image](https://github.com/user-attachments/assets/6abe1e10-084a-4adf-b614-663efe926f76)


## カスタマイズ
### 自社に関する情報を変更する場合:

自社の資本金は指示に定義しています。この金額を調整することでエージェントの振る舞いが変更されます。

![image](https://github.com/user-attachments/assets/f1bc4f93-01f7-4abf-8bc7-2bbf1e65567d)


### ナレッジを変更する場合:

参照させたいナレッジがある場合自由に変更することができます。

以上

