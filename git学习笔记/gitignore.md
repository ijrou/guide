### 忽略特殊文件   .gitignore

在git中如果想忽略掉某个文件或文件夹，不让这个文件提交到版本库中，可以使用修改根目录中 .gitignore 文件的方法（如无，则需自己手工建立此文件）。

* 新建方法一（最直接）：
  在资源管理创建文件时，文件命名`.gitignore.`，注意结尾有个.号，回车确认时系统会自动存成`.gitignore`。

* 新建方法二：
  打开文本编辑器，保存时文件名输入 `.gitignore` ，保存类型选“所有文件”

* 新建方法三：
  进入cmd命令行，执行 `echo > .gitignore` 输入空内容并创建文件，或执行 `rename somefile .gitignore、copy somefile .gitignore` 从已有文件复制、重命名。




该文件每一行保存了一个匹配的规则例如：


```
# 此为注释 – 将被 Git 忽略
*.a       # 忽略所有 .a 结尾的文件
!lib.a    # 但 lib.a 除外
/TODO     # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
build/    # 忽略 build/ 目录下的所有文件
doc/*.txt # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```


规则很简单，不做过多解释，但是有时候在项目开发过程中，突然心血来潮想把某些目录或文件加入忽略规则，按照上述方法定义后发现并未生效，原因是.gitignore只能忽略那些原来没有被track跟踪过的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。那么解决方法就是先把本地缓存删除（改变成未track状态），然后再提交：
```github
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```


推荐一个 ignore 自动生成网址 http://www.gitignore.io

