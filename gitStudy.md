# Githubのpageの見方や機能の説明を付け足す責務

# ***NCC Github講習会***

---

## **Github is 何**
簡単に言うと, 自分のcodeをversionごとに保存してくれるファイル(うまい説明よろ)
他の人のRepository(上でいうファイル)に色々な
詳しくは [ここ](https://ja.wikipedia.org/wiki/GitHub)に書いてあります
後で色々付け加える.

---

## **他のGit Hosting Serviceと何が違うねん**
### **Github**
 -  Free Accountで無限に **Public Repository** を作れる. **Private Repository** を作るには別のPlanにする必要がある.
 - HTTPS, SSH
 - Wiki, Gist
 - pull request
 - 自分のweb pageを公開できる(ドメインを用意してくれる)
 - member人数制限なし   

### **BitBucket**
 - 大体Githubと同じ.
 - Free PlanでPublicとPrivateの **両方の** Repositoryが無制限に作れる.  
 - memberはFree Planだと5人まで
 - Gistはない  

### **GitLab**
 - 大体Githubと同じ.
 -  Public, Privateの **両方の** Repositoryを無制限に作れる.  
 - Member 無制限
 - Wikiなし  


---

## **Githubの始め方**  

 1. [ここ](https://github.com/)にいってmail addressとpasswordを登録  

 1. GUIかCUIで操作  
  - GUIの場合, [SourceTree](https://www.sourcetreeapp.com/) か [Github for Desktop](https://desktop.github.com/) をinstall
  - MAC Userは[Homebrew](http://brew.sh/index_ja.html)入ってれば `brew install git` でterminal用のgitがinstallできる  
  - windows userは[ここ](https://git-for-windows.github.io/)からそれぞれのオペレーションシステムに合ったgit.exeをinstall(執筆当時ver2.8.2)   

---

## **Github入門**  
### CUI(terminalやcommand prompt)の場合(以下terminalで統一)   
 2. terminalでとりあえず `git --version` を打ち込んで入ってるか確認  
  - errorでたら教えてください  

 2. Githubの自分のPage([例](https://github.com/fmsuvM?tab=repositories))で, New RepositoryをClickします  
 2. こんな感じの画面になります  

 ![First Image](https://gyazo.com/579b371b8f6021b72a15f0240de63aec.jpg)  

 2. Repository NameとDescriptionを入力します  

  ![SecondImage](https://gyazo.com/dfb95f0d3fdcd1dffd168182ccdd3ad6.jpg)  

 2. こんな感じの画面が出ます  

  ![ThirdImage](https://gyazo.com/4f32aed5aac2b1171a5b8343270889c5.jpg)  

 2. 2種類のcommandがありますが, どちらでも構わないのでコピペします.   
  - 上のcommandはcurrent directoryで実行するだけでREADME.md(説明書のようなもの)も一緒に作ってくれます.
  - 下のcommandは自分でcurrent directoryでまず `git init` しなければなりません. その後に別途自分でREADME.mdも作成する必要があります.  
 2. これで自分の書いたcodeがGithub上に初めてuploadされます.  

### GUI(Github for DesktopやSource Tree)を使う場合(以下GUIで統一)
 ここは後で.

---
## **Githubの流れ(Local編)**
### Gitを使ってLocalで管理する場合. (多分実演する)
 3. codeの変更やFileの追加をしたら, とりあえず `git add .` を打つ
 3. 何を変更したか, 追加したかを明記するために `git commit -m "initial commit"` を打つ. initial commitと記述されている部分に自分のコメントを打つ.
 3. add -> commitをすると, codeやFileの変更が適用されて保存される.  
 3. これを, remoteのrepository, つまりGithubにあげることができるようになる.
 3. Githubにcodeを送る時は, `git push origin master` と打つと, Remote Repositoryも変更が適用される.  
 3. もし, いくつかの形式で管理をしたい場合は **Branch** というものを使って, 管理をする.
 3. 元は **master** とうBranchにいるが,  `git branch hoge` と打つと, masterではなく, hogeというbranchでcodeなどの管理が別途行われる.  
 ```
$git branch hogehoge
$git branch
       hogehoge
       *master
 ```
 3. もし, 別のbranchで作業したい時は, `git checkout hoge` で現在のbranchからhogeというbranchに移動する. `git branch` のみを打つと, どのようなbranchがあるかを見ることができる.  
 ```
$git branch hogehoge
$git branch
       hogehoge
       *master
$git checkout hogehoge
Switched to branch 'hogehoge'
$git branch
       *hogehoge
       master
 ```  
 3. masterではなく別のbranchにいる状態で, `git push origin master` とやっても, Remote Repositoryの **master** branchに変更が適用されてしまうので, `git push origin hoge` などのように, branchを指定する. そうすると, Remote Repositoryにも **hoge** branchが作成されて, 別途管理ができるようになる.  
 ```
 $git push origin hogehoge
 Total 0 (data0), reused 0 (delta 0)
 To git@github.com:fmsuvM/hugahuga.git
  * [new branch] hogehoge -> hogehoge
 ```
 ![GUI brach1](https://gyazo.com/b7c77c884dea50760b96d7a5010a42b8.jpg)  
 ![GUI branch2](https://gyazo.com/2734ab6ff55bc2332842aaba6baa1801.jpg)

### codeで追う流れ
 - 最初  
 ```
 var electron = require('electron');
 var app = electron.app;
 var BrowserWindow = electron.BrowserWindow;

 var mainWindow = null;
 ```

 - 変更後(少し変わった)
 ```
 let electron = require('electron')
 let app = electron.app
 let BrowserWindow = electron.BrowserWindow

 let mainWindow = null
 ```

 - `git status` を打って確認すると, 更新されてない
 ```
 $git status
 On branch master
 Your branch is ahead of 'origin/master' by 2 commits.
 (use "git push" to publish your local commits)
 Changes not staged for commit:
 (use "git add <file>..." to update what will be committed)
 (use "git checkout --<file>..." to discord changes in working directory)
       modified: index.js
 no changes added to commit (use "git add" and/or "git commit -a")
 ```

 - `git add .` と `git commit -m "message"` を使って更新する  
 ```
 $git add .
 $git commit -m "change import method"
 [master e938284] change import method
 1 file changed, 1 deletion(-)
 $git status
 On branch master
 Your branch is ahead of 'origin/master' by 3 commits.
 (use "git push" to publish your local commits)
 nothing to commit, working directory clean
 ```
 - `git log` で今までのcommit messageや日時を確認可能 ![log](https://gyazo.com/732079fba6a266e2db4ffb844b3f022d.jpg)

---

## **Githubの流れ(Remote編)**  
基本的に用語が多いので, 流れに沿ってGithubを使用しながらその都度説明します.  
**ここはあとでやります**  

### **Clone**
Github上にあるRepositoryを複製して, Local(自分のパソコン)のRepositoryを作ること.  

### **Pull**
Github上のRemote RepositoryからCommit(そのRepositoryの更新)をinstallして, Local Repositoryに反映させること.

### **Fork**  
自分のRemote Repositoryに他の人のRemote Repositoryをコピーすること. これで自分ではない人のRepositoryを編集できる.  

### **Issue**
Issueはプログラム上のバグのような問題がある場合などに飛んできたり飛ばしたりする.

### **Pull Request**  
Pull Requestとは, RepositoryのSource Codeなどの修正などをOwnerに送信するシステム. 主にチーム開発をしている時などに使う.
  - チーム開発のRepositoryを自分のRepositoryとしてForkしてから, Pull Request
  - チーム開発のRepositoryでbranchを作成してから, Pull Request(今回はこっち)
















---
