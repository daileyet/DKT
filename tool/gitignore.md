# gitignore

.gitignore文件记录哪些文件及文件夹不需要版本控制

## 使用方法

1. 创建.gitignore,放置项目根目录
2. 编辑.gitignore文件
   1. 以斜杠“/”开头表示目录
   2. 以星号“\*”通配多个字符
   3. 以问号“?”通配单个字符
   4. 以方括号“\[\]”包含单个字符的匹配列表
   5. 以叹号“!”表示不忽略\(跟踪\)匹配到的文件或目录
   6. git 对于 .ignore 配置文件是按行从上到下进行规则匹配的，意味着如果前面的规则匹配的范围更大，则后面的规则将不会生效

## 示例

| 规则 | 说明 |
| :--- | :--- |
| fd1/\* | 忽略目录 fd1 下的全部内容；注意，不管是根目录下的 /fd1/ 目录，还是某个子目录 /child/fd1/ 目录，都会被忽略 |
| /fd1/\* | 忽略根目录下的 /fd1/ 目录的全部内容 |
| /\*  !.gitignore !/fw/bin/ !/fw/sf/ | 忽略全部内容，但是不忽略 .gitignore 文件、根目录下的 /fw/bin/ 和 /fw/sf/ 目录 |
|  |  |

```text
# 忽略 .a 文件
*.a
# 但否定忽略 lib.a, 尽管已经在前面忽略了 .a 文件
!lib.a
# 仅在当前目录下忽略 TODO 文件， 但不包括子目录下的 subdir/TODO
/TODO
# 忽略 build/ 文件夹下的所有文件
build/
# 忽略 doc/notes.txt, 不包括 doc/server/arch.txt
doc/*.txt
# 忽略所有的 .pdf 文件 在 doc/ directory 下的
doc/**/*.pdf
```

## 注意

.gitignore只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的

解决办法

```text
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```

