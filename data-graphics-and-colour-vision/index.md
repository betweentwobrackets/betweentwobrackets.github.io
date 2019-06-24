
Information graphics should allow all viewers to easily understand raw data. These graphics can also provide interesting and alternative perspectives on a dataset.

> It doesn’t matter how good a chart looks if it doesn’t communicate anything!  
&mdash; [Mike Bostock &mdash; Let’s Make a Bar Chart, III](http://bost.ocks.org/mike/bar/3/#communicating)

Unfortunately, in many cases aesthetics take precedence over clarity, with poor use of colour and little or no labelling. Such graphics are difficult for viewers to decipher, especially viewers with some form of visual impairment.

![Confusing legend colours](../content/donut-confusing-legend-2.svg)

We've all seen this type of chart, from web analytics systems to time trackers and fitness apps. Although this chart might look nice it's really poor at its job, which is to make it easy to understand the raw data.

The above chart works for most people, however approximately 8% of the male population and 0.4% of the female population has some form of colour vision deficiency[^1]. Overall 285 million (~4%) people worldwide suffer some form of visual impairment[^2].

In this article we'll look at the difficulties faced by viewers with impaired colour vision and then define some patterns to minimise these difficulties.

For brevity we'll refer to *Colour Vision Deficiency* as CVD.

### Full Spectrum Confusion

Our contrived example of a chart that seems easy to understand. We've added a helpful legend and the use of bright colours should make it easy to link the segments to their key in the legend.

![Confusing legend colours](../content/donut-confusing-legend-2.svg)

Unfortunately, a viewer with CVD will likely find it difficult to distinguish several colours in this chart. The graphics below use modified colour values to simulate various forms of CVD[^1].

<div class="column-2">
    <img src="./donut-protanopia.svg" alt="Protanopia (L-cone absent)">
    <img src="./donut-deuteranopia.svg" alt="Deuteranopia (M-cone absent)">
    <img src="./donut-tritanopia.svg" alt="Tritanopia (S-cone absent)">
    <img src="./donut-protanomaly.svg" alt="Protanomaly (L-cone defect)">
    <img src="./donut-deuteranomaly-2.svg" alt="Deuteranomaly (M-cone defect)">
    <img src="./donut-tritanomoly.svg" alt="Tritanomaly (S-cone defect)">
</div>

The difference in colour is quite stark. Although it's still possible to differentiate colours at their boundaries it's difficult to link the segments to their keys in the legend.

For example, viewers with deuteranomaly will likely struggle to distinguish data points 'Writing code' and 'Commuting'.

![Deuteranomaly linking segments to keys](../content/donut-deuteranomaly-joins.svg)

Some viewers may even find it impossible to distinguish these colours. For viewers with tritanopia the data points for 'Eating' and 'Debugging' are almost completely identical.

![Tritanopia linking segments to keys](../content/donut-tritanopia-joins.svg)

Linking these segments to the keys requires extra mental effort and in some cases &mdash; from personal experience &mdash; the help of a colour picker tool.

![Colour picker example](../content/donut-deuteranomaly-picker.svg)

Factors such as screen quality, brightness, contrast and even lighting within a room can affect the ability of a viewer to distinguish individual colours.

You may have noticed the order of the legend keys matches the order of the segments, however a viewer &mdash; especially with those with CVD &mdash; cannot be certain of this. For example in a line chart the legend order is not likely to match the order of the data lines at any given point on an axis.

### Better Colour Choices

So how can we choose more helpful colour combinations? Well it seems obvious, choose contrasting colours.

As you might have guessed it's not actually so simple. Even primary-secondary colour combinations have the potential to confuse, depending on the type of CVD a viewer has. Both the blue/magenta and green/yellow colour pairs could be confusing.

<svg id="secondary" class="chart"></svg>

To avoid confusion you could switch magenta for a more contrasting tertiary colour like orange and the green for a grey. 

<p id="modified-secondary" class="d3-colorwheels">
</p>

Below are the same colour wheels but modified to simulate what a viewer with Deuteranopia (~5% of viewers) would see.

<p id="false-color-modified-secondary" class="d3-colorwheels">
</p>

Although not completely foolproof this combination of colours is less likely to cause confusion.

Using colour alone to encode information is not a reliable way to cater for all forms of CVD. Depending on the type, viewers with dichromacy (~2% of males) will struggle with some of the combinations in the *improved* wheel above.

<p id="false-dichromacy-secondary" class="d3-colorwheels">
</p>

That said, choosing contrasting colours is a good start in helping those with CVD understand your data. Viewers with anomolous trichromacy (~6% of males and ~0.01% of females) will be less likely to struggle with contrasting colour choices.


### Patterns to the Rescue

Rather than relying solely on colour to display information patterns provide a better way for viewers to differentiate information.

![Colour chart with patterns](../content/donut-patterns-4.svg)

Now a viewer with CVD can map the segments to the keys.

A great example of patterns being used to aid visually impaired viewers is the [London Underground Map (PDF)](https://tfl.gov.uk/cdn/static/cms/documents/large-print-tube-map.pdf).

![Colour Tube Map](../content/colour-tube-map.png)

The same map can also be viewed in [black &amp; white (PDF)](https://tfl.gov.uk/cdn/static/cms/documents/bw-large-print-map.pdf).

![Black and White Tube Map](../content/black-white-tube-map-1.png)

As well as helping viewers with CVD the high contrast of the black and white map helps viewers with other visual impairments.

Rather than having two versions the map could use colour and patterns to provide a more accessible version of the standard map.

![Colour Pattern Tube Map](../content/colour-pattern-tube-map-1.png)

### "But it looks ugly!"

The designer in you is likely not impressed. However, the desire for aesthetics is one of the main drivers for inaccessible information design.

The *primary* goal of information design should be to make information digestible to as many viewers as possible, aesthetics should always come second. However, it really should be possible to create information design that is both beautiful and usable.

If it's not desirable to incorporate patterns into a graphic then instead you can offer the option to view a more accessible version. For example: [Trello](https://trello.com) offers a *color blind friendly mode* when viewing labels.

<img src="./trello-labels-colourblind.png" alt="Trello Color Blind Friendly Mode" width="300">

Note that the setting isn't hidden away but is placed where the viewer needs it most.

### Label Your Data

Considering the issues with colour perception and the aesthetic drawbacks of using patterns, an alternative is to label your graphics. If the segments are labelled then the legend can be completely removed.

![Labelled donut chart](../content/donut-labelled-3.svg)

The viewer no longer has to waste mental effort linking the legend keys to the data in the graph. The added bonus is that we don't need crazy patterns.

Ideally the labels should be visible by default as in the example above. Alternatively the labels can be shown when the viewer interacts with the graphic. [Chart.js](http://www.chartjs.org/), [Chartist.js](https://gionkunz.github.io/chartist-js/) and [Google Charts](https://developers.google.com/chart/) (and many others) use interactive labels. When the viewer interacts with a segment/data point a label tooltip is shown.

<p id="library-examples" class="column-2">
    <img src="./chartjs-labels.png" alt="Chart JS Labels">
    <img src="./google-charts-labels.png" alt="Google Charts Labels">
</p>

### Conclusion

Accessibility is of primary importance when creating data graphics. Aesthetics should always come second but in many cases can complement the accessibility of a design.

The best way to make your graphics accessible is to provide labels, ideally without the need for viewer interaction. Don't use colour as the only way for your viewers to understand your graphic. If it isn't possible for your graphic to provide labels then use sensible colour combinations and interactive labels (tooltips).

Below are some useful resources and tools that will help you to create better graphics.

### Useful Resources

- [Sim Daltonism &mdash; simulate different forms of CVD](https://michelf.ca/projects/sim-daltonism/)
- [Contrast Ratio &mdash; colour contrast checker](http://leaverou.github.io/contrast-ratio/)
- [Tips for Designing Scientific Figures for Color Blind Readers](http://www.somersault1824.com/tips-for-designing-scientific-figures-for-color-blind-readers/)
- [Choosing Safe Colours](http://safecolours.rigdenage.com/colourchoice.html)

---

### References

[^1]: http://www.colour-blindness.com/general/prevalence/
[^2]: http://www.who.int/mediacentre/factsheets/fs282/en/

<style>
svg {
    width: 100%;
    font-family: "Helvetica", Arial, sans-serif;
    font-weight: 100;
}
svg text {
    font-size: 120%;
    fill: #000;
}
svg .arc path {
   stroke: #fff;
}
.d3-colorwheels,
.column-2 {
    float: left;
    width: 127%;
    margin-left: -13.5%;
}
.d3-colorwheels svg {
    display: block;
    float: left;
    width: 31.33333333333333%;
    margin: 0 1%;
}
.column-2 {
    position: relative;
}
.column-2 img {
    display: inline;
    max-width: none;
    width: 45%;
    margin: 0 2%;
    left: 0;
    vertical-align: middle;
    -webkit-transform: translateX(0);
    -ms-transform: translateX(0);
    transform: translateX(0)
}
@media only screen and (max-width: 600px) {
    .d3-colorwheels,
    .column-2 {
        width: 100%;
        margin-left: 0;
    }
    .d3-colorwheels svg {
        width: 98%;
        margin: 0 1%;
    }
    .column-2 img {
        width: 100%;
        margin: 0.6em 0;
    }
}
</style>
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.6/d3.min.js"></script>
<script src="./d3-colorwheel.js"></script>
<script>
var trueColor = [  
    {
        title: "Primary Colours",
        colors: [
            {label: 'Red', color: "#f00"},
            {label: 'Green', color: "#0f0"},
            {label: 'Blue', color: "#00f"}
        ]
    },
    {
        title: "Secondary Colours",
        colors: [
            {label: "Red", color: "#f00"},
            {label: "Yellow", color: "#ff0"},
            {label: "Green", color: "#0f0"},
            {label: "Cyan", color: "#0ff"},
            {label: "Blue", color: "#00f"},
            {label: "Magenta", color: "#f0f"}
        ]
    },
    {
        title: "Improved Secondary Colours",
        colors: [
            {label: "Red", color: "#f00"},
            {label: "Yellow", color: "#ff0"},
            {label: "Grey", color: "#888"},
            {label: "Cyan", color: "#0ff"},
            {label: "Blue", color: "#00f"},
            {label: "Orange", color: "rgb(255, 127, 0)"}
        ]
    }
];

var falseColor = [  
    {
        title: "Primary Colours",
        colors: [
            {label: 'Red', color: "#c76527"},
            {label: 'Green', color: "#d4e276"},
            {label: 'Blue', color: "#014df3"}
        ]
    },
    {
        title: "Secondary Colours",
        colors: [
            {label: 'Red', color: "#c76527"},
            {label: "Yellow", color: "#fcf7bf"},
            {label: 'Green', color: "#d4e276"},
            {label: "Cyan", color: "#c0eafd"},
            {label: 'Blue', color: "#014df3"},
            {label: "Magenta", color: "#a779f4"}
        ]
    },
    {
        title: "Improved Secondary Colours",
        colors: [
            {label: 'Red', color: "#c76527"},
            {label: "Yellow", color: "#fcf7bf"},
            {label: 'Grey', color: "#908488"},
            {label: "Cyan", color: "#c0eafd"},
            {label: 'Blue', color: "#014df3"},
            {label: "Orange", color: "#db8a2c"}
        ]
    }
];

var dichromacyColor = [  
    {
        title: "Protanopia",
        colors: [
            {label: 'Red', color: "#908020"},
            {label: "Yellow", color: "#fff5d0"},
            {label: 'Grey', color: "#8a8787"},
            {label: "Cyan", color: "#e4e2ed"},
            {label: 'Blue', color: "#054afb"},
            {label: "Magenta", color: "#af9d21"}
        ]
    },
    {
        title: "Deuteranopia",
        colors: [
            {label: 'Red', color: "#a3791f"},
            {label: "Yellow", color: "#fef3e5"},
            {label: 'Grey', color: "#948388"},
            {label: "Cyan", color: "#e6defe"},
            {label: 'Blue', color: "#015ced"},
            {label: "Magenta", color: "#c69327"}
        ]
    },
    {
        title: "Tritanopia",
        colors: [
            {label: 'Red', color: "#ed4730"},
            {label: "Yellow", color: "#fcf0f9"},
            {label: 'Grey', color: "#898691"},
            {label: "Cyan", color: "#9cf1fd"},
            {label: 'Blue', color: "#27626a"},
            {label: "Orange", color: "#ef6770"}
        ]
    }
];

var colorWheel = d3.colorWheel().width(300).height(360);

d3.select("svg#secondary")  
    .datum(trueColor[1])
    .call(colorWheel);

d3.select("#modified-secondary").selectAll("svg")  
    .data(trueColor)
  .enter().append("svg")
    .call(colorWheel);

d3.select("#false-color-modified-secondary").selectAll("svg")  
    .data(falseColor)
  .enter().append("svg")
    .call(colorWheel);

d3.select("#false-dichromacy-secondary").selectAll("svg")  
    .data(dichromacyColor)
  .enter().append("svg")
    .call(colorWheel);
</script>