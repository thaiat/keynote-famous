Short cuts:
* F : full screen
* Esc: all slide
* s : speaker notes
* Alt + click : zoom / unzoom


## Demo
### Codio

Show the end result from capptivate

we are going to use an awesome html5 editor. It's called codio. 

It s not only a very fast editor with in line linting, but it comes also with a box and a terminal so you can play
around and install all kind of stuff without polluting your laptop. Plus you can access from where you want so it s very easy to switch laptopt and start over where you left.
To ease the work with famous I have developped a yemoan generator that is going to do all the hard work for you. 
It will scaffold the application using angular best pratcices, but together linting, unit testing, e2e testing.
It has a very clean architecture model as it using browserify under the hoods.
Lets see how you install it : 

* open new project `famous-flickr-1`
* `nvm install 0.10.30`
* `npm install -g generator-mcfly`

While this is installing demonstrate how browserify works


* open a new project `browserify-1`
* `nvm install 0.10.30`
* `npm install -g browserify`
* `touch foo.js`
```javascript
exports.magic=function(value){
    return 2*value;
};
```
* `touch index.js`
```javascript
var foo=require('./foo.js');
var res= foo.magic(20);
console.log(res);
```
* `node index.js`
* `npm install -g browserify`
* `touch index.html`
! tab
```html
<body>
<h1>Browserify works</h1>
<script src="bundle.js"></script>
</body>
```
* split the screen and display the html
* go back to index.js
```javascript
var node=document.createTextNode(res);
document.body.appendChild(node);
```
* `browserify index.js -o bundle.js`
* go back to foo.js 
```javascript
var gamma=require('gamma');
exports.magic=function(value){
    return gamma(value);
};
```
* terminal : `npm install gamma`
* `browserify index.js -o bundle.js`


* terminal : `npm install cssify`
* `touch main.css`
```css
body {
    background-color:red;
    color:white;
}
```
* go back to index.js and add first line:
`require('./main.css')`
* `browserify index.js  -t cssify -o bundle.js`


come back to installed project famous-flickr-2
* `yo mcfly`
* bash ./startup.sh 
* bash ./bin/prepublish.sh
* autosave false
* change port to 5000
* prepare 2 windows
* `gulp browsersync'



DEMO START
Explain the project
* gulp help
* gulp lint

talk about the application structuration
server / client
separation by features and then types
best practices to deal with any kind of project size
Scaffold 1 module, 2 services, and 1 controller
run gulp karma




* install module `yo mcfly:module common`
* install service photos `yo mcfly:service common photos`
* install famous helper `yo mcfly:service common famousHelper`
* install controller home `yo mcfly:controller common home`
* modify head of index.html
```html
    <head>
    <meta charset="UTF-8">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no, target-densitydpi=device-dpi">
    <title>Flickr</title>
    <link rel="stylesheet" href="styles/main.css">
</head>
```
* modify `main.scss`

```css
@import "../../bower_components/font-awesome/scss/font-awesome.scss";

body {
    background-color:#000;
    color:white;
}

html, body , * {
    font-family:'verdana';
}

.full-screen {
    position: fixed;
    bottom: 0;
    top: 0;
    left: 0;
    right: 0;
}

.full-height,
.full-height .fa-surface {
    height: 100%
}

.full-width,
.full-width .fa-surface {
    width: 100%
}

.full-size {
    height: 100%;
     width: 100%;
}

.photo0 {
   padding-top:2px;
   padding-left:2px;
   padding-right:1px;
}

.photo1 {
   padding-top:2px;
   padding-left:1px;
   padding-right:1px;
}

.photo2 {
   padding-top:2px;
   padding-left:1px;
   padding-right:2px;
}

.circle{
    border-radius:50%;
}

.text-small{
 font-size:13px;
}

.text-center {
    text-align:center;
}

.white {
    color:#FFFFFF;
}

.border-bottom{
    border-bottom:2px solid white;
}

.padding{
    padding:5px;
}

