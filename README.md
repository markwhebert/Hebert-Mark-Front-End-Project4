# Mark Hebert's Process for Website Optimization
Current Speed (mobile/desktop): 
#	index		  28  /  30
#	2048		  75  /  87
#	webperf		  75  /  87
#	proj-mobile	  68  /  88
#	pizza		  25  /  30


## Focus #1: index.html
Address "Should Fix" issues in PageSpeed Insights:
==================================================

Optimize Images:
----------------
This issue was noticed prior to using PageSpeed Insights, by looking at
 the "Network" tab of the Dev tools and noticing the pizzeria.jpg image
 took 1.30s to load

This issue was remedied by using FILEminimizer Pictures 3.0 by balesio
 (free) on all of the image files.  A 96.1% reduction in file size was 
 recorded for the pizzeria.jpg file.  

New Site Score (mobile/desktop): 
#	index		  72  /  83 (+44 / +53)
#	2048		  75  /  88 ( 0  / +1 )
#	webperf		  77  /  90 (+2  / +3 )
#	proj-mobile	  68  /  90 ( 0  / +2 )
#	pizza		  62  /  83 (+37 / +53)



Eliminate Render-Blocking JavaScript:
-------------------------------------
Make the js running google analytics load asynchronously as opposed to
 renderblocking.  This is done by adding "async" after the "script".  
 This was also done to the other pages.  On 2048, the perfmatters.js was 
 render blocking, so this was also corrected.  

New Site Score (mobile/desktop): 
#	index		  72  /  83 ( 0  /  0 )
#	2048		  80  /  90 (+5  / +2 )
#	webperf		  81  /  92 (+4  / +2 )
#	proj-mobile	  72  /  92 (+4  / +2 )
#	pizza		  65  /  83 (+2  /  0 )



Eliminate Render-Blocking CSS:
---------------------------------------------
Due to the amount of time being used to retrieve the googleapi (290ms), I
 combined the important bits of the googleapi (cyrillic-ext --> 400 only,
 as 700 was not used) with the style.css, reducing the number of steps 
 the browser needed to take and the number of critical files.  

Also, a number of css styles were put inline.  See the comments in the
 respective html files. Most important to note is the portrait mobile 
 view as well as the print.css, eliminating another critical file and 
 removing the render blocking ability of the file.  

New Site Score (mobile/desktop): 
#	index		  81  /  86 (+9  / +3 )
#	2048		  86  /  92 (+6  / +2 )
#	webperf		  88  /  94 (+7  / +2 )
#	proj-mobile	  76  /  94 (+4  / +2 )
#	pizza		  65  /  83 (+3  /  0 )



Address Consider Fixing issues in PageSpeed Insights:
=====================================================

Minify:
------------
Minified the HTML and CSS with .
Nothing really happened :(

New Site Score (mobile/desktop): 
#	index		  81  /  86 ( 0  /  0 )
#	2048		  86  /  92 ( 0  /  0 )
#	webperf		  88  /  94 ( 0  /  0 )
#	proj-mobile	  76  /  94 ( 0  /  0 )
#	pizza		  65  /  83 ( 0  /  0 )



Enable Compression:
-------------------
Used htmlcompressor.com to compress the html and js files.  CSS files
 yielded no change in size after compression.  
Nothing really happened :(

New Site Score (mobile/desktop): 
#	index		  81  /  86 ( 0  /  0 )
#	2048		  86  /  92 ( 0  /  0 )
#	webperf		  88  /  94 ( 0  /  0 )
#	proj-mobile	  76  /  94 ( 0  /  0 )
#	pizza		  65  /  83 ( 0  /  0 )



Further Optimize Images:
------------------------
Since the pizzeria.jpg image is taking up a lot of data due to the size
 it needs to be for the pizza page, I made a copy of the image and moved 
 it into the "img" file with all of the other images for the index page, 
 and reduced the size to 115 pixels wide, consistent with the actual 
 image size displayed.  I did the same with the mobilewebdev.jpg.  I also 
 recompressed them using FILEminimizer.

New Site Score (mobile/desktop): 
#	index		  88  /  94 (+7  / +8 )
#	2048		  86  /  92 ( 0  /  0 )
#	webperf		  88  /  94 ( 0  /  0 )
#	proj-mobile	  88  /  94 (+12 /  0 )
#	pizza		  65  /  83 ( 0  /  0 )



Inline Font:
------------
The font style was moved out of css and into an inline format in html. 
 Sadly, nothing happened.

New Site Score (mobile/desktop): 
#	index		  88  /  94 ( 0  /  0 )
#	2048		  86  /  92 ( 0  /  0 )
#	webperf		  88  /  94 ( 0  /  0 )
#	proj-mobile	  88  /  94 ( 0  /  0 )
#	pizza		  65  /  83 ( 0  /  0 )



Relocate Images:
----------------
I notices a number of the image sources in index.html were web links.  I
 changed this to localize the location of the images, and noticed my 
 score decreased.  So naturally, I decided to go the other way with it, 
 and make all of the images external web links.  

New Site Score (mobile/desktop): 
#	index		  89  /  95 (+1  / +1 )
#	2048		  89  /  95 (+3  / +3 )
#	webperf		  89  /  95 (+1  / +1 )
#	proj-mobile	  89  /  95 (+1  / +1 )
#	pizza		  65  /  83 ( 0  /  0 )



Inline CSS:
-----------
After many revisions and streamlining the CSS into the HTML and not
 having the score change at all, I grew fairly frustrated.  Out of this 
 frustration, I decided to inline of the remaining CSS.  This produced 
 amazing results as shown below.  

New Site Score (mobile/desktop): 
#	index		  97  /  98 (+8  / +3 )
#	2048		  98  /  98 (+9  / +3 )
#	webperf		  97  /  98 (+8  / +3 )
#	proj-mobile	  98  /  98 (+9  / +3 )
#	pizza		  65  /  83 ( 0  /  0 )



## Focus #2: Pizza
Improve PageSpeed Insights
--------------------------
I cut out anything that wasn't relavent in bootstrap-grid.css, and wasn't
 left with much, so I decided to inline all of the css.  I also reduced 
 the size of the pizza image.  This provided an excellent increase in the 
 PageSpeed Insights score, which will hopefully help out the fps a bit
#	pizza		  94  /  95 (+29 / +22)



Focus on loops:
---------------
Created a variable within the update function to house the scroll factor
 which is the same for each pizza at this scroll point.  
I also eliminated the creation of the "phase" variable, which seemed to
 be excessive for 1-time use. 
Reduced the size of the pizza image for the back ground and moved the
 dimensions to the html.

# I created a variable to try and quantify the average fps as opposed to looking at unquantified fluctuations within a graph.  A few things I noticed:
Based on the average ms per frame calculated, the actual frames per
 second average between 900 and 2,000 depending on my scroll speed.  
The other thing I noticed was the scroll speed greatly influences the fps.
 I have my settings set to a fast scroll, which tends to put me into the 
 60-30fps range (or 900-1,700 average frames per second).  If I scroll 
 like my grandpa, I can get everything below the 60fps (above 2,000 
 frames per second).  Therefore, if I don't pass this section, it is 
 because you scrolled too fast :)



#Resize Pizzas (Original 228ms):

Moved the static variables outside of the for loop within the changePizzaSizes()
#	New 	13ms

Converted the determineDX function into a formula
#	New 	12ms

Eliminated the switches through an if/else and conversion to a formula
#	New 	6.2ms

Created a global variable for total number of pizzas and applied it to the loop
#	New 	3.1ms