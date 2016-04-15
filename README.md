# SoftwareRVG-Transform-3DAnimation-Transparent-circles-in-motion
function kickOffTransition(setTranslate3DTransform)(setTransitionDuration) developed by SoftwareRVG
                   DEBUG MODE IN CODEPEN 
**<a href="http://codepen.io/SoftwareRVG/pen/jqOXBp">http://codepen.io/SoftwareRVG/pen/jqOXBp </a>**

--------------------------------------------------------------------------------------------------------------------------------


Skip to content
This repository

    Pull requests
    Issues
    Gist

    @SoftwareRVG

1
0

    0

SoftwareRVG/SoftwareRVG-Transform-3DAnimation-Transparent-circles-in-motion
Code
Issues 0
Pull requests 0
Wiki
Pulse
Graphs
Settings
SoftwareRVG-Transform-3DAnimation-Transparent-circles-in-motion/entering and leaving to< div container>
67fabd0 a minute ago
@SoftwareRVG SoftwareRVG Update entering and leaving to< div container>
206 lines (175 sloc) 6.27 KB
 view en codepen :   
                  
                   DEBUG MODE IN CODEPEN 
**<a href="http://codepen.io/SoftwareRVG/pen/jqOXBp">http://codepen.io/SoftwareRVG/pen/jqOXBp </a>**
http://codepen.io/SoftwareRVG/pen/jqOXBp

# SoftwareRVG-Transform-3DAnimation-Transparent-circles-in-motion
function kickOffTransition(setTranslate3DTransform)(setTransitionDuration) developed by SoftwareRVG
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
	<meta name="generator" content="Software RVG HTML Editor (www.software-rvg.com)">
    <meta name="dcterms.created" content="Do., 28 feb. 2016 21:29:24 GMT">
	<meta name="description" content="Software RVG advanced designs_transparent circles into and out of position_Translate3d_Transform_element ">
	<meta name="keywords" content="Software RVG,Advanced designs,transparent circles into and out of position,css3,html5,software RVG designs,translate 3d">
    <title>SOFTWARE RVG Advanced Designs,"transparent circles into and out of position"</title>
  <style type="text/css">    
    <!--
	body {
      color:#E91414;
      background-color:#111111;
      background-image:url('Background Image');
      background-repeat:no-repeat; width:1000px;
  margin-left:auto;
  margin-right:auto;
  font-family: "Arial", sans-serif;
  color:blue;
  text-align:center;
  font-size:30px;
}
    } .header {
  width:500px;
  margin-left:auto;
  margin-right:auto;
  font-family: "Arial", sans-serif;
  color:blue;
  text-align:center;
  font-size:30px;
}

.header h3 {
color:blue;
  opacity:0.9;
}

.header small {
color:red;
  opacity:0.9;
  font-size:20px;
}


<style>
body {
	background-color: #FFF;
	margin: 30px;
	margin-top: 10px;
}
#box {  margin-left:auto;
  margin-right:auto;
	width: 550px;
	height: 350px;
	border: 5px black solid;
	overflow: hidden;
	background-color: #F2F2F2;
}
#contentContainer {
	position:   margin-left:auto;
  margin-right:auto;;
}
.thing {
	transition-property: transform;
	transition-timing-function: ease-in-out;
	position: absolute;
	width: 100px;
	height: 100px;
	border-radius: 50px;
	background-color: #0066CC;
	opacity: .5;
}

</style>
</head>
<div class="header">
  <h3><strong>TRANSPARENT CIRCLES IN MOTION </strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<small>by SOFTWARE RVG</small></h3>
</div>
<div><h5>" TRANSPARENT CIRCLES INTO AND OUT OF POSITION "</h5></div>

<body>
<div id="box">
	<div id="contentContainer">
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>
		<div class="thing"></div>						
	</div>
</div>

<script src="//www.kirupa.com/html5/examples/js/prefixfree.min.js"></script>
<script>
var theThings = document.querySelectorAll(".thing");

var transitionDurations = ["transitionDuration", "msTransitionDuration", "webkitTransitionDuration", "mozTransitionDuration", "oTransitionDuration"];
var transitionDurationProperty = getSupportedPropertyName(transitionDurations);

