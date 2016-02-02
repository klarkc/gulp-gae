gulp-gae
========

# Installation
`npm install gulp-gae --save-dev`

# Usage
```javascript
var gulp = require('gulp'),
  gae = require('gulp-gae');

// Optional google app engine directory, if omitted the built-in app engine library will be used
// var gae_dir = '/home/user/google-appengine';

// Optional options variable to be used into spawn function
// var options = {cwd: '/home/user/project', env: 'NODE_ENV=test'}

gulp.task('gae-serve', function () {
  gulp.src('app/app.yaml')
    .pipe(gae('dev_appserver.py', [], {
      port: 8081,
      host: '0.0.0.0',
      admin_port: 8001,
      admin_host: '0.0.0.0'
    }/*, gae_dir, options */));
});


gulp.task('gae-deploy', function () {
  gulp.src('app/app.yaml')
    .pipe(gae('appcfg.py', ['update'], {
      version: 'dev',
      oauth2: undefined // for value-less parameters
    }/*, gae_dir, options */));
});


gulp.task('default', ['gae-serve']);

```

For a working example see the `test` folder.
