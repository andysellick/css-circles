Segmented CSS circles generator in Less
=======================================

Less CSS mixin to generate interactive segmented circles using only CSS. This repo is intended as a working demonstration of what is possible with this mixin, if you want to just jump right in and get started I recommend you incorporate [this Less file] (src/static/less/circles.less) into your own project.

Features
--------

The mixin allows for generation of circles containing any number of segments from 4 upwards, although most browsers start to have CSS rendering issues if you try more than 12 segments. Hover effects to expand circle segments on mouseover are included but can be overridden or removed if not required.

In addition, the mixin has options to allows you to add a circle inside your circle, to make a ring. There is also a further option with a ring circle to make the hover effect appear as if the segments are moving out from the circle rather than just expanding.

Usage
-----

In your Less, apply the mixin to your element as follows.

```html
.yourcustomcircle {
	.gencircle(@numSegments,@donut: no,@donutSize: 50%,@donutStatic: no);
}
```

Options are:

- @numSegments: the number of segments your circle should have. Required field, must be 4 or more.
- @donut: Optional value. Set to yes if you want your circle to be a ring.
- @donutSize: Optional value. Defaults to 50%. Set to the size the ring should be.
- @donutStatic: Optional value. Set to yes to have segments appear to move away from the circle on hover, rather than simply expand.

Note: to remove the hover effect add the class of 'nohover' to the parent element.

Add markup as follows:

```html
<div class="yourcustomcircle">
	<div class="segmentwrapper segment1">
		<div class="segment"><div class="inner"></div></div>
	</div>
	<div class="segmentwrapper segment2">
		<div class="segment"><div class="inner"></div></div>
	</div>
	<!-- add in each required segment as above, incrementing the segment class number as shown -->
</div>
```



Use of Gulp
------------  

There is a `gulpfile.js` within this repository to make development much quicker. All you need to do is:
* Install Node (http://nodejs.org) & Gulp (https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md)  
* Run `npm run setup`  
This will install all the dependencies found in `package.json` (The `node_modules` folder that is generated when you run this command should be created on a case-by-case basis and not pushed to a repository), install the Bower dependencies found in `package.json` and run the local server through the `gulp` command.

Note for Windows users with Git Bash: you may need to run 'npm run setup' a couple of times for it to finally work.
  
This will open up a tab in your browser, running a server at `localhost:3000` (unless you have set up a proxy server address - details on how to change this are in the `gulpfile.js` file).

Gulp features
-------------

Name | Version | Description
--- | --- | ---
**gulp** | ^3.9.0 | Task runner to automate various tasks
**browser-sync** | ^2.8.0 | Local server enabling instant DOM injection to all devices connected when a file is changed
**gulp-byetdiff | ^1.0.0 | Shows a the difference between file sizes before and after gulp tasks have run.
**gulp-concat** | ^2.6.0 | Concatenates multiple files into one
**gulp-cache** | ^0.2.10 | Enables caching of piped files to prevent tasks being run unnecessarily
**gulp-imagemin** | ^2.3.0 | Compresses images - packaged with gifsicle, jpegtran, optipng, and svgo
**gulp-jshint** | ^1.11.2 | Provides JS validation and hinting. Settings for this are in the `.jshintrc` file
**gulp-less** | ^3.0.3 | Converts LESS files in CSS
**gulp-load-plugins** | ^1.0.0-rc.1 | Handles the `require()` functions for all plugins in `package.json`
**gulp-minify-css** | ^1.2.0 | Minifies CSS files to reduce file sizes
**gulp-newer** | ^0.5.1 | Ensure that gulp tasks only run on files that have changed rather than all files.
**gulp-notify** | ^2.2.0 | Enables the use of native notifications to display when tasks are complete
**gulp-plumber** | ^1.0.1 | Prevent pipe breaking caused by errors from gulp plugins
**gulp-rename** | ^1.2.2 | Allows files to be renamed via JS
**gulp-uglify** | ^1.2.0 | Minifies JS files
**gulp-util** | ^3.0.6 | Utility functions for gulp plugins
**jshint-stylish** | ^2.0.1 | Stylish reporter for JSHint
**path** | ^0.11.14 | Copy of Node.JS path module
**del** | ^1.2.0 | Enables the deleting of files

### BrowserSync
  
The main component of this Gulp setup is BrowserSync. This plugin provides the following advantages for development:  
* Simultaneous page scrolling for all devices connected to the same link  
* Clicking links or populating form fields on one device will duplicate this behaviour on all other linked devices  
* A dashboard at `localhost:3001` where you can send commands to all connected devices, perform actions and do network throttle testing.

