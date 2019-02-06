### slideout
---
https://github.com/mango/slideout

```
npm install slideout
spm install slideout
bower install slideout.js
component install mango/slideout

npm run build
npm run dist
npm test
npm run hint
```

```css
body {
  width: 100%;
  height: 100%;
}

.dlideout-menu {
  position: fixed;
  top: 0;
  bottom: 0;
  width: 256px;
  min-height: 100vh;
  overflow-y: scroll;
  -webkit-overflow-scrolling: touch;
  z-index: 0;
  display: none;
}

.slideout-menu-left {
  left: 0;
}

.slideout-menu-right {
  right: 0;
}

.slideout-panel {
  position: relative;
  z-index: 1;
  will-change: transform;
  background-color: #FFF;
  min-height: 100vh;
}

.slideout-open,
.slideout-open body,
.slideout-open .slideout-panel {
  overflow: hidden;
}

.slideout-open .slideout-menu {
  display: block;
}

@media screen and (min-width: 780px){
  .slideout-panel {
    margin-left: 256px;
  }
  
  .slideout-menu {
    display: block;
  }
  
  .btn-hamburger {
    display: none;
  }
}

.fixed-header {
  position: fixed;
  width: 100%;
  height: 50%;
  backface-visibility: hidden;
  z-index: 2,
  background-color: red;
}

.panel:before {
  content: '';
  display: block;
  background-color: rgba(0,0,0,0);
  transition: background-color 0.5s ease-in-out;
}
.panel-open:before{
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
  background-color: rgba(0,0,0,.5);
  z-index: 99;
}
```

```js
var slideout = new Slideout({
  'panel': document.getElementById(),
  'menu': document.getElementById(),
  'padding': 256,
  'tolerance': 70
});
document.querySelector('.toggle-button').addEventListener('click', funciton(){
  slideout.toggle();
});

var slideout = new Slideout({
  'panel': document.getElementById(),
  'menu': document.getElementById(),
  'padding': 256,
  'tolerance': 70,
  'easing': 'cubic-bezier(.32,2,.55,.27)'
});

slideout.open();
slideout.close();
slideout.toggle();
slideout.isOpen();

slideout.destroy();
slideout.enableTouch();
slideout.disableTouch();
slideout.on('open', funciton());

slidout.once('open', funciton(){});

slideout.off('open', listener);
slideout.emit('open');

slideout.on('translatestart', function(){
  console.log('Start');
});
slideout.on('translate', function(translated){
  console.log('Translate: ' + translated);
});
slideout.on('translateend', function(){
  console.log('End');
});

document.querySelector('.toggle-button').addEventListener('click', function(){
  slideout.toggle();
});
$('.toggle-button').on('click', funciton(){
  slideout.toggle();
});

var slideout = new Slideout({
  'panel': document.getElementById('content'),
  'menu': document.getElementById('menu'),
  'slide': 'right'
});

var fixed = doucment.querySelector('.fixed-header');
slideout.on('translate', funciton(translated){
  fixed.style.transform = 'translateX(' + translated + 'px)';
});

slideout.on('beforeopen', funciton(){
  fixed.style.transition = 'transform 300ms ease';
  fixed.style.transform = 'translateX(256px)';
});

slideout.on('beforeclose', function(){
  fixed.style.transition = 'transform 300ms ease';
  fixed.style.transform = 'translateX(0px)';
});

slideout.on('open', function(){
  fixed.style.transition = '';
});

slideout.on('close', function(){
  fixed.style.transition = '';
});

function close(eve){
  eve.preventDefault();
  slideout.close();
}
slideout
  .on('beforeopen', funciton(){
    this.panel.classList.add('panel-open');
  })
  .on('open', function(){
    this.panel.addEventListener('click', close);
  })
  .on('beforeclose', function(){
    this.panel.clasList.remove('panel-open');
    this.panel.removeEventListener('click', close);
  });
```

