### Reset
场景： 本地改了一些东西，也commit到本地了，但是尚未push到远端分支。这时候发现commit错误了，需要回退。
* reset --hard commit-id
* reset --mixed commit-id  （revert commit-id 等同 revert --mixed commit-id ） 
* reset --soft commit-id
### reset --hard commit-id.
- 场景：如果只需要一个干净的版本，使用hard 模式   
- 危险
- 工作区和暂存区都会丢失
### reset commit-id
- 场景：需要保留修改的内容，用mixed 模式（及默认模式）
- 安全
- 如果同一份文件工作区和暂存区都有修改，保留工作区修改
- 如果一份文件只在暂存区有修改，暂存区内容会到工作区
- commit 拆出来内容（commit 与 commit 之间的delta 部分）会放在工作区
### reset --soft commit-id
- 这个模式比较鸡肋，正常工作用不到，此处不讨论。