var transforms = ["transform", "msTransform", "webkitTransform", "mozTransform", "oTransform"];
var transformProperty = getSupportedPropertyName(transforms);

function setInitialProperties() {
	for (var i = 0; i < theThings.length; i++) {
		var theThing = theThings[i];

		var circleSize = Math.round(30 + Math.random() * 150);
		
		theThing.style.width = circleSize + "px";
		theThing.style.height = circleSize + "px";
		theThing.style.borderRadius = .5 * circleSize + "px";
		theThing.style.opacity = .1 + Math.random() * .5;

		setTranslate3DTransform(theThing);	
	}
	setTimeout(kickOffTransition, 100);
}
setInitialProperties();


function kickOffTransition() {
	for (var i = 0; i < theThings.length; i++) {
		var theThing = theThings[i];
		
		theThing.addEventListener("transitionend", updatePosition, false);
		theThing.addEventListener("webkitTransitionEnd", updatePosition, false);
		theThing.addEventListener("mozTransitionEnd", updatePosition, false);
		theThing.addEventListener("msTransitionEnd", updatePosition, false);
		theThing.addEventListener("oTransitionEnd", updatePosition, false);
		
		setTranslate3DTransform(theThing);
		setTransitionDuration(theThing);
	}
}

function updatePosition(e) {
	var theThing = e.currentTarget;
	
	if (e.propertyName.indexOf("transform") != -1) {
		setTranslate3DTransform(theThing);
		setTransitionDuration(theThing);
	}
}

function getRandomXPosition() {
	return Math.round(-50 + Math.random() * 650);
}

function getRandomYPosition() {
	return Math.round(-50 + Math.random() * 400);
}

function getRandomDuration() {
	return (.5 + Math.random() * 3) + "s";
}

function getSupportedPropertyName(properties) {
    for (var i = 0; i < properties.length; i++) {
        if (typeof document.body.style[properties[i]] != "undefined") {
            return properties[i];
        }
    }
    return null;
}

function setTranslate3DTransform(element) {
	element.style[transformProperty] = "translate3d(" + getRandomXPosition() + "px" + ", " + getRandomYPosition() + "px" + ", 0)";
}

function setTransitionDuration(element) {
	if (transitionDurationProperty) {
		element.style[transitionDurationProperty] = getRandomDuration();
	}
}
</script><div class="footer">
  <h4>SOFTWARE RVG en Twitter</h4>
  <div class="img">
    <a href="https://twitter.com/intent/follow?original_referer=https%3A%2F%2Fstatic.parastorage.com%2Fservices%2Fsanta%2F1.1149.21%2Fstatic%2Fexternal%2Ftwitter.html%3Falign%3Dleft%26compId%3Dcomp-ieykc65q%26href%3Dhttps%253A%252F%252Ftwitter.com%252FSoftwareRVG%26lang%3Des%26origin%3Dhttp%253A%252F%252Fwww.software-rvg.com%26screen_name%3DSoftwareRVG%26show_count%3Dtrue%26show_screen_name%3Dtrue%26widgetType%3DFOLLOW&amp;ref_src=twsrc%5Etfw&amp;region=follow_link&amp;screen_name=SoftwareRVG&amp;tw_p=followbutton" title="Sigue a Rober113 (@SoftwareRVG) en Twitter" id="follow-button" class="btn"><i></i><span class="label" id="l">Seguir a <b>@SoftwareRVG</b></span></a>
	<div class="byline">
      <img src="https://3.bp.blogspot.com/-SSIfWR01A4w/Vs9bJ91mJhI/AAAAAAAAB9I/qEnEqQWJRig/s320/SOFTWARE%2BRVG-Icon%2Bapp.jpg" height="309" border="0" width="320">
    </a>
    
  </div>
</div>

<script src="//codepen.io/assets/editor/live/css_live_reload_init.js"></script>

  </body>
</html>

    Status API Training Shop Blog About 

    © 2016 GitHub, Inc. Terms Privacy Security Contact Help 

