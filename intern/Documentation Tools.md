---
title: Documentation Tools and Installation
description: 
permalink: 
aliases: 
draft: true
shared: false
date: 2024-10-01
tags: 
---
# Documentation Tools

## Obsidian 

For each documentalist:

* If you write hardly any documentation, you can use Visual Studio or Visual Studio Code, as long as you comply to the standard maintained in the document;
* If you write more than a bit and need to maintain links, it is recommended to use Obsidian.

Follow standard installation on [Download - Obsidian](https://obsidian.md/download).
It works without a license, but please request one from our IT Administration.

Please don't change the Theme without consulting the team, since the settings are stored in the Vault.
### Obsidian Plugins

Both Core and [Community](https://obsidian.md/community) plugins are used. When you open the documentation Vault they are loaded as well. You need to provide community plugins permission to run. Please don't install new plugins without consulting the team.

#### DataView Plugin

This plugin is used to have Vault **global** variables for release dependent information. See also [[../templates/GlobalVariables|GlobalVariables]].

This one is very important to combine Methods (e.g. Calls in [[../content/8 API/NetCon API Introduction|NetCon API Introduction]] or Expressions) with their Parameters and Results.

You can read more on https://blacksmithgu.github.io/obsidian-dataview/reference/sources/
#### Enveloppe Plugin

It is very important to the the FileTree variable to `Obsidian-path` since also in Quartz it has been set this way. Otherwise, you path-links will be broken. This the default for v4, out of the box the setting is for v3. Don't change it, please.

See also https://enveloppe.github.io/ and for its settings https://enveloppe.github.io/Settings/Github.

Background discussion as to the why of this, see https://github.com/blacksmithgu/obsidian-dataview/issues/42.

For the moment, changes are published to https://kenkor.github.com/
#### TemplateR Plugin

Note this is not the Core plugin, but the community one, that has an `R` at the end. 

Create a new note with `Ctrl-N` (unfortunately it goes to the bottom), or with `right-mouse-click on folder` which makes it go into the folder your select.

After typing the page title, only then apply the template with `Alt-E`. This way, the properties are set the right way; otherwise you have to maintain them manually.

* As a default, use the [[../templates/NetConHelpPage|NetConHelpPage]]
* For API calls parameter or results use [[../templates/NetConApiParameterPage|NetConApiParameterPage]] or [[../templates/NetConApiResultPage|NetConApiResultPage]], as this will add the right tags
* For expressions parameter or results use [[../templates/NetConExpressionParameterPage|NetConExpressionParameterPage]] or [[../templates/NetConExpressionResultPage|NetConExpressionResultPage]], as this will add the right tags

The tags are then used on the API call or expressions pages to link to them.
## Quartz

Quartz is a tool to publish the Obsidian (and other MarkDown) vaults to the internet. See https://quartz.jzhao.xyz/.

This should be a central installation, preferably on a server. You can follow a video with the installation steps: https://www.youtube.com/watch?v=6s6DT1yN4dw&t=213s.

Below are the instruction for installating Quartz.
### Quartz 1: NVM - Node Version Manager

About https://github.com/nvm-sh/nvm/?tab=readme-ov-file

DON'T use: 

	sudo apt install npm

which will install and old unusable version
If you did, you need to uninstall and clean it:

	sudo apt remove npm
	sudo apt-get remove nodejs ^node-* nodejs-*
	sudo apt-get autoremove
	sudo apt-get clean

Install
https://host-world.com/how-to-install-nvm-on-ubuntu-step-by-step-tutorial
find latest link at:

	curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.2/install.sh | bash
	
Close terminal
	
	source ~/.bashrc
	nvm –version

After that you must create NPM:

	nvm i
	nvm install node
	nvm use node
	
And upgrade:
	
	npm install npm -g
	npm audit fix
	
DON'T use: 

	sudo apt install npm
	
which will install and old unusable version

### Quartz 2: Continued

Installation commands:
	
	git clone https://github.com/jackyzha0/quartz.git
	cd quartz
	npm i
	npx quartz create 
	git remote rm origin
	git remote add origin git@github.com:KenKor/NetCon
	npx quartz sync --no-pull
	ssh-add ~/.ssh/id_ed25519

Quartz will add the layout and the navigation functions:

* The layout can be customized in `custome.scss` according to the `sass` standard.
* `quartz.layout.ts` provides the footer information, amongst others.
* `quartz.condif.ts` provides font and color information.

Note the Quartz installation is kept in different git than the documention content. For the moment that is `git@github.com:KenKor/NetCon`.
To sync you can use:

	npx quartz sync

The sync will also publish the contents on the internet in https://kenkor.github.io/NetCon/.

It has a nice local test and previous mode:

	npx quartz build --serve

### To verify:

Upgrade:
	
	nvm --version
	sudo npm install npm -g


```
sudo apt-get remove nodejs ^node-* nodejs-*
sudo apt-get autoremove
sudo apt-get clean
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install nodejs
```
