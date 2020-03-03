ab -k -c 10 -n 400 "http://engine.supamob.com.cn/req_ad"

./dspmock --maxconn 1000 --plantime 50 --port 9090 > dspmock9090.log 2>&1 &


GOOS=linux GOARCH=amd64 go build

strace -f -F -o ~/adx_engine.txt /home/huyunzhi/adx-engine/adx_engine
这里 -f -F选项告诉strace同时跟踪fork和vfork出来的进程，-o选项把所有strace输出写到~/dcop-strace.txt里 面，dcopserver是要启动和调试的程序

TCP Dump消息
sudo tcpdump -vvvv -tttt  -A host  port 
Flags
* F : FIN - 结束; 结束会话
* S : SYN - 同步; 表示开始会话请求
* R : RST - 复位;中断一个连接
* P : PUSH - 推送; 数据包立即发送
* A : ACK - 应答
* U : URG - 紧急
* E : ECE - 显式拥塞提醒回应
* W : CWR - 拥塞窗口减少



https://github.com/google/eng-practices


curl —v H "Content-Type:application/json" -X POST --data ‘{“id":"628fd83d940e4ddaa2edefd83445479b”,”version”:”3.0”}’   https://dsp-test-x.jd.com/


git branch -r
-r 远程分支
-a 所有本地和远程分支

从特定tag开始项目
$ git clone git://git.kernel.org/pub/scm/.../linux-2.6 my2.6
$ cd my2.6
$ git branch my2.6.14 v2.6.14   (1)
$ git switch my2.6.14
1. This step and the next one could be combined into a single step with "checkout -b my2.6.14 v2.6.14".

删除不需要的分支
$ git clone git://git.kernel.org/.../git.git my.git
$ cd my.git
$ git branch -d -r origin/todo origin/html origin/man   (1)
$ git branch -D test                                    (2)

1. Delete the remote-tracking branches "todo", "html" and "man". The next fetch or pull will create them again unless you configure them not to.See git-fetch(1).
2. Delete the "test" branch even if the "master" branch (or whichever branch is currently checked out) does not have all commits from the test branch.


合并Merge 冲突
$git fetch origin
$git checkout -b feature-dsplog origin/feature-dsplog

$git fetch origin
$git checkout origin/master

合并merge操作
$git merge --no-ff feature-dsplog
查看冲突
$git status
On branch master
Your branch is up to date with 'origin/master'.

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
	modified:   src/adx-engine-service/dsp/apus/request.go
	new file:   src/adx-engine-service/dsp/lenovo/request.go
	new file:   src/adx-engine-service/dsp/lenovo/response.go
	new file:   src/adx-engine-service/dsp/lenovo/sender.go
	modified:   src/adx-engine-service/dsp/oppo/request.go

Unmerged paths:
  (use "git add <file>..." to mark resolution)
	both added:      src/adx-engine-service/dsp/apus/response.go
	both modified:   src/adx-engine-service/dsp/yingla/sender.go
	both modified:   src/adx-engine-service/service/auctionservice.go

修改冲突
$git add src/adx-engine-service/dsp/apus/response.go
$git add src/adx-engine-service/dsp/yingla/sender.go
$git add  src/adx-engine-service/service/auctionservice.go
提交
$git commit
$git push

rebase冲突
$ git rebase dog
First, rewinding head to replay your work on top of it...
Applying: add cat 1
Applying: add cat 2
Applying: add 123
Applying: update index
Using index info to reconstruct a base tree...
M	index.html
Falling back to patching base and 3-way merge...
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
error: Failed to merge in the changes.
Patch failed at 0004 update index
The copy of the patch that failed is found in: .git/rebase-apply/patch

When you have resolved this problem, run "git rebase --continue".
If you prefer to skip this patch, run "git rebase --skip" instead.
To check out the original branch and stop rebasing, run "git rebase --abort"

$git add index.html
$git rebase --continue


result = df.sort(['A', 'B'], ascending=[1, 0])
