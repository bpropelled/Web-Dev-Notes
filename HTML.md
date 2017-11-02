# HTML

## Difference between span and div
### What is the difference between a span and div tag?

A div has a default CSS display value of block which makes it take up all the available horizontal space. A span has a default display value of inline so it will take up only the horizontal space required by whatever it contains. You could change the display value of any element, making a span display:block or a div display:inline if for some reason you can't choose the element that has your desired layout properties in the first place.

## Don't let synchronous scripts get int he way of html loading by addding async tag
```html
<script src="async-example.js" async></script>
```
## Knockout Text
```html
<span class="knockout">Your Text</span>
```
```css 
body {
    background-color: #000;
    color: #FFF;
  margin: 0 auto;
  }

.knockout {
    font-family: sans-serif;
    font-size:15vw;
    font-weight:bold;
    text-transform:uppercase;
    text-align:center;
  background:url('https://farm6.staticflickr.com/5814/21965002905_33d689d9ad_h.jpg');
  background-position:bottom center;
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  }
  ```
  
  [link]https://codepen.io/bpropelled/pen/MEONrr
  
  ## Portfolio Filtering
  ```html
  
<main>
  <section id="controls">
    <ul>
      <li class="filter filter-all active">All</li>
      <li class="filter filter-landscape">Landscape</li>
      <li class="filter filter-urban">Urban</li>
      <li class="filter filter-portrait">Portrait</li>
    </ul>
  </section>
  <div class="grid-wrapper">
    <div class="image landscape landscape-1 all"></div>
    <div class="image urban urban-1 all"></div>
    <div class="image urban urban-2 all"></div>
    <div class="image portrait portrait-1 all"></div>
    <div class="image urban urban-3 all"></div>
    <div class="image portrait portrait-2 all"></div>
    <div class="image urban urban-4 all"></div>
    <div class="image landscape landscape-2 all"></div>
    <div class="image portrait portrait-3 all"></div>
    <div class="image landscape landscape-3 all"></div>
    <div class="image landscape landscape-4 all"></div>
    <div class="image portrait portrait-4 all"></div>
  </div>
</main>
  ```
  
  ```css
  * {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
}

.hide {
  -webkit-animation: fadeOut 150ms ease;
          animation: fadeOut 150ms ease;
  opacity: 0;
}

@-webkit-keyframes fadeOut {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

@keyframes fadeOut {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
.hide {
  display: none;
}

#controls {
  margin-bottom: 2rem;
}
#controls ul {
  list-style: none;
  padding: 1rem;
  margin: 0;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
}
#controls ul li {
  margin: 0;
  padding: 0.5rem;
  border: 1px solid #eee;
  cursor: pointer;
}
#controls ul li:hover {
  background: #eee;
}
@media (min-width: 400px) {
  #controls ul li {
    margin-right: 1rem;
    padding: 1rem;
  }
}
#controls ul .active {
  background: #444;
  color: white;
}
#controls ul .active:hover {
  color: #444;
}

.grid-wrapper {
  display: -ms-grid;
  display: grid;
  -ms-grid-columns: (1fr)[1];
      grid-template-columns: repeat(1, 1fr);
  -ms-grid-rows: auto;
      grid-template-rows: auto;
  grid-gap: 1rem;
  -ms-grid-column-align: center;
      justify-items: center;
  margin: 1rem;
}

@media (min-width: 500px) {
  .grid-wrapper {
    -ms-grid-columns: (1fr)[2];
        grid-template-columns: repeat(2, 1fr);
  }
}
@media (min-width: 768px) {
  .grid-wrapper {
    -ms-grid-columns: (1fr)[3];
        grid-template-columns: repeat(3, 1fr);
  }
}
@media (min-width: 1368px) {
  .grid-wrapper {
    -ms-grid-columns: (1fr)[4];
        grid-template-columns: repeat(4, 1fr);
  }
}
.image {
  width: 100%;
  height: 50vh;
}

@media (min-width: 500px) {
  .image {
    width: 100%;
    height: 50vw;
  }
}
@media (min-width: 768px) {
  .image {
    width: 100%;
    height: 40vw;
  }
}
@media (min-width: 1368px) {
  .image {
    width: 100%;
    height: 20vw;
  }
}
.urban-1 {
  background: url(https://unsplash.it/1500?image=1075);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.urban-2 {
  background: url(https://unsplash.it/1500?image=1067);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.urban-3 {
  background: url(https://unsplash.it/1500?image=1033);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.urban-4 {
  background: url(https://unsplash.it/1500?image=983);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.landscape-1 {
  background: url(https://unsplash.it/1500?image=961);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.landscape-2 {
  background: url(https://unsplash.it/1500?image=916);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.landscape-3 {
  background: url(https://unsplash.it/1500?image=901);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.landscape-4 {
  background: url(https://unsplash.it/1500?image=876);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.portrait-1 {
  background: url(https://unsplash.it/1500?image=978);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.portrait-2 {
  background: url(https://unsplash.it/1500?image=996);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.portrait-3 {
  background: url(https://unsplash.it/1500?image=1027);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.portrait-4 {
  background: url(https://unsplash.it/1500?image=838);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}
```

```javascript
// Show all
$('.filter-all').on('click', function() {
  var $this = $(this);
  $('.filter').removeClass('active');
  $this.addClass('active');
  $('.all').removeClass('hide');
});

// Show landscape
$('.filter-landscape').on('click', function() {
  var $this = $(this);
  $('.filter').removeClass('active');
  $this.addClass('active');
  $('.landscape').removeClass('hide');
  $('.urban, .portrait').addClass('hide');
});

// Show urban
$('.filter-urban').on('click', function() {
  var $this = $(this);
  $('.filter').removeClass('active');
  $this.addClass('active');
  $('.urban').removeClass('hide');
  $('.portrait, .landscape').addClass('hide');
});

// Show portrait
$('.filter-portrait').on('click', function() {
  var $this = $(this);
  $('.filter').removeClass('active');
  $this.addClass('active');
  $('.portrait').removeClass('hide');
  $('.landscape, .urban').addClass('hide');
});


```

[link]https://codepen.io/brianhaferkamp/pen/ZyOjPo/