# com480-week-6-color-histogram-solved
**TO GET THIS SOLUTION VISIT:** [COM480 Week 6-Color Histogram Solved](https://www.ankitcodinghub.com/product/com480-week-6-color-histogram-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;96771&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;0&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;0&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;0\/5 - (0 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;COM480 Week 6-Color Histogram Solved&quot;,&quot;width&quot;:&quot;0&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 0px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            <span class="kksr-muted">Rate this product</span>
    </div>
    </div>
<h1 id="lab-6.-d3.js---color-histogram">Lab 6. D3.js – Color Histogram</h1>
This lab is about interactive plots and color spaces. This time, we propose you to make an animated color histogram. If you used Gimp, Lightroom or Photoshop, you saw them there. Read more about color histograms&nbsp;<a href="https://en.wikipedia.org/wiki/Color_histogram">here</a>.

The end result swill look like this:

<img decoding="async" data-src="task_images/histogram_example.jpg" width="640" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==" class="lazyload">

Let’s consider the parts of this visualization:

<ul>
<li>The background is the analyzed image. We provide the code which loads the image and calculates color histograms.</li>
<li>The white-edged rectangle is the selection&nbsp;<a href="https://github.com/d3/d3-brush#api-reference"><em>brush</em></a></li>
<li>Three curve plots represent the histograms of red, green and blue pixel values withing the selected area.</li>
</ul>
<h2 id="overlay">Overlay</h2>
Please look at the CSS in&nbsp;<code>exercise/style.css</code>&nbsp;– the rules for&nbsp;<code>figure</code>&nbsp;and&nbsp;<code>.overlay</code>&nbsp;put the SVG on top of the image (the SVG has the class&nbsp;<code>.overlay</code>). The effect is achieved using&nbsp;<code>position: absolute</code>.

<h2 id="brush">Brush</h2>
First let us setup the&nbsp;<a href="https://github.com/d3/d3-brush#api-reference"><em>brush</em></a>&nbsp;(area selection tool). You can example usage of a 2D brush&nbsp;<a href="https://bl.ocks.org/mbostock/f48fcdb929a620ed97877e4678ab15e6">here</a>.

First we need to create a brush object and register the event handler. The function is called when the user finishes changing the selected area. If you prefer to update while the user is moving the area, you can listen to the&nbsp;<code>"brush"</code>&nbsp;event instead of&nbsp;<code>"end"</code>.

<pre><code>var brush = d3.brush().on("end",  () =&gt; {
    // this is called when the selection is changed
});</code></pre>
The selected area is specified in&nbsp;<code>d3.event.selection</code>&nbsp;as&nbsp;<code>[[x_min, y_min], [x_max, y_max]]</code>&nbsp;or&nbsp;<strong>null</strong>&nbsp;if nothing is selected.

We also need to create a visual representation of the brush (the white edged rectangle):

<pre><code>svg.append("g")
    .attr("class", "brush")
    .call(brush);</code></pre>
Create the brush and register the selection event. Print the coordinates of the selected area in the console.

Now that we have the selected area, we can use the provided method&nbsp;<code>getImageHistogramOfArea(x_left, y_top, width, height)</code>&nbsp;to calculate the histograms. Try printing the resulting data.

<h2 id="histogram-plots">Histogram plots</h2>
Now we shall plot the histogram data.

Create the plots for the red, green and blue channels. To draw curves use the&nbsp;<a href="https://d3indepth.com/shapes/#line-generator">line</a>&nbsp;or&nbsp;<a href="https://d3indepth.com/shapes/#area-generator">area</a>&nbsp;generators (given an array of values, they generate the textual representation to be used by the SVG&nbsp;<code>path</code>’s&nbsp;<code>d</code>&nbsp;attribute – see examples under those links). You can use the provided&nbsp;<code>red</code>,&nbsp;<code>green</code>&nbsp;and&nbsp;<code>blue</code>&nbsp;CSS classes to set the colors of the curves.

As usual with d3.js plots, use&nbsp;<a href="https://d3indepth.com/scales/">scales</a>&nbsp;to convert from data values to plot coordinates. The viewBox of the plot is&nbsp;<code>[0, 0, 900, 400]</code>, use the whole area.

You can try plotting some dummy data before you connect it to the selection mechanism – its easier to develop the parts separately.

The Y scale should adapt to the calculated histograms: the upper value of its&nbsp;<code>domain</code>&nbsp;should equal to the maximum value in the histograms. You can call&nbsp;<code>domain</code>&nbsp;again on an existing scale object to change its input range.

<h2 id="cross-origin">Cross-origin</h2>
If you are getting the error on Chrome:

<pre><code>The canvas has been tainted by cross-origin data.</code></pre>
<ul>
<li>Load your site from a local webserver and open&nbsp;<code>localhost:8000</code>&nbsp;in the browser:</li>
</ul>
<pre><code>    cd exercise_dir
    python3 -m http.server</code></pre>
<ul>
<li>Alternatively: it should work in Firefox</li>
</ul>
