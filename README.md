**Шпора по Bootstrap5.3.0 и его кастомизация из исходников  
Устанавливаем Node.js  
:white_check_mark:Команды для NPM установка модулей для Gulp**  
npm init  
npm i gulp  
npm i gulp-sass gulp-sourcemaps gulp-watch --SD  
nmp i (по package bs5)  
  
**:black_square_button:ОШИБКА gulp : Невозможно загрузить файл так как выполнение сценариев отключено в этой системе.**  
Открываем терминал от админа.  
Пишем и запускаем: Set-ExecutionPolicy RemoteSigned  
На вопрос отвечаем: A (Да для всех)  
  
**gulpfile.js**  
const gulp = require('gulp');  
const sass = require('gulp-sass');  
const sourcemaps = require('gulp-sourcemaps');  
const watch = require('gulp-watch');  
  
gulp.task('sass-compile', function() {  
  return gulp.src('./scss/**/*.scss')  
  .pipe(sourcemap.init())  
  .pipe(sass().on('error', sass.logError))  
  .pipe(sourcemaps.write('./'))  
  .pipe(gulp.dest('./css/'))  
})  
  
**:white_check_mark:Для изменения исходников Бутстрапа:**  
https://getbootstrap.com/docs/5.3/getting-started/contribute/#tooling-setup  
(в папке с бутстрапом):  
npm start	Компилирует CSS и JavaScript, создает документацию и запускает локальный сервер.  
npm run dist	Создает dist/каталог с скомпилированными файлами. Использует Sass , Autoprefixer и terser.  
npm test	Запускает тесты локально после запускаnpm run dist  
npm run docs-serve	Создает и запускает документацию локально.  
  
**:white_check_mark:setting.json (Live SASS Compiler)**  
"liveSassCompile.settings.forceBaseDirectory": "/scss/",  
"liveSassCompile.settings.generateMap": false,  
"liveSassCompile.settings.formats": [  
    {  
      "format": "expanded",  
      "extensionName": ".css",  
      "savePath": "~/../css/"  
    },  
    {  
      "format": "compressed",  
      "extensionName": ".min.css",  
      "savePath": "~/../css/"  
    }  
  ],  
"liveSassCompile.settings.showOutputWindowOn": "None",  
  
**:white_check_mark:Список поддерживаемых браузеров**  
Chrome >= 60  
Firefox >= 60  
Firefox ESR  
iOS >= 12  
Safari >= 12  
not Explorer <= 11  