#circleSvgContainer{
    width:100%;
    height:100%;
}

#circleSvgContainer > svg {
    width: 100%;
    display: block;
}

```

Add the dynamic sass
```scss
@mixin text-center-x {
    @for $i from 1 through 10  {
        .text-center-#{$i*10} {
            text-align:center;
            line-height:$i*10px;
        }
    }
}
@include text-center-x;
```

wrap `ui-view` with `fa-app` in `index.html`
```html
<fa-app class="full-screen">
    <ui-view></ui-view>
</fa-app>
```


bind directive and home controller + controllerAs : 'vm' index.js
```js
controller: fullname + '.home',
controllerAs: 'vm'
```


EXPLANATION ON fa-modifier
home.html
```html 
<fa-view>
    <fa-surface>
        <label for="">translateX</label>
        <br>
        <input type="text" ng-model="vm.translateX" ng-init="vm.translateX=100">
        <br>
        <label for="">translateY</label>
        <br>
        <input type="text" ng-model="vm.translateY" ng-init="vm.translateY=100">
    </fa-surface>


    <fa-modifier fa-align="[0.5,0.5]" fa-origin="[0.5,0.5]" fa-translate="[vm.translateX,0]">
        <fa-modifier fa-translate="[0,vm.translateY]">
            <fa-surface fa-size="[100,100]" fa-background-color="'red'"></fa-surface>
        </fa-modifier>
    </fa-modifier>

</fa-view>
```



Install npm packages
```
npm install --save lodash randomstring
```

change get function of `photos` with 
```js
var generate = function(width, height, number, groupOf) {
    number = number || 1;
    groupOf = groupOf || 1;
    var photos = _.chain(_.range(number))
        .map(function(index) {
            return 'http://lorempixel.com/' + Math.round(width) + '/' + Math.round(height) + '/?i=' + randomstring.generate(7);
         })
        .groupBy(function(value, i) {
                    return Math.floor(i / groupOf);
         })
                .value();

            return photos;
        };

        var getStyle = function(photoUrl) {
            return {
                'background-image': 'url(\'' + photoUrl + '\')',
                'background-size': 'cover',
                'background-repeat': 'no-repeat',
                'background-position': 'center',
                'width': '100%',
                'height': '100%'
            };
        };
        
         return {
            generate: generate,
            getStyle:getStyle
        };
```

change famousHelper with:
```js
'use strict';
var servicename = 'famousHelper';

