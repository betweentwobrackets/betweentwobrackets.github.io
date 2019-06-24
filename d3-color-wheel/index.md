D3 Color Wheel was created as part of an upcoming article on the use of colour in data graphics. Using the D3 pie layout the chart displays a colour wheel generated from JSON data.

[Download from Github](https://github.com/betweentwobrackets/d3-colorwheel)

### Example

<p id="colour-wheels"></p>

#### index.html

```html
<script src="d3.min.js"></script>
<script src="d3-colorwheel.js"></script>

<style>
svg {
    font-family: "Helvetica", Arial, sans-serif;
    font-weight: 100;
}
.arc path {
   stroke: #fff;
}
.arc text {
    font-size: 120%;
    fill: #aaa;
}
</style>

<p id="colour-wheels"></p>

<script src="color-wheels.js"></script>
```

#### color-wheels.js

```javascript
var data = [
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
        title: "Modified Secondary Colours",
        colors: [
            {label: "Red", color: "#f00"},
            {label: "Yellow", color: "#ff0"},
            {label: "Grey", color: "#888"},
            {label: "Cyan", color: "#0ff"},
            {label: "Blue", color: "#00f"},
            {label: "Orange", color: "#f67e18"}
        ]
    }
];

var colorWheel = d3.colorWheel().width(300).height(360);

var svg = d3.select("#colour-wheels").selectAll("svg")
    .data(data)
  .enter().append("svg")
    .call(colorWheel);
```

<style type="text/css" scoped>
svg {
    font-family: "Helvetica", Arial, sans-serif;
    font-weight: 100;
}
.arc path {
   stroke: #fff;
}
.arc text {
    font-size: 120%;
    fill: #000;
}
#colour-wheels {
    float: left;
    width: 127%;
    margin-left: -13.5%;
}
#colour-wheels svg {
    display: block;
    float: left;
    width: 31.33333333333333%;
    margin: 0 1%;
}
@media only screen and (max-width: 500px) {
    #colour-wheels {
        width: 100%;
        margin-left: 0;
    }
    #colour-wheels svg {
        width: 98%;
        margin: 0 1%;
    }
}
</style>

<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.6/d3.min.js" charset="utf-8"></script>
<script src="./d3-colorwheel.js"></script>

<script>
var data = [
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
        title: "Modified Secondary Colours",
        colors: [
            {label: "Red", color: "#f00"},
            {label: "Yellow", color: "#ff0"},
            {label: "Grey", color: "#888"},
            {label: "Cyan", color: "#0ff"},
            {label: "Blue", color: "#00f"},
            {label: "Orange", color: "#f67e18"}
        ]
    }
];

var colorWheel = d3.colorWheel().width(300).height(360);

var svg = d3.select("#colour-wheels").selectAll("svg")
    .data(data)
  .enter().append("svg")
    .call(colorWheel);
</script>
