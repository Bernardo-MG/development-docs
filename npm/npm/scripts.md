# Scripts

```text
{
   "scripts": {
      "validate-js": "./node_modules/.bin/jshint ./src/static/js/* --config .jshintrc"
   }
}
```

```text
npm run validate-js
```

## Chaining Scripts

```text
{
   "scripts": {
      "copy-bootstrap": "cpx \"node_modules/bootstrap/dist/js/*.js\" src/static/lib/bootstrap/js",
      "copy-bootswatch": "cpx \"node_modules/bootswatch/readable/*.css\" src/static/lib/bootswatch/readable",
      "copy-fontawesome": "cpx \"node_modules/font-awesome/**/*\" src/static/lib/font-awesome",
      "copy-html5shiv": "cpx \"node_modules/html5shiv/dist/*.css\" src/static/lib/html5shiv",
      "copy-jquery": "cpx \"node_modules/jquery/dist/*.js\" src/static/lib/jquery",
      "copy-all": "run-s copy-bootstrap copy-bootswatch copy-fontawesome copy-html5shiv copy-jquery"
   },
   "devDependencies": {
      "npm-run-all": "~4.1.5"
   }
}
```

