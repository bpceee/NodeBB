假设nodeBB配置在二级域名下，安装于次服务器中。

# NodeBB 与自己的网站 集成 注册/登录/修改密码/退出登录功能

## Installation 安装NodeBB
`sudo npm install`

## Setup db and other configs (run mongodb first)
`./nodebb setup`

## install customized plugins  (去掉了修改密码界面)
`cp -rf customized/* node_modules/`


### customized theme 说明：
1. nodebb-theme-persona
    * 去掉了修改密码界面



## start server
`./nodebb start`


## setting
Login in as admin

#### activate plugins-write-api  激活 nodebb-plugins-write-api
ADMIN CONTROL PANEL->EXTEND->PLUGINS, click Activate on nodebb-plugins-write-api
进入管理员界面, 点击 左边的EXTEND菜单 里面的 PLUGINS 子菜单. 激活 nodebb-plugin-write-api

然后重启NodeBB程序.

#### get plugins-write-api token  获取 插件的token
1. refer to https://github.com/NodeBB/nodebb-plugin-write-api  [相关资源链接](https://github.com/NodeBB/nodebb-plugin-write-api)
2. set the token to plugins-write-api user(your main site)

点击管理员左边 菜单 Write API, 生成token, 并把该token放到你主站里面的设置文件中.


#### setting as admin
1. ADMIN CONTROL PANEL->SETTINGS->USER, disallow registration, disallow account deletion
2. ADMIN CONTROL PANEL->APPEARANCE->THEMES, choose Persona THEMES

#### set cookie session
ADMIN CONTROL PANEL->SETTINGS->ADVANCED, DOMAIN SETTINGS, set session cookie to .yourdomainname.com (例子：.test.com)


## update log  文件修改记录
1. update src/user/profile.js, add  User.resetPassword function
2. customize nodebb-theme-persona plugin, forbidden user password/name/email update
3. customize nodebb-plugin-write-api, refer to https://github.com/bpceee/nodebb-plugin-write-api



# 主站设置

## 测试环境
### 设置/etc/hosts
例子：

    127.0.0.1       test.com      #主站
    127.0.0.1       bbs.test.com  #bbs二级站

    127.0.0.1	hcd.com  #主站
    127.0.0.1	community.hcd.com  #bbs二级站

### config.js
例子：

    config.bbsService = 'http://bbs.test.com:4567/';
    config.bbsToken = '02763566-35f4-48f8-8cb4-8322554e53d0';

### api/controllers/user/authentication.js
在所有process.env.NODE_ENV === 'ken' 处加上自己的env

## 生产环境

建议设置主服务器的/etc/hosts文件, 使NodeBB的所在的二级域名指向NodeBB所在机器的内网IP (安全，快速。。)