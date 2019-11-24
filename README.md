# conflict-sandbox
コンフリクトの解消を練習するためのリポジトリです

## 使い方

`feature-branch-1`と`feature-branch-2`でそれぞれのファイルに対してconflictするような変更を加えています。

### mergeでコンフリクトさせる場合
    
最終的に`feature-branch-1`と`feature-branch-2`をmergeさせるような手順であればコンフリクトします。
以下のような手順があります（他にもあります）。

* `feature-branch-1`に`feature-branch-2`をmergeする
    ```console
    $ git switch feature-branch-1
    $ git merge feature-branch-2
    ```
* `master`に`feature-branch-1`をmergeして、`master`に`feature-branch-2`をmergeする
    ```consosle
    $ git switch master
    $ git merge feature-branch-1
    $ git merge feature-branch-2
    ```

※ `feature-branch-1`と`feature-branch-2`のmerge順はどちらが先でも問題ありません。

### rebaseでコンフリクトさせる場合

rebaseを行う場合には、以下のような操作を行います。

1. `master`に`feature-branch-1`をmergeする
2. `feature-branch-2`で`master`を起点としてrebaseする

    ```console
    $ git switch master
    $ git merge feature-branch-1
    $ git switch feature-branch-2
    $ git rebase master
    ```

### 初期化する方法

各ブランチの初期位置にtagを打っているので、それぞれのブランチを対応するtagまでresetしてください。

```console
$ git switch master
$ git reset --hard base
$ git switch feature-branch-1
$ git reset --hard feature-1
$ git switch feature-branch-2
$ git reset --hard feature-2
```
