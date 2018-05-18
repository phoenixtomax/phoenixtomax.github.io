# Linux Shell Skill

### wget
```
wget -r -np -nH --cut-dirs=3 -R index.html http://hostname/aaa/bbb/ccc/ddd/
```
Explanation:

It will download all files and subfolders in ddd directory:
* recursively (-r),
* not going to upper directories, like ccc/… (-np),
* not saving files to hostname folder (-nH),
* but to ddd by omitting first 3 folders aaa, bbb, ccc (--cut-dirs=3)
* excluding index.html files (-R index.html)

```
Refs: https://stackoverflow.com/questions/23446635/how-to-download-http-directory-with-all-files-and-sub-directories-as-they-appear
```
