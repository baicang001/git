# git常用命令总结

## git reflog

记录你每一次的详细操作记录。

## git stash

缓存所修改的文件，新添加的文件无法被缓存，需要git add . ,只有被git追踪的文件可以被缓存起来。

```js
// 添加备注，方便查找。也可以直接git stash ，但查找不方便
1. git stash save "备注"

// 查看stash了哪些存储
2. git stash list

// 显示做了哪些改动，默认show第一个存储
3. git stash show

	// 查看其他的存储，比如第二个，0标识第一个
	 <1> git stash show stash@{1}

// 默认显示第一个存储的改动内容
4. git stash show ( stash@{0} ) -p

// 应用某个存储，但不会把存储从存储列表中删除，默认第一个。（应用存储不删除）
5. git stash apply ( stash@{0} )

// 应用某个存储，应用后将此存储删除，默认第一个。（应用存储后删除）
6. git stash pop ( stash@{0} )

// 从列表中删除这个存储。
7. git stash drop stash@{num}

// 删除所有缓存中的stash
8. git stash clear

// 常规的git stash的限制，是它会暂存所有的文件，但有时，我们只想 “暂存部分文件”。
9. git stash --keep-index   ||
   git stash save --keep-index "备注"

	 <1> 先将你不想暂存的文件 add 掉；
   <2> 调用上述命令，只会去暂存没有被add的文件；
	 <3> 取消add的文件。
```

```js
A、B两个分支，
本应该在B分支中写的代码却写在了A分支中，
故：
A中：git stash
在切换到B中：
B中：git stash pop

// git stash 缓存的代码可以在各个分支中共享。
```

