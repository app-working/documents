# 2019年7月、8月
## やったこと１
### 電卓アプリの作成
Kotlinでの電卓アプリを作成。と言っても、以下のサイトからコピペして作っただけです。

https://daeudaeu.com/programming/kotlin/androidstudio/#Android_Studio-3


## やったこと２
### GPSのテスト
GPS機能をテスト的に実行するアプリの作成。これも以下のサイトからコピペして作りました。

https://akira-watson.com/android/fusedlocationproviderapi.html

以前は、LocationManagerで作成するのが定番だったのですが、ここの所、
新しいFusedLocationProviderClientで作成する方が推奨されていましたので、試してみました。

APIが23以上の場合、Android 6.0 Runtime Permissionに該当するため、実装がちょっと面倒になっております。
