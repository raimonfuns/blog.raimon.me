---
title: The Cheatsheets for Mocha
categories: Javascript
tags: [Mocha, Cheatsheets]
---

### Getting Started

    $ npm install -g mocha
    $ mocha // 默认test目录下的测试脚本


### Usage

    --recursive                             include sub directories
    --reporters                             display available reporters
    -w, --watch                             watch files for changes
    -b, --bail                              bail after first test failure
    --compilers <ext>:<module>,...          use the given module(s) to compile files
    -r, --require <name>                    require the given module

### ES6测试

运行测试之前，需要先用Babel转码。

	$ npm install babel-core babel-preset-es2015 --save-dev

让Babel对Iterator、Generator、Promise、Map、Set等全局对象转码

	$ npm install babel-polyfill --save

在项目目录下新建一个.babelrc配置文件

	{
		"presets": [ "es2015" ]
	}


运行mocha命令，加上`--compilers`

	$ ../node_modules/mocha/bin/mocha --compilers js:babel-core/register
