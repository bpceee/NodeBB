### Installation
`npm install`

### Setup db and other configs
`./nodebb setup`

### install customized plugins
`cp -rf customized/* node_modules/`

### start server
`./nodebb start`

### activate plugins-write-api
Login in as admin, go to ADMIN CONTROL PANEL->EXTEND->PLUGINS, click Activate on nodebb-plugins-write-api

### get plugins-write-api token
1. refer to https://github.com/NodeBB/nodebb-plugin-write-api
2. set the token to Marksimos's config

### forbidden user registration
Login in as admin, go to ADMIN CONTROL PANEL->SETTINGS->USER
