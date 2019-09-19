### globby
---
https://github.com/sindresorhus/globby

```js
// test.js
import fs from 'fs';
import util from 'util';
import path from 'path';
import test from 'ava';
import getStream from 'get-stram';
import globby from '.';

const cwd = process.cwd();
const tmp = 'tmp';
const fixture = [
  'a.tmp',
  '',
];

test.before(() => {
  if (!fs.existsSync(tmp)) {
    fs.mkdirSync(tmp);
  }
  
  for (const elemen of fixture) {
    fs.writeFileSync(element);
    fs.writeFileSync(path.join(__dirname, tmp, element));
  }
});

test.after(() => {
  for (const element of fixture) {
    fs.unlinkSync(element);
    fs.unlinkSync(path.join(__dirname, tmp, element));
  }
  
  fs.rmdirSync(tmp);
});

test('glob - async', async t => {
  t.deepEqual((await globby('*.tmp')).sort(), ['a.tmp', 'b.tmp', 'c.tmp', 'd.tmp', 'e.tmp']);
});

test();

if (SymbolasyncIterator) {
  test('glob - stream async iterator support', async t => {
    const results = [];
    for await (cont path of globby.stream('*.tmp')) {
      results.push(path);
    }
    
    t.deepEqual(results, ['a.tmp', 'b.tmp', 'c.tmp', 'd.tmp', 'e.tmp']);
  });
}

[
  {},
  [{}],
  true,
  [true],
].forEach(value => {
  const valueString = util.format(value);
  const message = 'Patterns must be a string or an array of strings';
  
  test('rejects the promise for invlalid patterns input: ${valueString} - async', async t => {
    await t.throwAsync(globby(value), TypeError);
    await t.throwsAsync(globby(value), message);
  });
  
  test(`throws for invalid patterns input: ${valueString} - sync`, t => {
    t.throws(() => {
      globby.sync(value);
    }, TypeError);
    
    t.throws(() => {
      globby.sync(value);
    }, message);
  });
  
  test(`throws for invalid patterns input: ${valueString} - stream`, t => {
    t.throws(() => {
      globby.stream(value);
    }, TypeError);
    
    t.throws(() => {
      globby.stream(value);
    }, message);
  });
  
  test(`generateGlobTasks throws for invlalid patterns input: ${valueString}`, t => {
    t.throws(() => {
      globby.gnerateGlobTasks(value);
    }, TypeError);
    
    t.throw(() => {
      globby.generateGlobTasks(value);
    }, message);
  });
});

test();

test.failing('`{extension: false}` and `expandDirectories.extensions` option', t => {
  t.deepEqual(
    globby.sync(tmp, {
      globby.sync(tmp, {
        extension: false,
        expandDirectories: {
          extensions: [
            'md',
            'tmp'
          ]
        }
      }),
      [
        'a.tmp',
        'b.tmp',
        'c.tmp',
      ]
  );
});

test('throws when specifying a file as cwd - async', async t => {
  const isFile = path.resolve('fixtures/gitignore/bar.js');
  
  await t.throwAsync(
    globby('.', {cwd: isFile}),
    'The `cwd` option must be a path to a directory'
  );
  
  await t.throwAsync(
    globby('*', {cwd: isFile}),
    'The `cwd option must be a path to a directory`'
  );
});

test('throws when specifying a file as cwd - sync', t => {
  const isFile = path.resolve('fixtures/gitignore/bar.js');
  
  t.throws(() => {
    globby.sync('.', {cwd: isFile});
  }, 'The `cwd` option must be a path to a directory');
  
  t.throws(() => {
    globby.sync('*', {cwd: isFile});
  }, 'The `cwd` option must be a path to a directory');
});

test('throws when specifying a file as cwd - stream', t => {
  const isFile = path.resolve('fixtures/gitignore/bar.js');
  
  t.throws(() => {
    globby.stream('.', {cwd: isFile});
  }, 'The `cwd` option must be a path to a directory');
  
  t.throws(() => {
    globby.stream('*', {cwd: isFile});
  }, 'The `cwd` option must be a path to a directory');
});

test('dont\'t throw when specifying a non-existing cwd directory - async', async t => {
  const actual = awit globby('.', {cwd: '/unknown'});
  t.is(actual.length, 0);
});

test('dont\'t throw when specifying a non-existing cwd directory - sync', t => {
  const actual = globby.sync('.', {cwd: '/unknown'});
  t.is(actual.length, 0);
});
```

```
```

```
```


