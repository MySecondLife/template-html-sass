# template-html-sass
### quick feedback when coding
### two file for build the project
- package.json
```
{
   "name" : "frontend-template",
   "version": "0.0.1",
   "description": "a boilerplate project for quick feedback when coding",
   "main": "index.js",
   "dependencies": {
     "browser-sync": "^2.18.13"
   },
   "devDependencies": {
     "gulp":"^3.9.1",
     "gulp-ruby-sass": "^2.1.1"
   },
   "scripts": {
     "test" :"echo \"Error: no test spexified\" && exit 1"
   },
   "keywords": [],
   "author":"wxh",
   "license": "ISC"
}
```
- gulpfile.js
```
var gulp = require("gulp");
var sass = require("gulp-ruby-sass");
var browserSync = require("browser-sync");
var reload = browserSync.reload;
gulp.task('sass',function(){
  return sass('app/scss/main.scss')
         .pipe(gulp.dest('app/css'))
         .pipe(reload({stream: true}));
})
gulp.task('serve',['sass'],function(){
  browserSync({
     server: {
       baseDir: 'app'
     }
  })
gulp.watch('app/scss/*.scss',['sass']);
gulp.watch('app/index.html').on('change',browserSync.reload);
})
```
### write your project in fload ./app
