## Installation
`npm install`

## Setup db and other configs
`./nodebb setup`

## install customized plugins
`cp -rf customized/* node_modules/`

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