module.exports = function(app) {

    var dependencies = ['$famous'];

    function service($famous) {
        var getRenderNode = function(cacheEl, findSelector) {
            if(!cacheEl) {
                var el = $famous.find(findSelector)[0];
                if(el) {
                    cacheEl = el.renderNode;
                }
            }
            return cacheEl;
        };

        return {
            getRenderNode: getRenderNode
        };

    }
    service.$inject = dependencies;
    app.factory(app.name + '.' + servicename, service);
};
```


In the `home` controller define
```js
var deps = ['$window', '$famous', app.name + '.photos', app.name + '.famousHelper'];

 function controller($window, $famous,  photos, famousHelper) {
....

vm.viewSize = {
            width: $window.innerWidth,
            height: $window.innerHeight
        };
        vm.headerHeight = 200;
        vm.userName = 'John Doe';

        vm.photos = photos.generate(2 * vm.viewSize.width / 3, 2 * vm.viewSize.width / 3, 30, 3);
        vm.photoMain = photos.generate(vm.viewSize.width * 2, vm.headerHeight * 2)[0][0];
        vm.photoProfile = photos.generate(100, 100)[0][0];

        vm.getPhotoStyle = photos.getStyle;
        
       

```

home.html
```html
<fa-view>
    <!-- SCROLL VIEW-->
    <fa-scroll-view id="scrollView" fa-options="{direction: 1, edgeGrip:1}">
    <!-- HEADER -->
    <!-- IMAGES GRID-->
    </fa-scroll-view>
    <!-- FOOTER BAR-->
</fa-view>
```

change to single row
```html
<fa-surface class="full-height" ng-repeat="photo in vm.photos[0]" >
   <div ng-style="vm.getPhotoStyle(photo)"></div>
</fa-surface>
````
Add eventHandler to home.js (inject $famous)
```js
        var EventHandler = $famous['famous/core/EventHandler'];
        vm.eventHandler = new EventHandler();

```

```html
fa-pipe-to="vm.eventHandler"
fa-pipe-from="vm.eventHandler" 
```

change to grid
```html
 
<fa-view>
    <fa-scroll-view id="scrollView" fa-pipe-from="vm.eventHandler" fa-options="{direction: 1, edgeGrip:1}">
        <!-- IMAGES GRID-->
        <fa-view ng-repeat="row in vm.photos track by $index" fa-size="[undefined, vm.viewSize.width/3]" fa-index="$index">
            <fa-modifier>
                <fa-grid-layout fa-options="{dimensions :[3,1]}">
                    <fa-modifier ng-repeat="photo in row" fa-size="[vm.viewSize.width/3, vm.viewSize.width/3]">
                        <fa-surface fa-pipe-to="vm.eventHandler" fa-background-color="'black'" class="full-height">
                            <div class="full-height photo{{$index}}">
                                <div class="full-height" ng-style="vm.getPhotoStyle(photo)"></div>
                            </div>
                        </fa-surface>
                    </fa-modifier>
                </fa-grid-layout>
            </fa-modifier>
        </fa-view>
    </fa-scroll-view>
</fa-view>
```


Footer: add before the end node
```html
    <!-- FOOTER BAR-->
    <fa-modifier fa-size="[undefined, 40]" fa-align="[0,1]" fa-origin="[0,1]">
        <fa-modifier fa-opacity="0.6">
            <fa-surface fa-background-color="'black'" ></fa-surface>
        </fa-modifier>
        <!-- FOOTER BAR BUTTONS -->
      </fa-modifier>  
```

and then
```html
<!-- FOOTER BAR BUTTONS -->
<fa-grid-layout fa-options="{dimensions: [3,1]}">
    <fa-surface>
        <div class="text-center-40">
            <i class="fa fa-photo"></i>
        </div>
    </fa-surface>
    <fa-surface>
        <div class="text-center-50">
            <i class="fa fa-camera fa-2x"></i>
        </div>
    </fa-surface>
    <fa-surface>
        <div class="text-center-40">
            <i class="fa fa-user"></i>
        </div>
    </fa-surface>
</fa-grid-layout>
```


Header inside the srollview:

```html
<!-- HEADER -->
<fa-view>
    <fa-modifier fa-size="[undefined, vm.headerHeight]">
        <fa-surface></fa-surface>
        <!-- MAIN PHOTO -->
        <!-- PROFILE PICTURE AND TEXT  -->
        <!-- HEADER TOOLBAR -->
    </fa-modifier>
</fa-view>
```
replace fa-surface tag with (this create the upper image)
```html
<!-- MAIN PHOTO -->
<fa-modifier fa-align="[0.5,0]" fa-origin="[0.5,0]" ffa-size="[vm.viewSize.width+vm.getOverpull(), vm.headerHeight+15+vm.getOverpull()]" ffa-translate="[0, -15-vm.getOverpull()]" fa-opacity="1">
    <fa-surface class="full-height" fa-z-index="2" fa-pipe-to="vm.eventHandler">
        <div id="mainPhoto" class="full-height" ng-style="vm.getPhotoStyle(vm.photoMain)"></div>
    </fa-surface>
</fa-modifier>
```

under parent modifier of surface :
```html
<!-- PROFILE PICTURE AND TEXT -->
<fa-modifier fa-align="[0.5,0.5]"  fa-origin="[0.5,0.5]" fa-size="[200,110]" ffa-translate="[0,-20-vm.getOverpull()/2]">
    <!-- PROFILE CIRCLE -->
     <fa-modifier fa-size="[80,80]" fa-align="[0.5,0]" fa-origin="[0.5,0]">
                        <fa-surface class="full-height" fa-z-index="4" fa-pipe-to="vm.eventHandler">
                            <div class="circle full-height" ng-style="vm.getPhotoStyle(vm.photoProfile)">
                            </div>
                        </fa-surface>
                    </fa-modifier>
                    <fa-modifier fa-size="[undefined,20]" fa-align="[0.5,1]" fa-origin="[0.5,1]">
                        <fa-surface class="white text-center text-small full-height" fa-z-index="4" fa-pipe-to="vm.eventHandler">
                            <div>{{vm.userName}}</div>
                        </fa-surface>
                    </fa-modifier>
</fa-modifier>

```

under surface :

```html
<!-- HEADER TOOLBAR -->
<fa-modifier fa-size="[undefined, 40]" fa-align="[0,1]" fa-origin="[0,1]" fa-translate=[0,0,10]>
    <fa-modifier fa-opacity="0.6">
        <fa-surface fa-background-color="'black'"></fa-surface>
    </fa-modifier>
    <fa-grid-layout fa-options="{dimensions: [3,1]}">
        <fa-surface fa-pipe-to="vm.eventHandler">
            <div class="text-center-40">Photo</div>
        </fa-surface>
        <fa-surface fa-pipe-to="vm.eventHandler">
            <div class="text-center-40 border-bottom">Albums</div>
        </fa-surface>
        <fa-surface fa-pipe-to="vm.eventHandler">
            <div class="text-center-40">Groups</div>
        </fa-surface>
    </fa-grid-layout>
</fa-modifier>
```




Add animation function to home.js
```js
var getScrollView = function() {
            vm.scrollview = famousHelper.getRenderNode(vm.scrollview, '#scrollView');
            return vm.scrollview;
        };

        var getMainPhoto = function() {
            vm.mainPhoto = famousHelper.getRenderNode(vm.mainPhoto, '#mainPhoto');
            return vm.mainPhoto;
        };


vm.getOverpull = function() {
    return -Math.min(0, getScrollView().getAbsolutePosition());
};

vm.getToolbarTranslate = function() {
    var pos = getScrollView().getAbsolutePosition();
     return pos > (vm.headerHeight - 60) ? pos - (vm.headerHeight - 60) : 0;
};
        
       
        
```
deactivate ffa one by one

add to the top modifier to do the stick header
```html
fa-translate="[0, vm.getToolbarTranslate()]"
```


Blur home.js (remove old getMainPhotoBlurredOpacity fn)


```js
 var Timer = $famous['famous/utilities/Timer'];
        Timer.every(function() {
            var pos = vm.getOverpull();
             if(getMainPhoto()) {
                vm.mainPhoto.setProperties({
                    webkitFilter: getBlur(pos)
                });
            }

        }, 1);

        function getBlur(pos) {
            var blur = pos > 100 ? Math.min(Math.round((pos -100) / 15), 10) : 0;
            return 'blur(' + blur + 'px)';
        }

```


Install ProgressBar.js
```
npm install --save progressbar.js shifty
```

home.html before photo Profile image modifier
```html
<!-- PROFILE CIRCLE -->
                    <fa-modifier fa-size="[88,88]" fa-align="[0.5,0]" fa-origin="[0.5,0]" fa-translate="[0, -4]">
                        <fa-surface class="circle full-height" fa-z-index="4" fa-pipe-to="vm.eventHandler">
                            <div id="circleSvgContainer"></div>
                        </fa-surface>
                    </fa-modifier>

```

home.js
```js
var ProgressBar = require('progressbar.js');


var fillCircle = function(value) {
            if(vm.circle) {
                vm.circle.set(value);
                return;
            }
            vm.circle = new ProgressBar.Circle($window.document.getElementById('circleSvgContainer'), {
                color: '#3498DB',
                strokeWidth: 4,
                fill:'#FFFFFF'
            });
        };
        
```

in the timer
```js
fillCircle(Math.min(1, pos / 250));

```







