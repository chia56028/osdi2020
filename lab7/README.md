Lab7
===
#### `Q1` Is it possible that a file exists in a file system, but there is no vnode object of it?
可能。在硬碟剛被插到電腦上的時候，此時 file 存在硬碟中，但卻沒有對應的 vnode。

#### `Q2` Is EOF pass to the reader by a special character in the reader’s buffer?
在 lab7 中，使用 (-1) 來實作 EOF，但如果 user 把 (-1) 字符寫在字串當中，就可能造成誤判。所以可以改讓 reader 透過 f_pos 得知 file 的大小，在讀完後回傳一個值通知 user 已經讀完了。<br>
<br>
※ 思考：在 disk 裡可以很容易的取得檔案大小，但若是在終端機中，要如何得知輸入？socket 中要如何得知封包大小？

#### `Q3` Should each task owns its current working directory and the root directory?
需要紀錄 current working directory，這樣才有辦法知道跟其他 file 或 dir 的相對關係。<br>
可以藉由 ch_root 去限制檔案能 access 到的範圍與其權限。


### Reference
- [Linux 虛擬檔案系統概述](https://b8807053.pixnet.net/blog/post/3612745)
- [詳解 Linux 中的虛擬文件系統](https://kknews.cc/zh-tw/code/l9vlqzz.html)
- [Linux系统调用之open(), close()](http://joe.is-programmer.com/posts/17463.html)