Short cuts:
* F : full screen
* Esc: all slide
* s : speaker notes
* Alt + click : zoom / unzoom

## Slide 1
Hello everyone, I'm very glad to be here, and again welcome to this first famo.us meetup in TLV.


Today I want to show you some cool stuff about famous and especially famous angular, but before we begin, I have a couple of announcements
First I must admit that it is also my very first meetup as a presenter, so I'm very excited. We'll be writing live code at the end of the presentation so i count
on you to be my human debugger.
I want this session to be as interactive as possible so if you have any questions feel free to interrupt me.

Second I'll be presenting a meetup on ionic on november 5th. So if you want to compare ionic and famous capabilities you should register and come.
Third ans last annoucement, I have put together a meetup a another kind. It's called Russian Combat, and it s a form a self defense martial art similar to Krav Maga. It is very effective, and we have the chance
to have in Israel one of the best expert. So whenever you have an issue you can't solve with your code, it's a very effective way to release the frustration and sweat a bit.
Get in touch with me and i'll give you all the details.

So let's talk about famous.

So my name is Avi, you can see some of my details here. I've been an Entrepreneur slash CTO for the past 15 years. 3 years ago I sold my last company called Vizelia to one og the giant actor in the Green: Schneider Electric. 
Vizelia was developping a dashboard HTML5 platform for monitoring the Energy consumption in big buildings. And we used Sencha to build it.
How many of you are working in a startup ? Well you'll agree with me that one of the dream you have when you start a new company, like in the back of you're mind, you have is that it would be so cool to eventually sell it. But the question you never asked yourself 
is what do you do after you sold it. Because you know you kinda lost your baby...
So today I have the answer. In order to battle to post aquisition depression phase, the best thing to do is to start from the beginning.
And that's exactly what we did. 

We started a new company called Yoobic about 1 year ago.
The goal of Yoobic is to provide to corporate brand companies a mobile app, so they can ask the crowd to retreive for them field data. Like how are they doing in physical shops.
We call the mission Quests, and users can dedicated 10 mins of their time to take a survey while their are in the stores, with a few simple questions, so that the brand can get instant
feedback. And they get paid for that around 5 to 10 euros
The product was built using Ionic and angular, and we are in the process or re writing it with famous.
Also we are activly recruting so if you are looking for new opportunities do not hesitate to get in touch with me.

So what is the situation today if you wanna build a mobile app. You have several platforms, and one of your first choice could be to develop natively for those platforms.
And actually a lot of companies are still doing that. But as a startup you have limited resources, and you want to got live as soon as possible.
So the question is "is there a better way to achieve that"? And actually building an hybrid application seems like a very good fit. Because you reuse the same base code across all of the devices
So it is cheaper and both faster to develop.

But there is still some confusion about hybrid apps.
In 2012, Mark Zuckerberg declared that he should have bet on HTML5 over native.

And i remember that i was kind of chocking statement... It was about 5 or 6 years that i was developping a HTML 5 application (for the browser not mobile of course). And it was a lot more effective than the desktop application that we add before.
And in many aspect it reminds me of the debate between web app and desktop app like in 2000. Only in a very specific situation you should choose to go with desktop.
So when i read the statement my first reaction was a bit like that.
and then like that.

So there is a lot of controversy about what exacly Mark Zuckerberg meant. And you should be confident that the gap between native and mobile is rapidly decreasing. 
and famous help us do a few more steps in that direction.

So how does famous compare to other HTML5 / javascript frameworks.
If you look at the left column you see like the old way of doing things. Sencha and Kendo would be example of full stack javascript framework where you get everything out of the box.
The abstraction of the dom, the architecture with classes and components, and the presentation with UI theme that you have to love or be doomed.

But with the avenement of npm and bower packages, the new way of doing things is that you can choose and cherry pick the librairies you need for very specific task

So Famous is an open source web rendering engine
It is very performance focus and let you code animation in a mucg more simplier way than using css
It can be used to reproduce the native feeling your users expect from a mobile app
and it is javascript.

Now that you know what is famous you should probably know also where is famous.
They are located in San Fransisco, they shared untill a few months ago the same building as Firebase. And now that firebase as been aquired by google, the only thing really missing in the 
google stack is a nice ui framework so maybe they are going to follow the same path.
The nice thing about San Fransisco is that it is really a fun city to go. So if you are looking for a destination for you next holidays you should consider it.
Because not only like you can do lots of cool stuff, like kite surfing under the golden gate bridge and do some horse back riding on the beautilful beaches, you can also pay a visit to famous.
It is called famous Lab. The famous team will actually welcome you in their offices and you can spend a week or 2 sitting there with the developpers and get some help from the very people
writing the framework. That's awesome. Plus you feel like kind of being inside the silicon valley TV show.

There are really 2 concepts to understant when you start working with famous
The first one is the render tree.
So instead of giving you a direct interaction with the dom, famous holds an in memory tree view of nodes. Some of the node are visible and they are called renderable nodes. 
The most common renderable node is a Surface. Some of the nodes are invisible, they are  either placeholders  (their purpose is to group togeter other sub nodes) or they are modifiers
and their purpose is to animate or apply graphical tranformation to the underneath branch (translating , scaling, , rotating, changing the opacity etc..) 

