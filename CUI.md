# **GitHubでコード管理 ~入門~**
## **新しいRepositoryを作る(CUI編)**

1. terminalでとりあえず `git --version` を打ち込んで入ってるか確認
2. エラーがでたら言ってください
3. GitHubの自分のページ([例](https://github.com/fmsuvM?tab=repositories))で, New Repositoryをクリックする
4. こんな感じの画面になる

  ![First Image](https://gyazo.com/579b371b8f6021b72a15f0240de63aec.jpg)

5. Repository NameとDescriptionを入力

  ![SecondImage](https://gyazo.com/dfb95f0d3fdcd1dffd168182ccdd3ad6.jpg)

6. こんな感じの画面が出る

  ![ThirdImage](https://gyazo.com/4f32aed5aac2b1171a5b8343270889c5.jpg)

7. 2種類のコマンドがあるが, どちらでも構わないのでコピペする.

  - 上のコマンドは現在のディレクトリで実行するだけでREADME.md(説明書のようなもの)も一緒に作ってくれる.
  - 下のコマンドは自分で現在のディレクトリでまず `git init` しなければならない. その後に別途自分でREADME.mdも作成する必要がある.

8. これで自分の書いたコードがGitHub上に初めてuploadされる.

## 概要

1. コードの変更やファイルの追加をしたら, とりあえず `git add .` を打つ
2. 何を変更したか, 追加したかを明記するために `git commit -m "initial commit"` を打つ. initial commitと記述されている部分に自分のコメントを打つ.
3. add -> commitをすると, コードやファイルの変更が適用されて保存される.
4. これを, リモートのリポジトリ, つまりGitHubにあげることができるようになる.
5. GitHubにコードを送る時は, `git push origin master` と打つと, リモートのリポジトリも変更が適用される.

### 例

6. 最初

  ```javascript
  var app = require('app');
  var BrowserWindow = require('BrowserWindow');

  var mainWindow = null;
  ```

7. 変更後(少し変わった)

  ```javascript
  let electron = require('electron')
  let app = electron.app
  let BrowserWindow = electron.BrowserWindow

  let mainWindow = null
  ```

8. `git status` を打って確認すると, 更新されてない

  ```sh
  $ git status
  On branch master
  Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
  Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout --<file>..." to discord changes in working directory)
      modified: index.js
  no changes added to commit (use "git add" and/or "git commit -a")
  ```

9. `git add .` と `git commit -m "message"` を使って更新する

  ```sh
  $ git add .
  $ git commit -m "change import method"
  [master e938284] change import method
  1 file changed, 1 deletion(-)
  $ git status
  On branch master
  Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)
  nothing to commit, working directory clean
  ```

10. `git log` で今までのcommit messageや日時を確認可能  
  ![log](https://gyazo.com/732079fba6a266e2db4ffb844b3f022d.jpg)
