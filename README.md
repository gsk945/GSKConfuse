# GSKConfuse
iOS代码混淆（随机单词拼接）
## 前言
    最近进了一家特殊的公司（你懂得），代码需要时时更新方法名，来降低重复率，网上搜罗了一下，发现随机命名都是随机字符串，这个对于提审到App Store简直是个噩梦，因为机审可能都过不去，所以借鉴https://github.com/housenkui/HSKConfuse自己改了一份，随机方法名为随机单词拼接，哪个方法需要随机混淆由自己定。也搞了份随机单词拼接更改文件名和属性名的，操作比较繁琐就不发在这了。
## 成果
![](https://github.com/gsk945/GSKConfuse/blob/master/screenshots/tu1.jpg)
![](https://github.com/gsk945/GSKConfuse/blob/master/screenshots/tu2.jpg)
## 使用方式
1. 在words.list文件中加入词库的词
2. 在func.list文件中加入想要替换的方法，例如
   ```
   -(void)Function2:(NSString *)str;
   ```
   分别加入Function2和str就可以了，如果有同名的添加一次就可以
3. 在PrefixHeader.pch中加入
   ```
   #import "codeObfuscation.h"
   ```
4. 在Build Phases中新建一个Run Script中加入
  ```
  $PROJECT_DIR/GSKConfuse/Resource/confuse.sh
  ```
  路径根据实际情况来
1. 需要替换confuse.sh中文件的路径
 ![](https://github.com/gsk945/GSKConfuse/blob/master/GSKConfuse/screenshots/tu3.jpg)
##   温馨提示
1. codeObfuscation.h这个文件不能删除，但是可以清空，清空之后就是没替换过混淆的方法名，可以方便调试
2. confuse.sh、words.list、func.list这三个文件都可以删除依赖关系，只要不删除文件就可以了，删除依赖关系之后打包不会有任何脚本信息，否则包内可能会有残留脚本

