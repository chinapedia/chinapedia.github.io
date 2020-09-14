# 中国百科

* 中国百科是针对维基百科内容的一系列导出、转换和翻译计划。
* 目前计划中，中国百科的内容有三处来源：[中文维基百科](https://zh.wikipedia.org/)的内容导入如[chinapedia/wikipedia.zh](https://github.com/chinapedia/wikipedia.zh)，[英文维基百科](https://en.wikipedia.org/)、英文学术论文以及其它来源内容的[中文翻译站](https://en.chinapedia.org/)，以及[用户创作内容站](https://zh.roomchat.im/)。
* 从[维基百科](https://www.wikipedia.org/)首页可以看到，目前[英文维基百科](https://en.wikipedia.org/)有大约568万词条，但是中文仅有101万。我最近有发现有稍微专业一些的术语没有维基百科中文词条，如果有可读的翻译，将会极大丰富中文互联网内容。
* [中文维基百科](https://zh.wikipedia.org/)上审核比较严，不容许出现机器翻译的内容，也很少人有时间精力把其它语言的词条全文翻译，以至于许多词条完全空缺。我的计划是先用机器翻译占位，然后通过人工编辑，逐步改进，同时优化机器翻译的质量。

# 参与本项目

目前有三种参与方式，你可以任选：

* 参与[MediaWiki](https://www.mediawiki.org/)的定制开发、技术维护工作。
* 参与中国百科上词条修改的审核工作。
* 实现并优化英文维基百科以及其它内容到中文翻译的模型优化，因为是 MediaWiki markup 语言的翻译，可能会无法直接套用现成的翻译API。
* 使用[用户创作内容站](https://zh.roomchat.im/)分享行业知识，或者本地信息。

我本人计划先用对比下 Google 和 Microsoft Translator API 的翻译质量，然后用机器翻译出一个版本。

有意参与者可以加本人微信：li_ruqi 或者加入 Telegram 群组：https://t.me/chinapedia 

# Import Wikipedia dump

https://www.mediawiki.org/wiki/Manual:MWDumper

Before using mwdumper, your page, text, revision and redirect tables must be empty. To empty them, do this (note that this will wipe out an existing wiki): 

In SQL: <code>TRUNCATE TABLE page; TRUNCATE TABLE text; TRUNCATE TABLE revision; TRUNCATE TABLE redirect; TRUNCATE TABLE category;</code>

In maintenance directory: <code>php rebuildall.php</code>

# Update domain

https://www.mediawiki.org/wiki/Manual:Moving_a_wiki

<pre>
-- Update entries in module_deps table
SET @old='en.wikipedia.org';
SET @new='zh.chinapedia.org';
UPDATE `module_deps` SET `md_deps` = REPLACE( `md_deps`, @old, @new );
</pre>

# Extensions

* CategoryTree 动态导航分类结构	
* Math
* Scribunto 嵌入脚本语言(lua)到MediaWiki页面中的框架, 
* ParserFunctions 用逻辑函数加强解析器

{{#invoke:Infobox|infobox}}解析器依赖 Scribunto 和 ParserFunctions https://www.mediawiki.org/wiki/Manual:Importing_Wikipedia_infoboxes_tutorial

# Interface
* 编辑sidebar，https://zh.chinapedia.org/index.php?title=MediaWiki:Sidebar 参考 https://www.mediawiki.org/wiki/Manual:Interface/Sidebar
