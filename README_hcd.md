假设nodeBB配置在二级域名下，安装于次服务器中。

## Installation
`npm install`

## Setup db and other configs
`./nodebb setup`

## install customized plugins
`cp -rf customized/* node_modules/`

### customized plugin说明：
1. nodebb-theme-persona
    * 去掉了修改密码界面

## start server
`./nodebb start`

## setting
Login in as admin

#### activate plugins-write-api
ADMIN CONTROL PANEL->EXTEND->PLUGINS, click Activate on nodebb-plugins-write-api

#### get plugins-write-api token
1. refer to https://github.com/NodeBB/nodebb-plugin-write-api
2. set the token to plugins-write-api user(your main site)

#### setting as admin
1. ADMIN CONTROL PANEL->SETTINGS->USER, disallow registration, disallow acount deletion
2. ADMIN CONTROL PANEL->APPEARANCE->THEMES, chose Persona

#### set cookie session
ADMIN CONTROL PANEL->SETTINGS->ADVANCED, DOMAIN SETTINGS, set session cookie to .yourdomainname.com


## 设置主服务器的/etc/hosts文件，使NodeBB的所在的二级域名指向NodeBB所在机器的内网IP (安全，快速。。)


## update log
1. update src/user/profile.js, add  User.resetPassword function
2. customize nodebb-theme-persona plugin, forbidden user password/name/email update
3. customize nodebb-plugin-write-api, refer to https://github.com/bpceee/nodebb-plugin-write-api