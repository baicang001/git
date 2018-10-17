## 本地分支之间的代码更新rebase

```json
git clone 123456789
```

```json
git checkout -b dev origin/dev   // 本地 dev 分支 ---> 与远程映射的 dev 分支
```

```json
git checkout -b wydev   // 本地 wydev 分支 ---> 再次分支中开发代码
```

```js
// 要合并到本地的 dev 时,先切回到本地的 dev 分支
git rebase wydev dev  /* 就是以代码更新过的分支为基础(原点), 若 wydev 分支有更新,则将 dev 分支推到 wydev 分支更新的节点上,这样就相当于将 wydev 中更新的代码合并(添加)到了 dev 上 */	   
```



## 提交代码

> 我在本地的分支中已经开发好了代码( dev 分支中 ), 准备提交
>
> 首先, 得先将远程仓库中的代码先拉取下来  ( 当前指针指向本地 dev 分支 )

```js
// 1 fetch
git fetch origin  // 将远程仓库中的 dev 分支代码缓存一份到了本地

// 2 rebase
git rebase origin/dev dev  /* 已远程仓库的代码为基础(原定),将本地的 dev 分支推到与远程 dev 相同的节点上,就是将远程代码拉下来 */

// 3 手动合并冲突

// 4 
git add .

// 5
git rebase --continue   // 提交代码到本地仓库,相当于 git commit -m "123456"

// 6
git push origin dev    // 提交代码到远程 dev

// 注意 : 在这里要删除 wydev 要 git branch -D wydev

```



## 每天工作前

> 先将远程仓库的代码拉下来

```js
// 1
git fetch origin

// 2
git rebase origin/dev
```







