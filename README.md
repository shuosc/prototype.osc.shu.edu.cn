# 上海大学开源社区官网文档
本站点采用`Hexo`构建，主题`shuosc`为自主开发，具有`PC端`和`移动端`多端适应能力、代码高亮、Disqus评论，以下为本站点相关的几点说明：

### 自定义依赖包
- hexo-abbrlink
- hexo-deploy-git
- hexo-generator-feed
- hexo-generator-recent

### 功能说明
功能 | 路径
 :--: | :--: 
主页静态配置管理 | `/themes/shuosc/source/index.json`
文章`md`文件 | `/source/_posts`
所有文章 | `/archives`
最近十篇文章 | `/recent.json`
文章订阅 | `/atom.xml`
文章默认模板 | `/scaffolds/post.md`

### 配置说明
主页具有以下配置属性：

大类名 | 项属性 | 含义
 :--: | :--: | :--:
`menu` | `name`、`link` | 顶部菜单
`team` | `img_url`、`name`、`description` | 团队成员
`activity` | `title`、`reporter` 、`time`、`address`| 活动预告
`links` | `name`、`link` | 底部快速链接

文章默认具有以下配置属性：

属性名 | 含义 | 默认
 :--: | :--: | :---:
title | 文章标题 | `与源文件名一致`
author | 作者| `shuosc`
toc | 是否开启目录 | `true`
tags | 文章标签 | `空`
categories | 文章分类 | `空`
abbrlink | 文章唯一链接 | `自动生成`
date | 文章生成时间 | `自动生成`

### 使用说明
编辑内容的主机要求具有`Nodejs`环境，如无可参照[附录A](#附录A)中说明安装

```shell
git clone ssh://git@git.shuosc.org:8000/shuosc/osc.shu.edu.cn
npm install && npm install -g hexo-cli
hexo new t1  //生成新文章t1
编辑`/source/_posts/t1.md`  //支持常用Markdown语法
hexo server --debug  //调试状态，边编辑边查看
git status && git add -A
git commit -m 'update content'
git push origin master
```

如果需要同时同步`gitlab`和`github`，请在克隆之后立刻执行以下命令

```shell
git remote add github git@github.com:shuopensourcecommunity/osc.shu.edu.cn.git
```

在`push`时最后再加一步：`git push github master`即可同步到`github`的`master`分支
> - 如需删除文章，直接在目录`/source/_posts`删除源文件即可
> - `hexo generate -d`可以直接部署到`github`的`gh-pages`分支，不过正式`push`到`master`分支之前就需要执行`hexo clean`将刚才生成的`public`目录清除

# 附录A

## windows环境安装Nodejs
[nodejs在windows下的安装配置(使用NVM的方式)](http://blog.csdn.net/tyro_java/article/details/51232458)

## Linux环境安装Nodejs

```shell
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
sudo tee -a ~/.zshrc << EOF
NVM_NODEJS_ORG_MIRROR=http://npm.taobao.org/mirrors/node
EOF
nvm install node
npm install -g cnpm --registry=https://registry.npm.shuosc.org
cnpm config set registry https://registry.npm.shuosc.org
```

## Mac环境安装Nodejs

```shell
brew install node
npm install -g cnpm --registry=https://registry.npm.shuosc.org
cnpm config set registry https://registry.npm.shuosc.org
```