# THE@TER CHALLENGE!! 得票数ログ

シアターデイズにて開催されていたユニット選抜投票「THE@TER CHALLENGE!!」の非公式な得票数のログです。

このデータは [matsurihi.me](https://twitter.com/matsurihi_me) が収集した非公式なデータであり、データの完全性・信頼性は保証いたしかねます。

データの性質上詳細なライセンスは定めませんが、二次利用の際には matsurihi.me が収集したデータであることを明記してください。

THE@TER BOOST! のデータは TheaterGate の git リポジトリを参照してください（[theaterdays-diary/theater-boost](https://github.com/theaterdays-diary/theater-boost)）。

## ダウンロード

[このリポジトリのリリースページ](https://github.com/matsurihi-me/theater-challenge/releases)からダウンロードできます。

## データ収集期間

ログは 2018/12/19 00:05 から 2019/01/19 23:59 まで存在します。2019/01/19 23:55 までは 5 分ごと、それ以降は 1 分ごとに存在します。

ただし、以下の期間はシステム障害のためデータが存在しません。

- 2018/12/27 16:45
- 2019/01/09 11:20 – 14:35

利便性のため集計時刻はすべて 00 秒になっていますが、実際にデータを取得した時刻はその時刻よりわずかに遅れている場合があります。

なお、Twitter や Web で公開している終了数秒前のデータは、このデータには含まれていません。

## ファイルの説明

すべて json ファイルで、エンコードは UTF-8 です。

時刻はすべて ISO 8601 の拡張形式（YYYY-mm-ddTHH:MM:SS+09:00）で示しています。

### meta.min.json / meta.json

TC のメタデータです。

meta.json は整形したもので、内容は同じです。

### data.min.json

ログの全データです。巨大なファイルのため、取り扱いには注意してください。

データは次のような構造になっています。ranking オブジェクトは順位でソートされています。

- `Object[]`
    - `int role_id`: 役の ID
    - `Object[] logs`
        - `DateTime date`: 集計日時
        - `Object[] ranking`
            - `int idol_id`: アイドルの ID
            - `int votes`: 得票数

### data.30m.min.json

data.min.json のうち、毎時 0 分と 30 分のデータのみを抽出したものです。

データの構造は同じです。

### data_splitted/{role_id}/{date_id}.json

役・集計日時ごとに分割したデータです。

巨大な JSON ファイルが扱いにくい場合にご利用ください。  
毎時 0 分と 30 分のデータのみ抽出しています。

データは次のような構造になっています。

- `Object[]`
    - `int role_id`: 役の ID（ディレクトリ名）
    - `string role_name`: 役名
    - `int date_id`: 集計日時の ID（ファイル名）
    - `DateTime date`: 集計日時
    - `Object[] ranking`
        - `int rank`: 順位
        - `int idol_id`: アイドルの ID
        - `string idol_name`: アイドル名
        - `int votes`: 得票数