To give you a clearer picture of the render tree let's take an example of a person. A person has a body, a head , arms, 
I can decide to animate the root node, or only a sub node, or both.
That's a very common technique that almost every 3D game studio is using.

The second tehcnical magic of famous is that it uses css3 Matric3D, and requestAnimationFrame to get 3D at 60 FPS.
As famous interaction layer is the render tree, it can produce how of it , HTML, WEBGL

So when we were at the famous Lab, we first tried plain famous and it was kinda of hard, and then our second attempt was to use famous-angular.

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
* `npm install -g generator-angular-famous-ionic`

While this is installing demonstrate how browserify works


* open a new project `browserify-1`
* `nvm install 0.10.30`
* `npm install -g browserify`
* touch foo.js 
* touch index.js
* touch index.html
* foo calculate gamma fs   var html = fs.readFileSync(__dirname + '/robot.html', 'utf8');
* transforms cssify brfs yamlify


come back to installed project famous-flickr-2
* `yo angular-famous-ionic`
* bash ./startup.sh 
* bash ./bin/prepublish.sh
* autosave false
* fix .tern-project
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




* install module `yo angular-famous-ionic:module common`
* install service photos `yo angular-famous-ionic:service common photos`
* install famous helper `yo angular-famous-ionic:service common famousHelper`
* install controller home `yo angular-famous-ionic:controller common home`

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

.blurred {
    filter:blur(20px);
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


EXPLANATION ON fa-modifier
home.html
```html 
<fa-view>
    <fa-surface>
        <label for="">translateY</label>
        <br>
        <input type="text" ng-model="vm.translateY" ng-init="vm.translateY=200">
        <br>
        <label for="">rotateZ</label>
        <br>
        <input type="text" ng-model="vm.rotateZ" ng-init="vm.rotateZ=1">
    </fa-surface>


    <fa-modifier fa-align="[0.5,0.5]" fa-origin="[0.5,0.5]" fa-translate="[0,vm.translateY]">
        <fa-modifier fa-rotate-z="vm.rotateZ">
            <fa-surface fa-size="[100,100]" fa-background-color="'red'"></fa-surface>
        </fa-modifier>
    </fa-modifier>

</fa-view>
```


bind directive and home controller + controllerAs : 'vm' index.js
```js
controller: fullname + '.home',
controllerAs: 'vm'
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

        vm.userName = 'John Doe';

        vm.photos = photos.generate(2 * vm.viewSize.width / 3, 2 * vm.viewSize.width / 3, 30, 3);
        vm.photoMain = photos.generate(vm.viewSize.width * 2, 150 * 2)[0][0];
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
    <fa-modifier fa-size="[undefined, 150]">
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
<fa-modifier fa-align="[0.5,0]" fa-origin="[0.5,0]" ffa-size="[vm.viewSize.width+vm.getOverpull(), 165+vm.getOverpull()]" ffa-translate="[0, -15-vm.getOverpull()]" fa-opacity="0.8">
    <fa-surface class="full-height" fa-z-index="2" fa-pipe-to="vm.eventHandler">
        <div id="mainPhoto" class="full-height" ng-style="vm.getPhotoStyle(vm.photoMain)"></div>
    </fa-surface>
</fa-modifier>
```

under parent modifier of surface :
```html
<!-- PROFILE PICTURE AND TEXT -->
<fa-modifier ffa-translate="[0,-vm.getOverpull()/2]">
    <!-- PROFILE CIRCLE -->
    <fa-modifier fa-size="[80,80]" fa-align="[0.5,0]" fa-origin="[0.5,0]" fa-translate="[0,5]">
        <fa-surface class="padding circle full-height" fa-z-index="4" fa-pipe-to="vm.eventHandler">
            <div class="circle full-height" ng-style="vm.getPhotoStyle(vm.photoProfile)"></div>
        </fa-surface>
    </fa-modifier>
    <fa-modifier fa-size="[undefined,30]" fa-align="[0.5,0]" fa-origin="[0.5,0]" fa-translate="[0,85]" >
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
        <fa-surface>
            <div class="text-center-40">Photo</div>
        </fa-surface>
        <fa-surface>
            <div class="text-center-40 border-bottom">Albums</div>
        </fa-surface>
        <fa-surface>
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
    return pos > 110 ? pos - 110 : 0;
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

```js
"progressbar": "./bower_components/progressbar.js/dist/progressbar.js"

// and 

"progressbar": {
            "exports": "ProgressBar"
        },


```
home.html before photo Profile image modifier
```html
<!-- PROFILE CIRCLE -->
 <fa-modifier fa-size="[80,80]" fa-align="[0.5,0]" fa-origin="[0.5,0]" fa-translate="[0,5]">
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
                strokeWidth: 10
            });
        };
        
```

in the timer
```js
fillCircle(Math.min(1, pos / 250));

```























