## Proof General－－证明助手的通用的Emacs接口

### 什么是Proof General

*Proof General*是证明助手（交互式定理证明器）的通用前端，基于[Emacs](https://www．emacswiki．org/emacs/SiteMap)的自定义功能．Proof General由[爱丁堡大学](http://www．ed．ac．uk/)的 [LFCS](http://wcms．inf．ed．ac．uk/lfcs/) 及来自互联网的其它人员合力开发．构建于[GNU GeneralPublic License](http://www．gnu．org/licenses/gpl-2．0．html)之下．主管人员是 [DavidAspinall](http://homepages．inf．ed．ac．uk/da)，其它构建者在 [AUTHORS](https://proofgeneral．github．io/AUTHORS)文件中列出．

- Proof General对Coq证明助手提供全面的支持，作者：Healfdene Goguen， Patrick Loiseleur， David Aspinall， 和 [Pierre Courtieu](http://cedric．cnam．fr/%7Ecourtiep/)．
- 也支持Isabelle Proof General（更新至2014），作者：[David Aspinall](http://homepages．inf．ed．ac．uk/da) 和[Makarius](http://sketis．net/)．
- 支持Phox Proof General，作者：[Christophe Raffalli](http://www．lama．univ-savoie．fr/%7ERAFFALLI)， Paul Roziere and Jean-Roch Sotty．
- LEGO Proof General，作者： [LEGO](http://www．dcs．ed．ac．uk/home/lego)
- HOL Proof General作者： [HOL98/HOL4](https://hol-theorem-prover．org/)
- ACL2 Proof General，作者： [ACL2](http://www．cs．utexas．edu/users/moore/acl2)

这些例子也许并不完整，在最新的版本中．

Proof General准备个性化成一个全新的证明助手．它可以很容易地对工作提供基本支持．[提供了完全配置文档](https://github.com/ProofGeneral/PG/releases/download/v4.4/PG-adapting.pdf)．我们欢迎对Proof General进行支持和拓展，如果你计划了一个主要的工作，请联系我们．

如果准备支持（或应用）一个新的证明器，请阅读Proof General的[开发架构](http://proofgeneral.inf.ed.ac.uk/kit) ．思想是证明助手需要支持PGIP，一个一致的交互协议，而不是使用系统声明是的自定义接口．使用PCIP的主要的研究是一个[Eclipse](http://www.eclipse.org)插件，虽然Emacs Proof General支持一些PGIP配置．

### 快速安装指导

删除旧版本的Proof General，然后从github上下载和安装新的发布：

> ```b
> git clone https://github.com/ProofGeneral/PG ~/.emacs.d/lisp/PG
> cd ~/.emacs.d/lisp/PG
> make
> ```

然后添加如下至.emacs文件：

> ```lisp
> ;; Open .v files with Proof General's Coq mode
> (load "~/.emacs.d/lisp/PG/generic/proof-site")
> ```

如果Proof General抱怨版本不匹配，请确认shell中的emacs是你常用的emacs，否则将Emacs添加入PATH中，并重新make一遍．特别地，在macOS上，你可能需要这样：

> ```
> make clean; make EMACS=/Applications/Emacs.app/Contents/MacOS/Emacs
> ```

更多信息，请看github上的文件 [README](https://github.com/ProofGeneral/PG#more-info)
和 [INSTALL](https://github.com/ProofGeneral/PG/blob/master/INSTALL)．