---
title: 单元测试之常用的ES6语法
categories: Javascript
tags: [ES6, 单元测试]
---

之前粗略的看过[ECMAScript 6入门][1]教程，对于ES6的语法有了大概的了解，比如箭头函数，let和const声明，设置函数参数的默认值等等，一直没有系统地学习，今天抽空阅读一遍[es6-cheatsheet][2]，针对常用的语法写了单元测试，以加强对ES6语法的理解，下面是测试代码和测试结果。

## 测试代码

``` Javascript
'use strict'

var chai = require('chai');
chai.should()

describe('var versus let / const', function () {
  it('let statements are not hoisted to the top of their enclosing scope', function () {
    let snack = 'Meow Mix';

    function getFood(food){
      if (food) {
        let snack = 'Friskies';
        return snack;
      }
      return snack;
    }

    getFood(false).should.be.equal('Meow Mix');
  });
});

describe('Replacing IIFEs with Blocks', function () {
  it('create block-based scopes', function () {
    let food = 'noodle';
    {
      let food = 'Meow Mix';
    }
    food.should.be.equal('noodle');
  });
});

describe('Arrow Functions', function () {
  it('preserve the lexical value of this', function () {
    function Person(name) {
      this.name = name;
    }

    Person.prototype.prefixName = function (arr) {
      return arr.map(character => this.name + character);
    }

    var person = new Person();
    person.name = 'prefix-';
    var resultArr = person.prefixName(['raimon', 'raimonfuns']);

    resultArr.length.should.be.equal(2);
    resultArr[0].should.be.equal('prefix-raimon');
  });

  describe('Strings', function () {
    it('.includes()', function () {
      const string = 'food';
      const substring = 'foo';

      string.includes(substring).should.be.equal(true);
    });

    it('.repeat()', function () {
      'raimon'.repeat(3).should.be.equal('raimonraimonraimon');
    });
  });

  describe('Template Literals', function () {
    it('do not need to be escaped anymore', function () {
      let test = `This string contains "double quotes" which don't need to be escaped anymore.`;

      test.should.be.equal("This string contains \"double quotes\" which don't need to be escaped anymore.");
    });

    it('interpolation', function () {
      const name = 'raimon';
      const age = 24;

      let test = `My cat is named ${name} and is ${age} years old.`;
      test.should.be.equal('My cat is named raimon and is 24 years old.');
    });

    it('expressions', function () {
      let string = 'nba';
      let test = `${string.toUpperCase()}, where amazing happens`;

      test.should.be.equal('NBA, where amazing happens');
    });
  });

  describe('Destructuring', function () {
    it('Destructuring Arrays', function () {
      let [a, b] = [1, 2];

      a.should.be.equal(1);
      b.should.be.equal(2);
    });

    it('Destructuring Objects', function () {
      let luke = {occupation: 'jeki', father: 'anakin'};
      let {occupation, father} = luke;

      occupation.should.be.equal('jeki');
      father.should.be.equal('anakin');
    });
  });

  describe('Parameters', function () {
    it('Default Parameters', function () {
      function addTwoNumbers(x=0, y=0) {
        return x + y;
      }

      addTwoNumbers(2, 4).should.be.equal(6);
      addTwoNumbers(2).should.be.equal(2);
      addTwoNumbers().should.be.equal(0);
    });

    it('Rest Parameters', function () {
      function joinArguments(...args) {
        return args.join('');
      }

      joinArguments('a', 'b').should.be.equal('ab');
    });

    it('Named Parameters', function () {
      function initializeCanvas({ height=600, width=400, lineStroke='black' }) {
        return 'height:' + height + ';' + 'width:' + width + ';' + 'lineStroke:' + lineStroke;
      }

      initializeCanvas({height: 100, width: 100, lineStroke: 'black'}).should.be.equal('height:100;width:100;lineStroke:black');
      initializeCanvas({height: 100, lineStroke: 'black'}).should.be.equal('height:100;width:400;lineStroke:black');
    });
  });

  describe('Spread Operator', function () {
    it('pass an array of values to be used as parameters to a function', function () {
      Math.max(...[1, 100, 9001, -32]).should.be.equal(9001);
    });

    it('concat array literals', function () {
      let cities = ['San Francisco', 'Los Angeles'];
      let places = ['Miami', ...cities, 'Chicago'];

      places.length.should.be.equal(4);
      places[1].should.be.equal('San Francisco');
    });
  });

  describe('Maps', function () {
    it('set, get, search', function () {
      let map = new Map();
      map.set('name', 'david');

      map.get('name').should.be.equal('david');
      map.has('name').should.be.equal(true);
    });

    it('use any type as a key', function () {
      var typeStr = '';
      let map = new Map([
        ['name', 'david'],
        [true, 'false'],
        [1, 'one'],
        [{}, 'object'],
        [function () {}, 'function']
      ]);

      for (let key of map.keys()) {
        typeStr += typeof key + '|';
      }

      typeStr.should.be.equal('string|boolean|number|object|function|');
    });

    it('.entries()', function () {
      var resultStr = '';
      let map = new Map([
        ['name', 'david'],
        ['age', '24']
      ]);

      for (let [key, value] of map.entries()) {
        resultStr += key + ': ' + value + '|';
      }

      resultStr.should.be.equal('name: david|age: 24|');
    });
  });
});

```

## 测试结果
![unit test result][image-1]

[1]:	http://es6.ruanyifeng.com/
[2]:	https://github.com/DrkSephy/es6-cheatsheet

[image-1]:	http://chuantu.biz/t5/14/1467467341x2918528194.png