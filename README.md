# crepubver
crepub规定和使用的一种与semver对应的、用于宣传和交流的版本号规则。

## 简表
|说明|crepubver|semver|
|:-----:|:--:|:--:|
|X分支的第一个开发中版本|X100a|0.100.0|
|小型功能更新|X101a|0.101.0|
|主要功能更新|X200a|0.200.0|
|第一个测试版本|X500b|0.500.0|
|第一个RC版本|X1000rc|1.1000.0-rc|
|第一个正式版本|X1000|1.1000.0|
|开发中版本|X1001a1|1.1001.0-alpha1|
|测试版本|X1001b1|1.1001.0-beta1|
|RC版本|X1001rc1|1.1001.0-rc1|
|小型功能更新|X1001|1.1001.0|
|中型功能更新|X1100|1.1100.0|
|主要功能更新|X2000|1.2000.0|
|问题修正|X2000p1|1.2000.1|
|不兼容更新|X7000|2.7000.0|
|新的Z分支的第一个正式版本|Z1000|3.1000.0|

## 背景
crepub使用semver为基础来设定版本号，但我们希望我们能够尽可能长久的保持向下兼容。一些项目至今保持着1.x的版本号，这其实体现了其优秀的稳定性和向下兼容性，但却给不熟悉semver的人一种很久没有大更新的感觉，但实际上从1.0以来可能已经有了巨大的进步，一个实际上是值得肯定的行为体现在宣传中却对不懂的人可能会产生负面印象，这是额外规定和使用crepubver的主要动机。

crepubver主要设计为用来宣传和交流使用，实际依赖管理还是使用semver，且每个crepubver应该有唯一semver。

crepubver同时希望能够在宣传和交流时表达诸如所属分支（这个分支是概念意义上的，设计是否有重大改动的分支，而不是指兼容性上的），更新内容的重要程度等信息。

## 细节
### 分支名称
crepubver以分支名称开头，我们一般使用某个特定字母来表示分支。

分支与semver大版本号可以是一对多的，semver大版本号变化时，如果设计思路并没有大的改变，那么分支名称可以保持原样，但建议使用非常明显的版本代码变化来表示不兼容。

### 版本代码
对应semver的小版本号，一般使用4位数字来表达三种不同程度的更新，例如：
- ```1000```代表第一个稳定版本
- ```1001```代表小型功能更新
- ```1100```代表中型功能更新，例如社区有一部分人曾表示期待的功能被实现
- ```2000```代表主要功能更新，一般是所有用户都能明显感觉到的大型功能更新，例如界面的明显变化，重要功能的添加。有时也许只是累积的普通功能更新版本号满了，也会如此增加
- ```9000```过后的下一个大更新是```10000```，再下一个是```11000```还是```20000```视情况而定，一般选择```11000```来避免数值膨胀的太快。
- 对于第一个发布版本之前的版本，一般推荐使用3位数版本代码，此时的数字增加比较随意，一般推荐小更新递增，大更新第一位数字加一。

### 修正版本
对应semver的修正版本号，在结尾加上p后从1开始递增
