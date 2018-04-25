# Windows XP下的Sublime Text 配置文件
因为一些原因，我有时候仍然需要在Windows XP下使用Sublime Text和Git。所以整理了一下Sublime Text的配置文件。
## 配置Git for Windows的$HOME界面
在安装了Git for Windows后，每次打开Git命令行，进入的默认目录通常是
```
C:\Users\Bill
```
为了节约时间，直接进入到我们想要的Repository目录下，可以通过修改`$HOME`的路径来实现。
- 打开你按照Git for Windows的路径，找到`Git\etc\profile`，这里的`profile`文件是不带后缀的。使用文本编辑器打开`profile`文件。
- 找到如下代码的地方
```
# normalize HOME to unix path
HOME="$(cd "$HOME" ; pwd)"
export PATH="$HOME/bin:$PATH"
```
- 添加两行代码，使得更改的代码为（代码之间如果有空行，不影响配置生效）：
```
# normalize HOME to unix path
HOME="E:/develop/codebase"
HOME="$(cd "$HOME" ; pwd)"
cd
export PATH="$HOME/bin:$PATH"
```
`HOME`出现的第一行后面引号内的内容将会是你打开Git命令行后进入的默认目录。
- 重启Git for Windows，生效。
## 配置Sublime Text为Git for Windows的默认文本编辑器
强烈建议先配置了Git for Windows的`$HOME`界面再操作这一步。主要步骤如下：
在Git for Windows的HOME目录新建一个`.bashrc`文件，在Windows XP下实现这一步最简便的方式是通过命令行。打开Git for Windows，输入以下命令：
```
echo alias subl="e:/billApp/sublime\ text/sublime_text.exe" > .bashrc
```
然后你可以看到，在`$HOME`界面的目录下可以看到多了一个`.bashrc`文件，使用文本编辑器打开它，确保里面的内容与如下所示一致（可能会出现异常字符，删除它，重新写入如下代码）：
```
alias subl="e:/billApp/sublime\ text/sublime_text.exe"
```
说明如下：
- `alias` 别称的意思，这里相当于设置一个自定义命令。
- `subl` 这里将在Git for Windows的命令行界面打开Sublime Text编辑器的快捷命令设置为subl。
- 双引号内修改为你想要在Git for Windows的命令行界面快速运行的应用程序的绝对路径。这里是Sublime Text的路径，其实对其他支持用cmd打开的应用程序也一样。
- 使用方法
    + `subl` 直接打开Sublime Text编辑器
    + `subl index.html` 使用Sublime Text编辑器新建一个`index.html`文件并打开它

以上配置针对的环境为Windows XP系统，Windows 7及以上会更加简单。
