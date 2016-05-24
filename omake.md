# **おまけ**

## **1: 他のGit Hosting Serviceと何が違うねん**

### **GitHub**

- フリーアカウントで無限に **Public Repository** を作れる. **Private Repository** を作るには別のPlanにする必要がある.
- HTTPS, SSH
- Wiki, Gist
- pull request
- 自分のweb pageを公開できる(ドメインを用意してくれる)
- チームのメンバーは人数制限なし
- 学生だったら無限にprivateリポジトリを作れる. [ここ](https://education.github.com/pack)
### **BitBucket**

- 大体GitHubと同じ.
- フリープランでPublicとPrivateの **両方の** リポジトリが無制限に作れる.
- メンバーはフリープランだと5人まで
- Gistはない

### **GitLab**

- 大体GitHubと同じ.
- Public, Privateの **両方の** リポジトリを無制限に作れる.
- メンバーは無制限
- 最新のGitLab(または, gitlab.comにてホスティングされているもの)には, Wiki機能がついている[(参考)](https://github.com/fmsuvM/GitStudy/blob/tkd/gitStudy.md#gitlab)

## **2: 幾つかの形式でコードやファイルを管理したい場合**

1. もし, いくつかの形式で管理をしたい場合は **Branch** というものを使って, 管理をする.
2. 元は **master** というブランチにいるが, `git branch hoge` と打つと, masterではなく, hogeというブランチでコードなどの管理が別途行われる.

  ```
  $git branch hogehoge
  $git branch
     hogehoge
     *master
  ```

3. もし, 別のブランチで作業したい時は, `git checkout hoge` で現在のブランチからhogeというブランチに移動する. `git branch` のみを打つと, どのようなブランチがあるかを見ることができる.

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

4. masterではなく別のブランチにいる状態で, `git push origin master` とやっても, リモートリポジトリの **master** ブランチに変更が適用されてしまうので, `git push origin hoge` などのように, ブランチを指定する. そうすると, リモートリポジトリにも **hoge** ブランチが作成されて, 別途管理ができるようになる.

  ```
  $git push origin hogehoge
  Total 0 (data0), reused 0 (delta 0)
  To git@github.com:fmsuvM/hugahuga.git
  * [new branch] hogehoge -> hogehoge
  ```

  ![GUI brach1](https://gyazo.com/b7c77c884dea50760b96d7a5010a42b8.jpg)<br>
  ![GUI branch2](https://gyazo.com/2734ab6ff55bc2332842aaba6baa1801.jpg)


## **3: 他のCommand**
### **clone**
GitHub上にあるリポジトリを複製して, ローカル(自分のパソコン)のリポジトリを作る.  
`git clone <Repository URL>`

### **fetch**
GitHub上のリモートリポジトリからローカルリポジトリに最新の状態を反映させる.  
pullのようにファイルが更新されるわけではない.  
`git fetch`

### **merge**
ローカルのファイルを更新して, コミットするとブランチはmasterに入る. ローカルの作業ディレクトリはmaster branchと結びついている.  
origin/masterというブランチはGithubのリモートリポジトリと結びついているブランチ. `git fetch` をすると, **origin/master** が更新される.  
これだとmaster branchは **更新されていない** ので `git merge origin/master` をする.  
こうすると, origin/masterの変更が, masterにも反映される. **master <- origin/master**

### **pull**
fetchとmergeを合体させたようなもの.  
GitHub上のリモートリポジトリからコミット(そのリポジトリの更新)をインストールして, ローカルリポジトリに反映させること.  
`git pull origin <branch name>`

### **fork**  
自分のリモートリポジトリに他の人のリモートリポジトリをコピーすること. これで自分ではない人のリポジトリを編集できる.  

### **issue**
Issueはプログラム上のバグのような問題がある場合などに飛んできたり飛ばしたりする.

### **Pull Request**  
Pull Requestとは, リポジトリのコードなどの修正などを作成者に送信するシステム. 主にチーム開発をしている時などに使う.
  - チーム開発のリポジトリを自分のリポジトリとしてForkしてから, Pull Request
  - チーム開発のリポジトリでブランチを作成してから, Pull Request(今回はこっち)

## **4: 参考にしたサイト**

[サルでもわかるgit入門](http://www.backlog.jp/git-guide/)  

[onsen-2015-summer-textbook](https://github.com/post-internet/onsen-2015-summer-textbook/tree/master/001_mactkg)
