# ターミナルでgitを使うときのvimの簡単な使い方

### 背景
リモート環境は制約がきつく、vimもよく使います。ただ、vimはデフォルト設定なので使いにくいのが難です。

### gitでvimが走るとき
* gitの設定でエディタがviやvimになってるとき。
(nanoになってればnanoも使いやすいです。)

* git commit/ git rebase -i 等で -mオプションをつけないときはエディタが走ります。
commit画面とrebaseの最初はファイルを破棄すればgitは何もしません。

---
### vimの使い方

#### 起動と終了(変更破棄)

* gitからは自動で起動します。

* コマンドラインからは vim で起動します。

* esc :q! で変更破棄で終了します。ときに複数バッファを使ってるときはこれを複数回行えば同じく終了できます。

#### escキー

* escキーはCTRL-C(C-c)で代用可能です。esc :q! は C-c :q! と同じです。

* カスタマイズした際は変わる可能性があります。ローカルでvimを使ってカスタマイズした場合は注意してください。

#### ファイル操作(esc : から入ります。)

|key   |アクション    |
|:-----|------------|
|w     |保存　　　　　|
|wq!   |保存して終了|
|e!    |ファイルの再読込|

#### モード(単純にまとめてます。選択モードはノーマルモードに含めます)

* 他のエディタと違い、モードの概念があります。

* 最初はノーマルモード、編集するときはインサートモード、esc : で入る画面一番下はコマンドモードになります。

* ノーマルモードが基本で、他のモードに入って何かをしてノーマルモードに戻って最後にコマンドモードで保存したり終了したりします。

* ノーマルモードは移動、選択、インサートモードを使わない文字列削除等に使います。

|key   |アクション    |
|:-----|------------|
|矢印     |移動　　　　　|
|i |インサートモード|
|A |インサートモード(行ラストから追加)|
|v |これで移動すれば文字単位で選択|
|vから選択してd/y|選択した文字を削除/コピー|
|V |これで上下移動すれば行単位で選択|
|Vから選択してd/y|選択した行を削除/コピー|
|dd|今いる行を削除|
|yy|今いる行をコピー|
|x|一文字削除|
|p|ペーストします|
|gg|先頭行に移動|
|G|最後に移動|
|esc or C-c|コマンドモード|

** dで削除したものはペーストできます。カットアンドペーストの感じです。

** キーの組み合わせで組み合わさったアクションができます。

|key   |アクション    |
|:-----|------------|
|ggVG|ファイル全体を選択|
|dd移動p|一行カットして移動後にペースト|
|14G|14行目に移動|