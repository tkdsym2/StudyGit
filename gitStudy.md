# ***Github講習会***

---

## **Github is 何**
簡単に言うと, 自分のcodeをversionごとに保存してくれるファイル(うまい説明よろ)
他の人のRepository(上でいうファイル)に色々な
詳しくは [ここ](https://ja.wikipedia.org/wiki/GitHub)に書いてあります
後で色々付け加える.

---

## **BitBucketと何が違うねん**
~~うるさい~~


---

## **Githubの始め方**  

 1. [ここ](https://github.com/)にいってmail addressとpasswordを登録  

 1. GUIかCUIで操作  
  - GUIの場合, [SourceTree](https://www.sourcetreeapp.com/) か [Github for Desktop](https://desktop.github.com/) をinstall
  - MAC Userはhomebrew入ってれば `brew install git` でterminal用のgitがinstallできる  
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
Gitを使ってLocalで管理する場合です.  
 3. codeの変更やFileの追加をしたら, とりあえず `git add .` を打つ
 3. 何を変更したか, 追加したかを明記するために `git commit -m "initial commit"` を打つ. initial commitと記述されている部分に自分のコメントを打つ.
 3. add -> commitをすると, codeやFileの変更が適用されて保存される.  
 3. これを, remoteのrepository, つまりGithubにあげることができるようになる.
 3. Githubにcodeを送る時は, `git push origin master` と打つと, Remote Repositoryも変更が適用される.  
 3. もし, いくつかの形式で管理をしたい場合は **Branch** というものを使って, 管理をする.
 3. 元は **master** とうBranchにいるが,  `git branch hoge` と打つと, masterではなく, hogeというbranchでcodeなどの管理が別途行われる.
 3. もし, 別のbranchで作業したい時は, `git checkout hoge` で現在のbranchからhogeというbranchに移動する. `git branch` のみを打つと, どのようなbranchがあるかを見ることができる.  
 3. masterではなく別のbranchにいる状態で, `git push origin master` とやっても, Remote Repositoryの **master** branchに変更が適用されてしまうので, `git push origin hoge` などのように, branchを指定する. そうすると, Remote Repositoryにも **hoge** branchが作成されて, 別途管理ができるようになる.  


---

## **Githubの流れ(Remote編)**  
基本的に用語が多いので, 流れに沿ってGithubを使用しながらその都度説明します.  
**ここはあとでやります**
 4. **Issue** :  Issueはプログラム上のバグのような問題がある場合などに飛んできたり飛ばしたりします.
  - Issueが飛んできます(画像挿入)
  - Issueが解決したと思ったら返信します(画像挿入)
  - 問題は解決したので, Issueを閉じます(画像挿入)

 4. **Pull Request**
  -    
  -   
  -  
















---
