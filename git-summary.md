## Git

### Git安装
- Windows: http://git-scm.com
- Mac: 如果安装过xcode自带git, homebrew是wmac的包管理器
	- http://ohmyz.sh/
	- http://www.iterm2.com/

### 配置用户 (不配置用户不能提交代码)
```
	
	git config --list 查看git的配置文件
	git config --global user.name "你的用户名"
	git config --global user.email "你的邮箱地址"
	
	还可以直接修改git的配置文件的方式来进行修改
	打开全局的.gitconfig文件的命令为：vi ~/.gitconfig; 然后在文件中直接修改即可
```

### 初始化git
- 一个项目初始化一次, 不能嵌套
```
	git init 告诉git哪个文件夹被git管理
	git status 查看git状态
	
```
### 添加到暂存区
```
	git add ./ -A / <文件名>	| 参数[可选]: .或者-A 表示所有文件  
	例子:
	git add .
	git add 1.txt
	git add -A
	git add *.txt
```

### 删除暂存区
```
	git rm --cached <文件名>	删除暂存区
```
### 提交到版本区
```
	git commit -m "注释内容"
```
### 查看版本历史记录
```
	git log   | 参数:--graph 显示ASCII 图形表示的分支合并历史  --oneline 压缩模式,在每个提交的旁边显示经过精简的提交哈希码和提交信息,以一行显示.
```
> 修改时通过git status查看当前状态

### git diff   不同区的代码比较
- 工作区和暂存区比较
```
	git diff
```
- 工作区和版本区比较
```
	git diff master 
```
- 暂存区和版本区比较
```
	git diff --cached
```
### 撤销
```
	git checkout <文件名>	将暂存区的内容覆盖工作区的
```
### 回滚暂存区
```
	git reset HEAD <文件名> 回到上一次的缓存区
```
>	history > 文件名	将历史记录保存到一个文件里
>例子: 	history > 1.txt	现在1.txt保存着历史记录

### 回滚版本区
```
git reset --hard <版本号>   会把<版本区的内容>覆盖掉<暂存区的内容>和<工作区的内容>
git reset --hard HEAD^ 快速回到上一个版本
<版本号>可以通过命令git log查看历史日志
```
> git reflog 查看所有的历史日志

### 分支
- 查看分支
```
	git branch
```
- 创建分支
```
	git branch <分支名>  
```
- 切换分支
```
	git checkout <分支名>
```
- 删除分支
```
	git branch -D <分支名>  
```
> 注意: 不能在当前分支下删除当前的分支, 可以切换到master主干或者当前分支的父级分支再删除
> 
- 创建并切换分支
```
	git checkout -b <分支名>
```
> 提交文件到版本区此时两个分支就没关系了

### 文件修改切换分支
```
	git stash 	暂存文件
	git stash pop 还原暂存的内容
```
> 分支有更改不能直接切换, 可以提交更改或者暂存更改, 暂存使用过渡区的覆盖掉工作区的
### 合并分支
```
	git merge <分支名>
```
### 解决冲突
- 遇到冲突时只能手动的解决冲突,留下想要的结果再次提交
```
	发生这种情况主要是master分支和子分支上两个相同的文件, 但是内容不同并且都commit了
	此时在合并分支时, 修改文件内容选择需要保留的,再次提交到暂存区,然后提交到版本区
```
### 本地仓库 -> github
- github账号
#### 本地提交
- README.md
- 创建一个.gitignore文件 (用于忽略不需要跟踪的文件)
	```
		.idea
		/node_modules
		.DS_Store
	```
- git不会上传空文件夹

  - 有时候没有文件可放又想保持目录文件夹的完整,而空目录不会被git上传, 可在空文件夹内, 创建一个.gitkeep文件

### 关联远程仓库
- git remote add origin <地址>
  - origin 表示<地址>的别名, 这个自己可以取名, 如果用了别名, git push也要使用别名
  -  如: git push -u <别名> <地址>,  一般都使用origin

```
git remote add origin <地址>
例子:git remote add origin https://github.com/fantasy0617sky/node-project.git
```
- 查看关联
```
git remote -V
```
- 删除关联
```
git remote rm 名字/别名			// 当输入的地址是错误的, 可以使用这个命令删除
```
- 推到远程仓库
	- git push -u origin master
	- 参数: -u表示加了-u参数, 以后用git push就默认推送到origin
```
git push origin master
```
- 拉取最新的代码
```
git pull origin master
```
### gh-pages分支发不静态页
- 在项目创建一个gh-pages分支
- 将分支提到线上仓库
- 找到提供给你的网址	settings github-pages
```
	git checkout -b gh-pages
	touch index.html
	git add .
	git commit -m 'xxxx'
	git push origin 
```

### linux命令

- pwd (print working directory)

  - 打印工作目录
```
	pwd
```

- rm -rf  <文件夹>  | rm <文件名>

  - 删除文件
```
	rm -rf 1.txt
	rm 1.txt
```

- mkdir <文件夹名字>	创建目录
```
	mkdir demo-01
```

- cd <目录名>	change directory
```
	cd d:/program
```

- ls -al 显示目录下所有的文件
```
	ls -al
```

- touch <文件名>	创建文件
```
	touch 1.txt	// 创建了一个1.txt
```

- cat <文件名>	查看文件内容
```
	cat 1.txt		// 查看1.txt文件内容
```

- vi <文件名>	编辑文件     i: 插入模式	esc 退出编辑模	:q! 强制退出	:wq 保存并退出
  - 进入命令行, 输入: vi <文件名>  进入文件编辑窗口
  - 按 i 键, 插入模式,窗口下方显示 -- insert-- , 现在可以在窗口编写文件的内容
  - 按esc退出编辑模式 --> :q! 强制退出 (强制退出不保存修改过的文件内容)	|	:wq 保存退出
```
	vi 1.txt
```

- echo 输入文件内容
```
	echo "内容" > 1.txt	  // 一个>表示写入内容
  echo "内容" >> 1.txt	  // 一个>表示追加内容
```