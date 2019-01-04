# Mac 利用rsync差异化备份

## 简单备份

命令行并不等同于复杂，rsync 的基础语法就非常简单：

```bash
rsync -av [源文件夹路径] [备份路径]
```

把两个路径名替换成你自己的（可以直接拖动文件夹进 Terminal 来获得），之后就可以在 Terminal 里执行了。特别注意的是，**两条路径最后需要以 / 结尾，不然它们会出现在让你觉得莫名其妙的地方。**

我需要备份音乐文件夹到 U盘，就可以用 `rsync -av /Users/apple/Music/ /Volumes/Min\'s/music/`。

![rsync](https://ws2.sinaimg.cn/large/006tNc79ly1ftt2dafdiuj30v40opgmp.jpg)

你会注意的一些乱码，这是由于部分音乐文件名带有中文或日文，不能正常显示，但不会影响备份效果。

rsync 的差异算法非常管用，即使文件名没有改动，它也会备份有过改动的文件。我经常为音频更换专辑封面、添加 tag，过去备份时需要按照修改时间排列、手工选出近期改动的文件，繁琐程度可想而知，换 rsync 就省下一大笔力气。

🚮**删除多余文件**

最简单的 rsync 只会做加法，但那些在源文件夹里删掉的文件，我不想去备份文件夹里再删一遍。`--delete`参数就是用来解决这个问题的：

```
rsync -av [源文件夹路径] [备份路径] --delete
```

在末位添加这一串参数后，如果删除了源文件夹里的某些东西，备份中的对应文件也会乖乖消失。

🙅**不想备份特定文件或文件夹**

在备份音乐文件夹时，我发现里面的 iTunes 文件夹也混了进去，但是我不需要这个东西。可以用 `--exclude "想要排除的文件"` 这串参数来避开它：

```
rsync -av [源文件夹路径] [备份路径] --delete --exclude "想要排除的文件或文件夹"
```

比如我就加了 `--exclude "iTunes"` 来避免同步 iTunes 文件夹。文件名之后记得带上拓展名，尾巴不要落下。如果是文件夹，就不需要带拓展名。

## 一键备份、恢复

命令虽好，但每次输入太麻烦，备份多个文件夹更成了噩梦。做一个脚本就解决问题了。

1.打开 Automator，新建一个「应用程序」，添加一个「运行 Shell 脚本」步骤；

2.把刚才测试成功的命令粘贴进去。想备份多个文件夹，就粘一条换一行，它们会依次执行；

![automator](https://ws2.sinaimg.cn/large/006tNc79ly1ftt2dpr8h7j30v40o1403.jpg)automator

3.保存好刚才制作的应用程序，放在方便取用的地方。

以后需要备份的话，双击它就完成了👏。

至于恢复备份的应用程序，制作起来也不难，只需要把源文件夹路径与备份路径换一下。此时你最好慎用 `--delete` 参数，降低丢失文件的风险。

## 定时备份

还记得用日历启动定时任务的技巧吗？你当然可以用同样的方法启动定时备份了。

![把提醒换成打开程序](https://ws2.sinaimg.cn/large/006tNc79ly1ftt2fkpws9j30v40js409.jpg)把提醒换成打开程序

iMac、Mac mini 可以等长期通电的设备可以在夜深人静时自己备份，利用闲置时间，不影响白天工作。可惜我在外使用的是笔记本电脑，闲置时都在盒盖休眠，无福享受。

## 总结

rsync 方便高效，灵活、可定制，和 Automator、日历配合能满足更多需求。我现在备份音乐、照片和 PDF 都会使用它。

但是相比 Time Machine、Git 等工具，rsync 的局限也很明显：没有版本记录，也就没有炫酷的时光机功能，如果你需要频繁回溯到历史版本——尤其当你从事编程或设计等工作时——rsync 不是一个好选择。但不保存这些历史记录也就更省空间，小小的 U盘就足够胜任，事实上，我使用普通 U盘的时间远远多余搭载 Time Machine 的硬盘。

对我来说，rsync 更适合保存一些零碎的、私人的文件。推荐把备份作为每周甚至每日的例行任务，给自己的文件多加一道保险。



> ```
> -v, --verbose 详细模式输出。
> -q, --quiet 精简输出模式。
> -c, --checksum 打开校验开关，强制对文件传输进行校验。
> -a, --archive 归档模式，表示以递归方式传输文件，并保持所有文件属性，等于-rlptgoD。
> -r, --recursive 对子目录以递归模式处理。
> -R, --relative 使用相对路径信息。
> -b, --backup 创建备份，也就是对于目的已经存在有同样的文件名时，将老的文件重新命名为~filename。可以使用--suffix选项来指定不同的备份文件前缀。
> --backup-dir 将备份文件(如~filename)存放在在目录下。
> -suffix=SUFFIX 定义备份文件前缀。
> -u, --update 仅仅进行更新，也就是跳过所有已经存在于DST，并且文件时间晚于要备份的文件，不覆盖更新的文件。
> -l, --links 保留软链结。
> -L, --copy-links 想对待常规文件一样处理软链结。
> --copy-unsafe-links 仅仅拷贝指向SRC路径目录树以外的链结。
> --safe-links 忽略指向SRC路径目录树以外的链结。
> -H, --hard-links 保留硬链结。
> -p, --perms 保持文件权限。
> -o, --owner 保持文件属主信息。
> -g, --group 保持文件属组信息。
> -D, --devices 保持设备文件信息。
> -t, --times 保持文件时间信息。
> -S, --sparse 对稀疏文件进行特殊处理以节省DST的空间。
> -n, --dry-run现实哪些文件将被传输。
> -w, --whole-file 拷贝文件，不进行增量检测。
> -x, --one-file-system 不要跨越文件系统边界。
> -B, --block-size=SIZE 检验算法使用的块尺寸，默认是700字节。
> -e, --rsh=command 指定使用rsh、ssh方式进行数据同步。
> --rsync-path=PATH 指定远程服务器上的rsync命令所在路径信息。
> -C, --cvs-exclude 使用和CVS一样的方法自动忽略文件，用来排除那些不希望传输的文件。
> --existing 仅仅更新那些已经存在于DST的文件，而不备份那些新创建的文件。
> --delete 删除那些DST中SRC没有的文件。
> --delete-excluded 同样删除接收端那些被该选项指定排除的文件。
> --delete-after 传输结束以后再删除。
> --ignore-errors 及时出现IO错误也进行删除。
> --max-delete=NUM 最多删除NUM个文件。
> --partial 保留那些因故没有完全传输的文件，以是加快随后的再次传输。
> --force 强制删除目录，即使不为空。
> --numeric-ids 不将数字的用户和组id匹配为用户名和组名。
> --timeout=time ip超时时间，单位为秒。
> -I, --ignore-times 不跳过那些有同样的时间和长度的文件。
> --size-only 当决定是否要备份文件时，仅仅察看文件大小而不考虑文件时间。
> --modify-window=NUM 决定文件是否时间相同时使用的时间戳窗口，默认为0。
> -T --temp-dir=DIR 在DIR中创建临时文件。
> --compare-dest=DIR 同样比较DIR中的文件来决定是否需要备份。
> -P 等同于 --partial。
> --progress 显示备份过程。
> -z, --compress 对备份的文件在传输时进行压缩处理。
> --exclude=PATTERN 指定排除不需要传输的文件模式。
> --include=PATTERN 指定不排除而需要传输的文件模式。
> --exclude-from=FILE 排除FILE中指定模式的文件。
> --include-from=FILE 不排除FILE指定模式匹配的文件。
> --version 打印版本信息。
> --address 绑定到特定的地址。
> --config=FILE 指定其他的配置文件，不使用默认的rsyncd.conf文件。
> --port=PORT 指定其他的rsync服务端口。
> --blocking-io 对远程shell使用阻塞IO。
> -stats 给出某些文件的传输状态。
> --progress 在传输时现实传输过程。
> --log-format=formAT 指定日志文件格式。
> --password-file=FILE 从FILE中得到密码。
> --bwlimit=KBPS 限制I/O带宽，KBytes per second。
> -h, --help 显示帮助信息。
> ```