# api documentation for  [json (v9.0.6)](https://github.com/trentm/json#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-json.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-json) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-json.svg)](https://travis-ci.org/npmdoc/node-npmdoc-json)
#### a 'json' command for massaging and processing JSON on the command line

[![NPM](https://nodei.co/npm/json.png?downloads=true)](https://www.npmjs.com/package/json)

[![apidoc](https://npmdoc.github.io/node-npmdoc-json/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-json_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-json/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-json/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-json/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Trent Mick",
        "email": "trentm@gmail.com",
        "url": "http://trentm.com"
    },
    "bin": {
        "json": "./lib/json.js"
    },
    "bugs": {
        "url": "https://github.com/trentm/json/issues"
    },
    "contributors": [
        {
            "name": "Trent Mick",
            "email": "trentm@gmail.com",
            "url": "http://trentm.com"
        },
        {
            "name": "Yaniv Aknin",
            "url": "https://github.com/yaniv-aknin"
        },
        {
            "name": "Fred Kuo",
            "url": "https://github.com/fkuo"
        },
        {
            "name": "Bill Pijewski",
            "url": "https://github.com/pijewski"
        },
        {
            "name": "Isaac Schlueter",
            "url": "https://github.com/isaacs"
        },
        {
            "name": "Andrew O'Brien",
            "url": "https://github.com/AndrewO"
        },
        {
            "name": "Nate Fitch",
            "url": "https://github.com/nfitch"
        },
        {
            "name": "https://github.com/inator"
        },
        {
            "name": "Todd Whiteman",
            "url": "https://github.com/twhiteman"
        }
    ],
    "dependencies": {},
    "description": "a 'json' command for massaging and processing JSON on the command line",
    "devDependencies": {
        "ansidiff": "1.0",
        "async": "0.1.22",
        "ben": "0.0.x",
        "nodeunit": "0.8.x",
        "semver": "1.1.0",
        "uglify-js": "1.1.x"
    },
    "directories": {},
    "dist": {
        "shasum": "7972c2a5a48a42678db2730c7c2c4ee6e4e24585",
        "tarball": "https://registry.npmjs.org/json/-/json-9.0.6.tgz"
    },
    "engines": {
        "node": ">=0.10.0"
    },
    "gitHead": "a26e16a00ae4ab0f39f49a5ee3025ff48cf6eb32",
    "homepage": "https://github.com/trentm/json#readme",
    "keywords": [
        "json",
        "jsontool",
        "filter",
        "command",
        "shell"
    ],
    "main": "./lib/json.js",
    "maintainers": [
        {
            "name": "trentm",
            "email": "trentm@gmail.com"
        }
    ],
    "man": [
        "./man/man1/json.1"
    ],
    "name": "json",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/trentm/json.git"
    },
    "scripts": {
        "test": "make test"
    },
    "version": "9.0.6"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module json](#apidoc.module.json)
1.  [function <span class="apidocSignatureSpan">json.</span>getVersion ()](#apidoc.element.json.getVersion)
1.  [function <span class="apidocSignatureSpan">json.</span>lookupDatum (datum, lookup)](#apidoc.element.json.lookupDatum)
1.  [function <span class="apidocSignatureSpan">json.</span>main (argv)](#apidoc.element.json.main)
1.  [function <span class="apidocSignatureSpan">json.</span>parseLookup (lookup, lookupDelim)](#apidoc.element.json.parseLookup)
1.  [function <span class="apidocSignatureSpan">json.</span>printDatum (datum, opts, sep, alwaysPrintSep)](#apidoc.element.json.printDatum)



# <a name="apidoc.module.json"></a>[module json](#apidoc.module.json)

#### <a name="apidoc.element.json.getVersion"></a>[function <span class="apidocSignatureSpan">json.</span>getVersion ()](#apidoc.element.json.getVersion)
- description and source-code
```javascript
function getVersion() {
    return VERSION;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.json.lookupDatum"></a>[function <span class="apidocSignatureSpan">json.</span>lookupDatum (datum, lookup)](#apidoc.element.json.lookupDatum)
- description and source-code
```javascript
function lookupDatum(datum, lookup) {
    var d = datum;
    for (var i = 0; i < lookup.length; i++) {
        var bit = lookup[i];
        if (d === null) {
            return undefined;
        } else if (typeof (bit) === 'number' && bit < 0) {
            d = d[d.length + bit];
        } else {
            d = d[bit];
        }
        if (d === undefined) {
            return undefined;
        }
    }
    return d;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.json.main"></a>[function <span class="apidocSignatureSpan">json.</span>main (argv)](#apidoc.element.json.main)
- description and source-code
```javascript
function main(argv) {
    var opts;
    try {
        opts = parseArgv(argv);
    } catch (e) {
        warn('json: error: %s', e.message)
        return drainStdoutAndExit(1);
    }
    //warn(opts);
    if (opts.help) {
        printHelp();
        return;
    }
    if (opts.version) {
        if (opts.outputMode === OM_JSON) {
            var v = {
                version: getVersion(),
                author: 'Trent Mick',
                project: 'https://github.com/trentm/json'
            };
            console.log(JSON.stringify(v, null, opts.jsonIndent));
        } else {
            console.log('json ' + getVersion());
            console.log('written by Trent Mick');
            console.log('https://github.com/trentm/json');
        }
        return;
    }
    var lookupStrs = opts.args;

    // Prepare condition and execution funcs (and vm scripts) for -c/-e.
    var execVm = Boolean(process.env.JSON_EXEC &&
        process.env.JSON_EXEC === 'vm');
    var i;
    var condFuncs = [];
    if (!execVm) {
        for (i = 0; i < opts.condSnippets.length; i++) {
            condFuncs[i] = funcWithReturnFromSnippet(opts.condSnippets[i]);
        }
    }
    var condScripts = [];
    if (execVm) {
        for (i = 0; i < opts.condSnippets.length; i++) {
            condScripts[i] = vm.createScript(opts.condSnippets[i]);
        }
    }
    var cond = Boolean(condFuncs.length + condScripts.length);
    var exeFuncs = [];
    if (!execVm) {
        for (i = 0; i < opts.exeSnippets.length; i++) {
            exeFuncs[i] = new Function(opts.exeSnippets[i]);
        }
    }
    var exeScripts = [];
    if (execVm) {
        for (i = 0; i < opts.exeSnippets.length; i++) {
            exeScripts[i] = vm.createScript(opts.exeSnippets[i]);
        }
    }
    var exe = Boolean(exeFuncs.length + exeScripts.length);

    var lookups = lookupStrs.map(function (lookup) {
        return parseLookup(lookup, opts.lookupDelim);
    });

    if (opts.group && opts.array && opts.outputMode !== OM_JSON) {
        // streaming
        var chunker = chunkEmitter(opts);
        chunker.on('error', function (error) {
            warn('json: error: %s', err.message);
            return drainStdoutAndExit(1);
        });
        chunker.on('chunk', parseChunk);
    } else if (opts.inPlace) {
        assert.equal(opts.inputFiles.length, 1,
            'cannot handle more than one file with -I');
        getInput(opts, function (err, content, filename) {
            if (err) {
                warn('json: error: %s', err.message)
                return drainStdoutAndExit(1);
            }

            // Take off a leading HTTP header if any and pass it through.
            var headers = [];
            while (true) {
                if (content.slice(0, 5) === 'HTTP/') {
                    var index = content.indexOf('\r\n\r\n');
                    var sepLen = 4;
                    if (index == -1) {
                        index = content.indexOf('\n\n');
                        sepLen = 2;
                    }
                    if (index != -1) {
                        if (!opts.dropHeaders) {
                            headers.push(content.slice(0, index + sepLen));
                        }
                        var is100Continue = (
                            content.slice(0, 21) === 'HTTP/1.1 100 Continue');
                        content = content.slice(index + sepLen);
                        if (is100Continue) {
                            continue;
                        }
                    }
                }
                break;
            }
            parseChunk(content, undefined, filename, true, headers.join(''));
        });
    } else {
        // not streaming
        getInput(opts, function (err, buffer, filename) {
            if (err) {
                warn('json: error: %s', err.message)
                return drainStdoutAndExit(1);
            }
            // Take off a leading HTTP header if any and pass it through.
            while (true) {
                if (buffer.slice(0, 5) === 'HTTP/') { ...
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.json.parseLookup"></a>[function <span class="apidocSignatureSpan">json.</span>parseLookup (lookup, lookupDelim)](#apidoc.element.json.parseLookup)
- description and source-code
```javascript
function parseLookup(lookup, lookupDelim) {
    var debug = function () {};
    //var debug = console.warn;

    var bits = [];
    debug('\n*** ' + lookup + ' ***');

    bits = [];
    lookupDelim = lookupDelim || '.';
    var bit = '';
    var states = [null];
    var escaped = false;
    var ch = null;
    for (var i = 0; i < lookup.length; ++i) {
        var escaped = (!escaped && ch === '\\');
        var ch = lookup[i];
        debug('-- i=' + i + ', ch=' + JSON.stringify(ch) + ' escaped=' +
            JSON.stringify(escaped));
        debug('states: ' + JSON.stringify(states));

        if (escaped) {
            bit += ch;
            continue;
        }

        switch (states[states.length - 1]) {
        case null:
            switch (ch) {
            case '"':
            case '\'':
                states.push(ch);
                bit += ch;
                break;
            case '[':
                states.push(ch);
                if (bit !== '') {
                    bits.push(bit);
                    bit = ''
                }
                bit += ch;
                break;
            case lookupDelim:
                if (bit !== '') {
                    bits.push(bit);
                    bit = ''
                }
                break;
            default:
                bit += ch;
                break;
            }
            break;

        case '[':
            bit += ch;
            switch (ch) {
            case '"':
            case '\'':
            case '[':
                states.push(ch);
                break;
            case ']':
                states.pop();
                if (states[states.length - 1] === null) {
                    var evaled = vm.runInNewContext(
                        '(' + bit.slice(1, -1) + ')', {}, '<lookup>');
                    bits.push(evaled);
                    bit = ''
                }
                break;
            }
            break;

        case '"':
            bit += ch;
            switch (ch) {
            case '"':
                states.pop();
                if (states[states.length - 1] === null) {
                    bits.push(bit);
                    bit = ''
                }
                break;
            }
            break;

        case '\'':
            bit += ch;
            switch (ch) {
            case '\'':
                states.pop();
                if (states[states.length - 1] === null) {
                    bits.push(bit);
                    bit = ''
                }
                break;
            }
            break;
        }
        debug('bit: ' + JSON.stringify(bit));
        debug('bits: ' + JSON.stringify(bits));
    }

    if (bit !== '') {
        bits.push(bit);
        bit = ''
    }

    // Negative-intify: strings that are negative ints we change to a Number for
    // special handling in 'lookupDatum': Python-style negative array indexing.
    var negIntPat = /^-\d+$/;
    for (var i = 0; i < bits.length; i++) {
        if (negIntPat.test(bits[i])) {
            bits[i] = Number(bits[i]);
        }
    }

    debug(JSON.stringify(lookup) + ' -> ' + JSON.stringify(bits));
    return bits
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.json.printDatum"></a>[function <span class="apidocSignatureSpan">json.</span>printDatum (datum, opts, sep, alwaysPrintSep)](#apidoc.element.json.printDatum)
- description and source-code
```javascript
function printDatum(datum, opts, sep, alwaysPrintSep) {
    var output = stringifyDatum(datum, opts);
    if (output && output.length) {
        emit(output);
        emit(sep);
    } else if (alwaysPrintSep) {
        emit(sep);
    }
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
