1. install gh-pages `npm i -D gh-pages`
2. In `package.json` and
```
"homepage": "http://velmyk.github.io/test",
```

```
"deploy": "gh-pages -d dist",
"predeploy": "npm run build"
```
1. webpack.config.js

```
new CopyPlugin([
    { from: 'src/404.html', to: '404.html' },
]),
```

```
publicPath: isProduction ? '/test' : '/',
```
3. Add `src/404.html` with
```
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <title>Single Page Apps for GitHub Pages</title>
  <script type="text/javascript">
    var segmentCount = 1;

    var l = window.location;
    l.replace(
      l.protocol + '//' + l.hostname + (l.port ? ':' + l.port : '') +
      l.pathname.split('/').slice(0, 1 + segmentCount).join('/') + '/?p=/' +
      l.pathname.slice(1).split('/').slice(segmentCount).join('/').replace(/&/g, '~and~') +
      (l.search ? '&q=' + l.search.slice(1).replace(/&/g, '~and~') : '') +
      l.hash
    );

  </script>
</head>

<body>
</body>

</html>
```
Code from `https://github.com/rafrex/spa-github-pages`

4. Add to `src/index.html`
```
<script type="text/javascript">
        (function (l) {
            if (l.search) {
                var q = {};
                l.search.slice(1).split('&').forEach(function (v) {
                    var a = v.split('=');
                    q[a[0]] = a.slice(1).join('=').replace(/~and~/g, '&');
                });
                if (q.p !== undefined) {
                    window.history.replaceState(null, null,
                        l.pathname.slice(0, -1) + (q.p || '') +
                        (q.q ? ('?' + q.q) : '') +
                        l.hash
                    );
                }
            }
        }(window.location))
    </script>
```

5. Add `basename` to `BrowserRouter`
```
<BrowserRouter basename={process.env.NODE_ENV === 'production' ? '/test' : '/'}>
```


