### Git Diff
#### git diff file_name  
对比工作区和暂存区差异  
```git
liang.liang@ubuntu:~/code/OnlyForTest$ git diff a1.md 
diff --git a/a1.md b/a1.md
index 524cb55..c200906 100644
--- a/a1.md
+++ b/a1.md
@@ -1 +1 @@
-1.1.1
+222

```


#### git diff HEAD -- file_name
对比工作区和本地版本库差异  
```git
liang.liang@ubuntu:~/code/OnlyForTest$ git diff HEAD -- a1.md 
diff --git a/a1.md b/a1.md
index 524cb55..c200906 100644
--- a/a1.md
+++ b/a1.md
@@ -1 +1 @@
-1.1.1
+222
```
