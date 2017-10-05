##### SASS OF CONTENTS

- [Sass & Gulp](https://codepen.io/mimoduo/post/sass-cheat-sheet#sass-and-gulp-2)
- [Variables](https://codepen.io/mimoduo/post/sass-cheat-sheet#variables-3)
- [Interpolation](https://codepen.io/mimoduo/post/sass-cheat-sheet#interpolation-4)
- [Math](https://codepen.io/mimoduo/post/sass-cheat-sheet#math-5)
- [Nesting](https://codepen.io/mimoduo/post/sass-cheat-sheet#nesting-6)
- [Conditionals](https://codepen.io/mimoduo/post/sass-cheat-sheet#conditionals-7)
- [Mixins](https://codepen.io/mimoduo/post/sass-cheat-sheet#mixins-8)
- [For Loops](https://codepen.io/mimoduo/post/sass-cheat-sheet#for-loops-9)
- [Each](https://codepen.io/mimoduo/post/sass-cheat-sheet#each-10)

#### [#](https://codepen.io/mimoduo/post/sass-cheat-sheet#sass-and-gulp-2)Sass & Gulp

vargulp=require('gulp'),  
sass=require('gulp-sass'),  
sassGlob=require('gulp-sass-glob'),  
postcss=require('gulp-postcss'),  
cssnano=require('gulp-cssnano'),  
extReplace=require('gulp-ext-replace');  
  
gulp.task('sass', function() {  
  
returngulp.src('sass/site.scss')  
    .pipe(sassGlob())  
    .pipe(sass().on('error', sass.logError))  
    .pipe(gulp.dest('css'))  
    .pipe(postcss([  
require('autoprefixer')({  
browsers: ['&gt; 1%'],  
cascade: false  
      })  
    ]))  
    .pipe(cssnano())  
    .pipe(extReplace('.min.css'))  
    .pipe(gulp.dest('css'));  
  
});  

#### [#](https://codepen.io/mimoduo/post/sass-cheat-sheet#variables-3)Variables

$color:rgba(#aae, .25);  
$number:20;  
$string:'JambaJuice';  
$list:'Item', 'Item';  
$boolean:true;  
  
$nestedList:(  
('Berry', 80),  
('Troup', 100)  
);  
  
$map:(  
Bubble:'Pop',  
Trouble:'Maker'  
);  

#### [#](https://codepen.io/mimoduo/post/sass-cheat-sheet#interpolation-4)Interpolation

$theme:'jazz';  
$moogle:8;  
$lg:'(min-width: '+900px+')';  
  
.theme_#{$theme}{  
font-size:$moogle#{em};  
  
@media#{$lg}{}  
}  

#### [#](https://codepen.io/mimoduo/post/sass-cheat-sheet#math-5)Math

.bombay{  
margin:random(100)*1%0;  
padding:$chocobo*2em;  
line-height:(24/16);  
}  

#### [#](https://codepen.io/mimoduo/post/sass-cheat-sheet#nesting-6)Nesting

// Input  
.straddle{  
  
@mediaprint{}  
  
  &:focus,  
  &:hover{}  
  
  &[attr*="wiggle"] {}  
  
@at-root.track{}  
}  

// Output  
.straddle{}  
  
@mediaprint{  
.straddle{}  
}  
  
.straddle:focus,  
.straddle:hover{}  
  
.straddle[attr*="wiggle"] {}  
  
.track{}  

#### [#](https://codepen.io/mimoduo/post/sass-cheat-sheet#conditionals-7)Conditionals

.ballin{  
$space:'power';  
  
@if$space=='jam'{  
transform:scale(1, -1);  
}@else if$space=='power'{  
transform:scale(-1, 1);  
}@else{  
transform:scale(0, 0);  
}  
  
$doodle:20;  
  
@if$doodle&lt;0{  
background:#eaa;  
}@else if$doodle==0{  
background:#aea;  
}@else{  
background:#aae;  
}  
}  

#### [#](https://codepen.io/mimoduo/post/sass-cheat-sheet#mixins-8)Mixins

@mixinturbo($background, $color:'#afa'){  
background:$background;  
color:$color;  
}  
  
.speeder{  
@includeturbo(#000);  
}  

#### [#](https://codepen.io/mimoduo/post/sass-cheat-sheet#for-loops-9)For Loops

.zazzle{  
  
@for$ifrom1through20{  
  
    &:nth-child(#{$i}){  
background:hsl((255/20)*$i, 90, 60);  
}  
}  
}  

#### [#](https://codepen.io/mimoduo/post/sass-cheat-sheet#each-10)Each

$theme-colors:(  
(blue, $blue),  
(mint, $mint)  
);  
  
@each$label, $colorin$theme-colors{  
  
.theme-#{$label} & {  
color:$color;  
}  
}  
  
$social-themes:(  
facebook:#3b5998,  
twitter:#55acee  
);  
  
@each$label, $colorin$social-themes{  
  
.theme-#{$label}{  
color:$color;  
}  
}