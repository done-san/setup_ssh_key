# GitHubアカウントにSSH接続で使用する公開鍵を登録する

## 本記事の対象者
- GitHubのSSHの設定についてピンポイントで知りたい人
- Windowsユーザー

## 本記事のゴール
- アカウントにローカルホストのSSH公開鍵を反映する

### 注意
- 本記事における環境は、Windows 10を前提とします。
- 本記事の内容は、2022年4月3日のものであるため、  GitHubおよびssh-keygenコマンドなどの細かな表記が  変わるおそれがあります。

## キャラクターの確認
- GitHub
- コマンドライン
- ssh-keygen コマンド
- id_rsa.pub
- エクスプローラ
- メモ帳

## 本記事の概要・おおまかな流れ
1. コマンドラインを起動する
2. 公開鍵・秘密鍵を発行する
3. GitHubに反映する
4. 戻し作業について

### 1. コマンドラインを起動する
1. Windows + R で「ファイル名を実行」を表示する
2. "cmd"と入力して、Enterキーを押下する
3. コマンドラインが起動されていることを確認する

### 2. 公開鍵・秘密鍵を発行する
1. "ssh-keygen"と入力して,Enterキーを押下する
2. Generating public/private rsa key pair.  Enter file in which to save the key (C:\Users\"ユーザ名"/.ssh/id_rsa):  と表示されるので、Enterキーを押下する  ※"ユーザ名"はWindowsでログインしているユーザの名前
3. Enter passphrase (empty for no passphrase):  と表示されるので、Enterキーを押下する
4. Enter same passphrase again:  と表示されるので、Enterキーを押下する
5. コマンドライン上に表示されている C:\Users\"ユーザ名"/.ssh/ という文字をCtrl + C でコピーする
6. エクスプローラを開いて、上記でコピーした文字をCtrl + V でペーストしてフォルダを開く  

### 3. GitHubに反映する
1. C:\Users\"ユーザ名"/.ssh/ 配下にある "id_rsa.pub"というファイルをメモ帳で開く
2. メモ帳に表示された文字を Ctrl + A で全選択する
3. 全選択した文字を Ctrl + C でコピーする
4. GitHubのアカウントにログインした状態(していなければ、すること)で  https://github.com/settings/keys へ移動する
5. New SSH Key ボタンを押下する
6. Title に識別しやすい名前で入力する(ex: "ホスト名")
7. Key に4.でコピーした文字をCtrl + Vで登録する
8. SSH keysに登録されている内容(名前、時間など)が正しいことを確認する

### 4. 戻し作業について
1. https://github.com/settings/keys へ移動する
2. 登録されている対象の公開鍵の Delete ボタンを押下する
3. I understand, please delete this SSH key ボタンを押下する
4. 削除対象の公開鍵が削除されていることを確認する
5. エクスプローラで C:\Users\"ユーザ名"/.ssh/id_rsa に移動する
6. 削除対象の鍵ペア(id_rsa および id_rsa.pub の2つのファイル)をDeleteで削除する
