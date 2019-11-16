# 2019-11（下期計画）

# 目標
* チームによる成果物（チェックインアプリ）の完成
* mbass（FireBase）の利用 
 - [Cloud Firestore(以下Firestore)はGoogleが提供しているNoSQLドキュメント指向データベース](https://qiita.com/keito_jp/items/3a9a14c9e0fb951152f7)

# チェックインアプリ概要
[Firebase導入](https://qiita.com/Nabe_LiT/items/660e97150fb87a2e7ffd)<br>
0. アカウント作成<br>
　Id : phai0512@gmail.com<br>
　Pass : phai1205<br>
1. プロジェクトの作成：Phai1205<br>
2. アプリ登録<br>
3. google-services.jsonのダウンロード＆ルートディレクトリに格納<br>
4. grade（ルート・アプリ）更新<br>
　[androidXとandroid.support.compatライブラリがコンフリクト](https://kurutabrog.hatenablog.com/entry/2019/05/04/133140)<br>
5. DB作成<br>
6. 実装<br>
　[参考]https://firebase.google.com/docs/android/setup<br><br><br>

## 処理（データ）の流れ
### チェックイン機能
　イベントデータ（JSON定義※）<br>
		↓<br>
　QRコード（Webサービス等）<br>
		↓<br>
　アプリ ：QRコードとしてイベントデータを取得<br>
		↓<br>
　Cloud Firestore<br>

### 履歴（蕎麦人数も同様）
　アプリ ：イベントデータを取得（クエリLikeに抽出キーを指定）<br>
		↑<br>
　Cloud Firestore<br>

また、イベントにおけるマスターデータがないため、
QRで受け取ったイベントデータ（および社員番号）をそのまま正として
Cloud Firestoreに登録しているのは課題

※QRで必要なJSON定義
↓これをQRコードにしてアプリ で読み込ませる<br>
{"event_id":1, "event_name":"WM&P部門会議", "event_month":201910}<br>
注1. 1イベントにつき、event_idがユニークに振られる<br>
注2. event_monthは当初定義するつもりがなかったが、蕎麦集計の抽出キーの関係上付けた<br>


## 課題
* 通常は各サービスから提供されるRESTAPIを叩いてドメインデータとのやりとりをするが、Firestoreを利用する性質上
　FirebseSDKとの連携によるデータのやりとりとなるため、特に表示系（RecycleViewを利用した一覧など）の処理が複雑化している
 
# Firebase・ Cloud Firestore の利用（データ確認）方法
　1. firebaseログイン(https://firebase.google.com)<br>
　アカウント<br>
　Id : phai0512@gmail.com<br>
　Pass : phai1205<br>

　2. コンソールに異動(メニュー右上にある「コンソールへ移動」ボタン)<br>
　3. Firebaseプロジェクトをクリック(Phai1205)<br>
　4. メニューペイン(開発)からDataBaseを選択<br>
　5. データベース種類を選択(Cloud Firestore)  ▶︎ 多分デフォルトでなっているハズ<br>
　※現状として、[Checkin]というコレクション(テーブルのようなもの)を１つ定義しています<br>
 
 # TODO
　1. 認証機能（ユーザ）<br>
　2. Firebaseプロジェクトの付け替え（Phai1205→Creva専用）<br>
　3. リファクタ<br>
　　3-1. UI見直し（履歴０件の時の表示、蕎麦人数確認ページの作成など）<br>
　　3-2. アーキテクチャの見直し（そもそもコード汚い、MVVM、、リポジトリパターン、DI、RxJavaの利用など）<br>
　4. QRコード拡散した場合の対策として、GPSを使った場所のチェック機能（イベントマスターにも緯度経度の登録が必要）<br>
　5. イベントマスター管理および、イベントデータのQRコード表示<br>
　　→別(管理用)アプリで作っても良いカモ・・・
