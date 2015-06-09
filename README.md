coz
=====

Flexible generator, which makes your project clean and maintainable.

<!-- Badge start -->

[![Build Status][my_travis_badge_url]][my_travis_url]
[![Code Climate][my_codeclimate_badge_url]][my_codeclimate_url]
[![Code Coverage][my_codeclimate_coverage_badge_url]][my_codeclimate_url]
[![dependencies][my_gemnasium_badge_url]][my_gemnasium_url]
[![npm version][my_npm_budge_url]][my_npm_url]
[![Gratipay][my_gratipay_budge_url]][my_gratipay_url]

<!-- Badge end -->


<!-- Banner start -->

<a href="https://github.com/okunishinishi/coz#readme"><img style="height:px;" src="assets/images/coz-banner.png" height=""/></a>

<!-- Banner end -->


<!-- Table start -->

Table of Contents
-----
- [About coz](#01-about)
    - [What's this?](#01-about--whats-this)
    - [What for?](#01-about--what-for)
    - [Why this?](#01-about--why-this)
- [Getting started](#02-howto)
    - [Requirements](#02-howto--requirements)
    - [Install](#02-howto--install)
    - [Simple example](#02-howto--simple-example)
- [Specifications](#03-spec)
    - [Bud file specification.](#03-spec--bud-file-specification-)
- [Links](#09-links)
    - [Documents](#09-links--documents)
    - [Reports](#09-links--reports)
- [License](#10-license)
- [About this project](#11-project)
    - [Author](#11-project--author)
    - [Donation](#11-project--donation)

<!-- Table end -->


<!-- Sections start -->

<a name="01-about"></a>
About coz
------

<a name="01-about--whats-this"></a>
### What's this?

The basic idea of coz is that creating files from files.

Write a meta file called [.bud file][#spec-bud-spec] and run coz generates the magic.

<img style="height:256px;" src="assets/images/coz-outline.jpg" height="256">

<a name="01-about--what-for"></a>
### What for?

##### Automation.


##### No more meta programming.



<a name="01-about--why-this"></a>
### Why this?

##### - Because it's fast.
coz is lightweight engine and do nothing but rendering.

##### - Because it's extensible.
coz is an unopinionated provides ways to customize.

##### - Because it's flexible.
coz is attentive, like handling array or async operations, and guess a lot unless otherwise specified.



<a name="02-howto"></a>
Getting started
------

<a name="02-howto--requirements"></a>
### Requirements

+ [node.js][nodejs_url]


<a name="02-howto--install"></a>
### Install

```bash
$ npm install coz -g
```

<a name="02-howto--simple-example"></a>
### Simple example

Step01 **Configure bud file**

```Javascript
module.exports = {
    force: true,
    mode: '444',
    data: {
        entities: [
            {name: 'User'},
            {name: 'Machine'},
        ]
    }
}
```

Step02 **Prepare template**
```Javascript

{{#each entities}}
/** Entity for {{snakecase name}} */
module.exports = function {{pascalcase name}}Entity(){
};
{{/each}}

```

Step03 **Render file**
```bash
$ coz render .*.bud
```
<a name="03-spec"></a>
Specifications
---------

<a name="spec-bud-spec"></a>
<a name="03-spec--bud-file-specification-"></a>
### Bud file specification.

A bud contains file meta data like witch template to use, where to render it, what permission to give, and so on.

You can specify bud data by writing `.bud` file, which is actually a javascript file and could be written nodejs format.

```Javascript
module.exports = {
    path: 'my_file.txt',
    tmpl: '.my_file.txt.hbs',
    data: require('./.my_data')
}
```

And bud could be an array like:

```Javascript
module.exports = [
    {path: 'my_file.txt', /*...*/},
    {path: 'my_other_file.txt', /*...*/},
]
```

Or an async function.

```Javascript
module.exports = function(callback){
    myAsync(function(data){
        var error = null;
        callback(err, data);
    });
}
```

##### Supported properties

Name | Type | Description
----- | ----- | -----
engine | string&#124;object | Template compile function or name of function |
cwd | string | Working directory path |
data | object | Data to template render with |
done | boolean | Done to writeout or not |
mkdirp | boolean | Make parent directories if needed |
setup | object | Properties to set engine |
force | boolean | Should overwrite file when already exists, or not |
mode | string&#124;number | File permission |
path | string | Destination file path. If not provided, guess from bud file path |
src | string | Bud source file path |
tmpl | string&#124;function | Template file path or registered template name or template function |

<a name="09-links"></a>
Links
------

<a name="09-links--documents"></a>
### Documents

+ [API Guide][my_apiguide_url]

<a name="09-links--reports"></a>
### Reports

+ [Build Status @travis][my_travis_url]
+ [Analysis Result @codeclimate][my_codeclimate_url]
+ [Issues @github](https://github.com/okunishinishi/coz/issues)
+ [Coverage Report][my_coverage_url]

<a name="10-license"></a>
License
-------
This software is released under the [MIT License](https://raw.githubusercontent.com/okunishinishi/coz/master/LICENSE).

<a name="11-project"></a>
About this project
--------

<a name="11-project--author"></a>
### Author

+ [Taka Okunishi](http://okunishitaka.com)

<a name="11-project--donation"></a>
### Donation

Support this project and [others by okunishinishi][my_gratipay_url] via [gratipay][my_gratipay_url].

[<img src="https://cdn.rawgit.com/gratipay/gratipay-badge/2.3.0/dist/gratipay.svg" alt="Support via Gratipay"/>][my_gratipay_url]


<!-- Sections end -->


<!-- Links start -->

[nodejs_url]: http://nodejs.org/
[my_travis_url]: http://travis-ci.org/okunishinishi/coz
[my_travis_badge_url]: http://img.shields.io/travis/okunishinishi/coz.svg?style=flat
[my_codeclimate_url]: http://codeclimate.com/github/okunishinishi/coz
[my_codeclimate_badge_url]: http://img.shields.io/codeclimate/github/okunishinishi/coz.svg?style=flat
[my_codeclimate_coverage_badge_url]: http://img.shields.io/codeclimate/coverage/github/okunishinishi/coz.svg?style=flat
[my_apiguide_url]: http://okunishinishi.github.io/coz/apiguide/
[my_coverage_url]: http://okunishinishi.github.io/coz/coverage/lcov-report
[my_coverage_report_url]: http://okunishinishi.github.io/coz/coverage/lcov-report/
[my_gratipay_url]: https://gratipay.com/okunishinishi/
[my_gratipay_budge_url]: http://img.shields.io/gratipay/okunishinishi.svg?style=flat
[my_npm_url]: http://www.npmjs.org/package/coz
[my_npm_budge_url]: http://img.shields.io/npm/v/coz.svg?style=flat
[my_tag_url]: http://github.com/okunishinishi/coz/releases/tag/
[my_tag_badge_url]: http://img.shields.io/github/tag/okunishinishi/coz.svg?style=flat
[my_gemnasium_url]: http://gemnasium.com/okunishinishi/coz
[my_gemnasium_badge_url]: http://img.shields.io/gemnasium/okunishinishi/coz.svg?style=flat

<!-- Links end-->
