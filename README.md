### globby
---
https://github.com/sindresorhus/globby

```js
// test.js

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




```

```
```

```
```


