# 8.Traditional DOM manipulation with D3
## Spreadsheet
### Making a spreadsheet with table
[Fig_08_02.html][1]

```html
<html>
<head>
  <title>D3 in Action Chapter 8 - Example 1</title>
  <meta charset="utf-8" />
<script src="d3.v3.min.js" type="text/JavaScript"></script>
</head>
<style>
tr {
  border: 1px gray solid;
}

td {
  border: 2px black solid;
}

div.table {
  position:relative;
}
div.data {
  position: absolute;
  width: 90px;
  padding: 0 5px;
}

div.head {
  position: absolute;
}

div.datarow {
  position: absolute;
  width: 100%;
  border-top: 2px black solid;
  background: white;
  height: 35px;
  overflow: hidden;
}

div.gallery {
  position: relative;
}

img.infinite {
  position: absolute;
  background: rgba(255,255,255,0);
  border-width: 1px;
  border-style: solid;
  border-color: rgba(0,0,0,0);
}

</style>
<body>
<div id="traditional">
</div>
</body>
  <footer>

<script>
d3.json("tweets.json",function(error,data) { createSpreadsheet(data.tweets)});

      function createSpreadsheet(incData) {

        var keyValues = d3.keys(incData[0])//This won’t work if your objects have differing numbers of attributes, but usually that’s not the case.

        d3.select("#traditional")
        .append("table")

        d3.select("table")
        .append("tr")
        .attr("class", "head")
        .selectAll("th")
        .data(keyValues)//Creates our header row from our keys
        .enter()
        .append("th")
        .html(function (d) {return d})

        d3.select("table")
        .selectAll("tr.data")
        .data(incData).enter()//Creates each row for a tweet
        .append("tr")
        .attr("class", "data")

        d3.selectAll("tr")
        .selectAll("td")
        .data(function(d) {return d3.entries(d)})//Creates each cell for an entry in each datapoint
        .enter()
        .append("td")
        .html(function (d) {return d.value})
      }
</script>
</footer>
</html>
```

![f8.2](fig8_2.png)

### Making a spreadsheet with divs
[Fig_08_03.html][2]

```html
<html>
<head>
  <title>D3 in Action Chapter 8 - Example 2</title>
  <meta charset="utf-8" />
<script src="d3.v3.min.js" type="text/JavaScript"></script>
</head>
<style>
tr {
  border: 1px gray solid;
}

td {
  border: 2px black solid;
}

div.table {
  position:relative;
}
div.data {
  position: absolute;
  width: 90px;
  padding: 0 5px;
}

div.head {
  position: absolute;
}

div.datarow {
  position: absolute;
  width: 100%;
  border-top: 2px black solid;
  background: white;
  height: 35px;
  overflow: hidden;
}

div.gallery {
  position: relative;
}

img.infinite {
  position: absolute;
  background: rgba(255,255,255,0);
  border-width: 1px;
  border-style: solid;
  border-color: rgba(0,0,0,0);
}

</style>
<body>
<div id="traditional">
</div>
</body>
  <footer>

<script>
d3.json("tweets.json",function(error,data) { createSpreadsheet(data.tweets)});

      function createSpreadsheet(incData) {

        var keyValues = d3.keys(incData[0])

        d3.select("#traditional")
        .append("div")
        .attr("class", "table")//It’s a <div.table>, not a <table>.

        d3.select("div.table")
        .append("div")
        .attr("class", "head")
        .selectAll("div.data")
        .data(keyValues)
        .enter()
        .append("div")
        .attr("class", "data")
        .html(function (d) {return d})
        .style("left", function(d,i) {return (i * 100) + "px"});//Instead of x/y or transform, HTML elements have top/ bottom/left/ right

        d3.select("div.table")
        .selectAll("div.datarow")
        .data(incData, function(d) {return d.content})
        .enter()
        .append("div")
        .attr("class", "datarow")
        .style("top", function(d,i) {return (40 + (i * 40)) + "px"});

        d3.selectAll("div.datarow")
        .selectAll("div.data")
        .data(function(d) {return d3.entries(d)})
        .enter()
        .append("div")
        .attr("class", "data")
        .html(function (d) {return d.value})
        .style("left", function(d,i,j) {return (i * 100) + "px"});
      }

</script>
</footer>
</html>
```

![f8.3](fig8_3.png)

### Animating our spreadsheet
[Fig_08_04.html][3]

```html
<html>
<head>
  <title>D3 in Action Chapter 8 - Example 3</title>
  <meta charset="utf-8" />
<script src="d3.v3.min.js" type="text/JavaScript"></script>
</head>
<style>
tr {
  border: 1px gray solid;
}

td {
  border: 2px black solid;
}

div.table {
  position:relative;
}
div.data {
  position: absolute;
  width: 90px;
  padding: 0 5px;
}

div.head {
  position: absolute;
}

div.datarow {
  position: absolute;
  width: 100%;
  border-top: 2px black solid;
  background: white;
  height: 35px;
  overflow: hidden;
}

div.gallery {
  position: relative;
}

img.infinite {
  position: absolute;
  background: rgba(255,255,255,0);
  border-width: 1px;
  border-style: solid;
  border-color: rgba(0,0,0,0);
}

</style>
<body>
<div id="traditional">
</div>
</body>
  <footer>

<script>
d3.json("tweets.json",function(error,data) { createSpreadsheet(data.tweets)});

      function createSpreadsheet(incData) {

        var keyValues = d3.keys(incData[0])

        d3.select("#traditional")
        .append("div")
        .attr("class", "table")

        d3.select("div.table")
        .append("div")
        .attr("class", "head")
        .selectAll("div.data")
        .data(keyValues)
        .enter()
        .append("div")
        .attr("class", "data")
        .html(function (d) {return d})
        .style("left", function(d,i) {return (i * 100) + "px"});

        d3.select("div.table")
        .selectAll("div.datarow")
        .data(incData, function(d) {return d.content})
        .enter()
        .append("div")
        .attr("class", "datarow")
        .style("top", function(d,i) {return (40 + (i * 40)) + "px"});

        d3.selectAll("div.datarow")
        .selectAll("div.data")
        .data(function(d) {return d3.entries(d)})
        .enter()
        .append("div")
        .attr("class", "data")
        .html(function (d) {return d.value})
        .style("left", function(d,i,j) {return (i * 100) + "px"});

        d3.select("#traditional").insert("button", ".table").on("click", sortSheet).html("sort")
        d3.select("#traditional").insert("button", ".table").on("click", restoreSheet).html("restore")

function sortSheet() {
          var dataset = d3.selectAll("div.datarow").data();
            dataset.sort(function(a,b) {
              var a = new Date(a.timestamp);
              var b = new Date(b.timestamp);
            return a>=b ? 1 : (a<b ? -1 : 0);
            })
            d3.selectAll("div.datarow")
            .data(dataset, function(d) {return d.content})
            .transition()
            .duration(2000)
            .style("top", function(d,i) {return (40 + (i * 40)) + "px"});
        }

        function restoreSheet() {
          d3.selectAll("div.datarow")
            .transition()
            .duration(2000)
            .style("top", function(d,i) {return (40 + (i * 40)) + "px"});
        }

      }

</script>
  </footer>

</html>
```

![f8.4](fig8_4.png)

[Fig_08_05.html][4]

```html
<html>
<head>
  <title>D3 in Action Chapter 8 - Example 4</title>
  <meta charset="utf-8" />
<script src="d3.v3.min.js" type="text/JavaScript"></script>
</head>
<style>
tr {
  border: 1px gray solid;
}

td {
  border: 2px black solid;
}

div.table {
  position:relative;
}
div.data {
  position: absolute;
  width: 90px;
  padding: 0 5px;
}

div.head {
  position: absolute;
}

div.datarow {
  position: absolute;
  width: 100%;
  border-top: 2px black solid;
  background: white;
  height: 35px;
  overflow: hidden;
}

div.gallery {
  position: relative;
}

img.infinite {
  position: absolute;
  background: rgba(255,255,255,0);
  border-width: 1px;
  border-style: solid;
  border-color: rgba(0,0,0,0);
}

</style>
<body>
<div id="traditional">
</div>
</body>
  <footer>

<script>
d3.json("tweets.json",function(error,data) { createSpreadsheet(data.tweets)});

      function createSpreadsheet(incData) {

        var keyValues = d3.keys(incData[0])

        d3.select("#traditional")
        .append("div")
        .attr("class", "table")

        d3.select("div.table")
        .append("div")
        .attr("class", "head")
        .selectAll("div.data")
        .data(keyValues)
        .enter()
        .append("div")
        .attr("class", "data")
        .html(function (d) {return d})
        .style("left", function(d,i) {return (i * 100) + "px"});

        d3.select("div.table")
        .selectAll("div.datarow")
        .data(incData, function(d) {return d.content})
        .enter()
        .append("div")
        .attr("class", "datarow")
        .style("top", function(d,i) {return (40 + (i * 40)) + "px"});

        d3.selectAll("div.datarow")
        .selectAll("div.data")
        .data(function(d) {return d3.entries(d)})
        .enter()
        .append("div")
        .attr("class", "data")
        .html(function (d) {return d.value})
        .style("left", function(d,i,j) {return (i * 100) + "px"});


        d3.select("#traditional").insert("button", ".table").on("click", sortColumns).html("sort columns ")
        d3.select("#traditional").insert("button", ".table").on("click", restoreColumns).html("restore columns")

        d3.select("#traditional").insert("button", ".table").on("click", sortSheet).html("sort")
        d3.select("#traditional").insert("button", ".table").on("click", restoreSheet).html("restore")

function sortSheet() {
          var dataset = d3.selectAll("div.datarow").data();
            dataset.sort(function(a,b) {
              var a = new Date(a.timestamp);
              var b = new Date(b.timestamp);
            return a>=b ? 1 : (a<b ? -1 : 0);
            })
            d3.selectAll("div.datarow")
            .data(dataset, function(d) {return d.content})
            .transition()
            .duration(2000)
            .style("top", function(d,i) {return (40 + (i * 40)) + "px"});
        }

        function restoreSheet() {
          d3.selectAll("div.datarow")
            .transition()
            .duration(2000)
            .style("top", function(d,i) {return (40 + (i * 40)) + "px"});
        }
        function sortColumns() {
          d3.selectAll("div.datarow")
          .selectAll("div.data")
            .transition()
            .duration(2000)
        .style("left", function(d,i,j) {return (Math.abs(i - 4) * 100) + "px"});
        }

        function restoreColumns() {
          d3.selectAll("div.datarow")
          .selectAll("div.data")
            .transition()
            .duration(2000)
        .style("left", function(d,i,j) {return (i * 100) + "px"});
        }

      }

</script>
  </footer>

</html>
```

![f8.5](fig8_5.png)

## Canvas
[Fig_08_06.html][5]

```html
<html>
<head>
  <title>D3 in Action Chapter 8 - Example 5</title>
  <meta charset="utf-8" />
<script src="d3.v3.min.js" type="text/JavaScript"></script>
</head>
<style>
tr {
  border: 1px gray solid;
}

td {
  border: 2px black solid;
}

div.table {
  position:relative;
}
div.data {
  position: absolute;
  width: 90px;
  padding: 0 5px;
}

div.head {
  position: absolute;
}

div.datarow {
  position: absolute;
  width: 100%;
  border-top: 2px black solid;
  background: white;
  height: 35px;
  overflow: hidden;
}

div.gallery {
  position: relative;
}

img.infinite {
  position: absolute;
  background: rgba(255,255,255,0);
  border-width: 1px;
  border-style: solid;
  border-color: rgba(0,0,0,0);
}

</style>
<body>
<div id="traditional">
</div>
</body>
  <footer>

<script>
d3.select("#traditional")
.append("canvas")
.attr("height", 500)
.attr("width", 500);

  var context = d3.select("canvas").node().getContext("2d");

  context.strokeStyle = "black";
  context.lineWidth = 2;
  context.fillStyle = "red";
  context.beginPath();
  context.arc(250,250,200,0,2*Math.PI);
  context.fill();
  context.stroke();

  context.textAlign = "center";
  context.font="200px Georgia";
  context.fillStyle = "black";
  context.textAligh = "center";
  context.fillText("1",250,250);
</script>
</footer>
</html>
```

![f8.6](fig8_6.png)

[Fig_08_08.html][6]

```html
<html>
<head>
  <title>D3 in Action Chapter 8 - Example 6</title>
  <meta charset="utf-8" />
<script src="d3.v3.min.js" type="text/JavaScript"></script>
<script src="colorbrewer.js" type="text/JavaScript"></script>
</head>
<style>
tr {
  border: 1px gray solid;
}

td {
  border: 2px black solid;
}

div.table {
  position:relative;
}
div.data {
  position: absolute;
  width: 90px;
  padding: 0 5px;
}

div.head {
  position: absolute;
}

div.datarow {
  position: absolute;
  width: 100%;
  border-top: 2px black solid;
  background: white;
  height: 35px;
  overflow: hidden;
}

div.gallery {
  position: relative;
}

img.infinite {
  position: absolute;
  background: rgba(255,255,255,0);
  border-width: 1px;
  border-style: solid;
  border-color: rgba(0,0,0,0);
}

</style>
<body>
<div id="traditional">
</div>
</body>
  <footer>

<script>
  imageArray = [];
 d3.select("#traditional").append("canvas").attr("height", 500).attr("width", 500);

  var context = d3.select("canvas").node().getContext("2d");
  context.textAlign = "center";
  context.font="200px Georgia";
  colorScale = d3.scale.quantize().domain([0,1]).range(colorbrewer.Reds[7]);

  lineScale = d3.scale.quantize().domain([0,1]).range([10,40]);
  for (var x=0;x<100;x++) {
  context.clearRect(0,0,500,500);
  context.strokeStyle = colorScale(Math.random());
  context.lineWidth = lineScale(Math.random());
  context.fillStyle = colorScale(Math.random());
  context.beginPath();
  context.arc(250,250,200,0,2*Math.PI);
  context.fill();
  context.stroke();

  context.fillStyle = "black";
  context.fillText(x,250,280);
  var dataURL = d3.select("canvas").node().toDataURL();
  imageArray.push({x: x, url: dataURL});
  }
  d3.select("#traditional")
  .append("div").attr("class", "gallery")
  .selectAll("img").data(imageArray)
  .enter().append("img")
  .attr("src", function(d) {return d.url})
  .style("height", "50px")
  .style("float", "left")


</script>
  </footer>

</html>
```

![f8.8](fig8_8.png)

## Image gallery
[Fig_08_09.html][7]

```html
<html>
<head>
  <title>D3 in Action Chapter 8 - Example 7</title>
  <meta charset="utf-8" />
<script src="d3.v3.min.js" type="text/JavaScript"></script>
<script src="colorbrewer.js" type="text/JavaScript"></script>
</head>
<style>
tr {
  border: 1px gray solid;
}

td {
  border: 2px black solid;
}

div.table {
  position:relative;
}
div.data {
  position: absolute;
  width: 90px;
  padding: 0 5px;
}

div.head {
  position: absolute;
}

div.datarow {
  position: absolute;
  width: 100%;
  border-top: 2px black solid;
  background: white;
  height: 35px;
  overflow: hidden;
}

div.gallery {
  position: relative;
}

img.infinite {
  position: absolute;
  background: rgba(255,255,255,0);
  border-width: 1px;
  border-style: solid;
  border-color: rgba(0,0,0,0);
}

</style>
<body>
<div id="traditional">
</div>
</body>
  <footer>

<script>
  imageArray = [];
 d3.select("#traditional").append("canvas").attr("height", 500).attr("width", 500);

  var context = d3.select("canvas").node().getContext("2d");
  context.textAlign = "center";
  context.font="200px Georgia";
  colorScale = d3.scale.quantize().domain([0,1]).range(colorbrewer.Reds[7]);

  lineScale = d3.scale.quantize().domain([0,1]).range([10,40]);
  for (var x=0;x<100;x++) {
  context.clearRect(0,0,500,500);
  context.strokeStyle = colorScale(Math.random());
  context.lineWidth = lineScale(Math.random());
  context.fillStyle = colorScale(Math.random());
  context.beginPath();
  context.arc(250,250,200,0,2*Math.PI);
  context.fill();
  context.stroke();

  context.fillStyle = "black";
  context.fillText(x,250,280);
  var dataURL = d3.select("canvas").node().toDataURL();
  imageArray.push({x: x, url: dataURL});
  }

  imgPerLine = 8;
  d3.select("canvas").remove();
  d3.select("#traditional")
  .append("div").attr("class", "gallery")
  .selectAll("img").data(imageArray).enter().append("img")
  .attr("class", "infinite")
  .attr("src", function(d) {return d.url})

  redrawGallery();

  function redrawGallery() {
var newWidth = parseFloat(d3.select("div.gallery").node().clientWidth);
      var imageSize = newWidth / imgPerLine;
      function imgX(x) {
        return Math.floor(x / imgPerLine) * imageSize;
      }
      function imgY(x) {
        return Math.floor(x%imgPerLine * imageSize)
      }
      d3.selectAll("img")
      .style("width", newWidth / imgPerLine)
      .style("top", function(d) {return imgX(d.x)})
      .style("left", function(d) {return imgY(d.x)})
  }

  window.onresize = function(event) {
	redrawGallery();
  }

</script>
</footer>
</html>
```

![f8.9](fig8_9.png)


[Fig_08_10.html][8]

```html
<html>
<head>
  <title>D3 in Action Chapter 8 - Example 8</title>
  <meta charset="utf-8" />
<script src="d3.v3.min.js" type="text/JavaScript"></script>
<script src="colorbrewer.js" type="text/JavaScript"></script>
</head>
<style>
tr {
  border: 1px gray solid;
}

td {
  border: 2px black solid;
}

div.table {
  position:relative;
}
div.data {
  position: absolute;
  width: 90px;
  padding: 0 5px;
}

div.head {
  position: absolute;
}

div.datarow {
  position: absolute;
  width: 100%;
  border-top: 2px black solid;
  background: white;
  height: 35px;
  overflow: hidden;
}

div.gallery {
  position: relative;
}

img.infinite {
  position: absolute;
  background: rgba(255,255,255,0);
  border-width: 1px;
  border-style: solid;
  border-color: rgba(0,0,0,0);
}

</style>
<body>
<div id="traditional">
</div>
</body>
  <footer>

<script>
  imageArray = [];
 d3.select("#traditional").append("canvas").attr("height", 500).attr("width", 500);

  var context = d3.select("canvas").node().getContext("2d");
  context.textAlign = "center";
  context.font="200px Georgia";
  colorScale = d3.scale.quantize().domain([0,1]).range(colorbrewer.Reds[7]);

  lineScale = d3.scale.quantize().domain([0,1]).range([10,40]);
  for (var x=0;x<100;x++) {
  context.clearRect(0,0,500,500);
  context.strokeStyle = colorScale(Math.random());
  context.lineWidth = lineScale(Math.random());
  context.fillStyle = colorScale(Math.random());
  context.beginPath();
  context.arc(250,250,200,0,2*Math.PI);
  context.fill();
  context.stroke();

  context.fillStyle = "black";
  context.fillText(x,250,280);
  var dataURL = d3.select("canvas").node().toDataURL();
  imageArray.push({x: x, url: dataURL});
  }

  imgPerLine = 8;
  d3.select("canvas").remove();
  d3.select("#traditional")
  .append("div").attr("class", "gallery")
  .selectAll("img").data(imageArray).enter().append("img")
  .attr("class", "infinite")
  .attr("src", function(d) {return d.url})

  redrawGallery();

d3.selectAll("img")
.on("mouseover", highlightImage)
.on("mouseout", dehighlightImage)


  function redrawGallery() {
var newWidth = parseFloat(d3.select("div.gallery").node().clientWidth);
      var imageSize = newWidth / imgPerLine;
      function imgX(x) {
        return Math.floor(x / imgPerLine) * imageSize;
      }
      function imgY(x) {
        return Math.floor(x%imgPerLine * imageSize)
      }
      d3.selectAll("img")
      .style("width", newWidth / imgPerLine)
      .style("top", function(d) {return imgX(d.x)})
      .style("left", function(d) {return imgY(d.x)})
  }

      function highlightImage(d) {
      var newWidth = parseFloat(d3.select("div.gallery").node().clientWidth);
      var imageSize = newWidth / 8;
    d3.select(this).transition().duration(500).style("width", imageSize * 2)
    .style("background", "rgba(255,255,255,1)")
    .style("border-color", "rgba(0,0,0,1)");
    this.parentNode.appendChild(this)

  }

  function dehighlightImage(d) {
      var newWidth = parseFloat(d3.select("div.gallery").node().clientWidth);
      var imageSize = newWidth / 8;
    d3.select(this).transition().duration(500).style("width", imageSize)
    .style("background", "rgba(255,255,255,0)")
    .style("border-color", "rgba(0,0,0,0)")
  }

  window.onresize = function(event) {
	redrawGallery();
  }



</script>
  </footer>

</html>
```

![f8.10](fig8_10.png)

[Fig_08_11.html][9]

```html
<html>
<head>
  <title>D3 in Action Chapter 8 - Example 9</title>
  <meta charset="utf-8" />
<script src="d3.v3.min.js" type="text/JavaScript"></script>
<script src="colorbrewer.js" type="text/JavaScript"></script>
</head>
<style>
tr {
  border: 1px gray solid;
}

td {
  border: 2px black solid;
}

div.table {
  position:relative;
}
div.data {
  position: absolute;
  width: 90px;
  padding: 0 5px;
}

div.head {
  position: absolute;
}

div.datarow {
  position: absolute;
  width: 100%;
  border-top: 2px black solid;
  background: white;
  height: 35px;
  overflow: hidden;
}

div.gallery {
  position: relative;
}

img.infinite {
  position: absolute;
  background: rgba(255,255,255,0);
  border-width: 1px;
  border-style: solid;
  border-color: rgba(0,0,0,0);
}

</style>
<body>
<div id="traditional">
</div>
</body>
  <footer>

<script>
  imageArray = [];
 d3.select("#traditional").append("canvas").attr("height", 500).attr("width", 500);

  var context = d3.select("canvas").node().getContext("2d");
  context.textAlign = "center";
  context.font="200px Georgia";
  colorScale = d3.scale.quantize().domain([0,1]).range(colorbrewer.Reds[7]);

  lineScale = d3.scale.quantize().domain([0,1]).range([10,40]);
  for (var x=0;x<100;x++) {
  context.clearRect(0,0,500,500);
  context.strokeStyle = colorScale(Math.random());
  context.lineWidth = lineScale(Math.random());
  context.fillStyle = colorScale(Math.random());
  context.beginPath();
  context.arc(250,250,200,0,2*Math.PI);
  context.fill();
  context.stroke();

  context.fillStyle = "black";
  context.fillText(x,250,280);
  var dataURL = d3.select("canvas").node().toDataURL();
  imageArray.push({x: x, url: dataURL});
  }

  imgPerLine = 8;
  d3.select("canvas").remove();
  d3.select("#traditional")
  .append("div").attr("class", "gallery")
  .selectAll("img").data(imageArray).enter().append("img")
  .attr("class", "infinite")
  .attr("src", function(d) {return d.url})

  redrawGallery();

d3.selectAll("img")
.on("mouseover", highlightImage)
.on("mouseout", dehighlightImage)

d3.select("div.gallery").style("height", "50%").style("overflow","scroll").style("border", "2px black solid")

d3.select("#traditional").append("select")
.on("change", zoomTo)
.selectAll("option").data(d3.selectAll("img").data()).enter().append("option").attr("value", function(d) {return d.x}).html(function(d) {return "Image #" +d.x})


  function redrawGallery() {
var newWidth = parseFloat(d3.select("div.gallery").node().clientWidth);
      var imageSize = newWidth / imgPerLine;
      function imgX(x) {
        return Math.floor(x / imgPerLine) * imageSize;
      }
      function imgY(x) {
        return Math.floor(x%imgPerLine * imageSize)
      }
      d3.selectAll("img")
      .style("width", newWidth / imgPerLine)
      .style("top", function(d) {return imgX(d.x)})
      .style("left", function(d) {return imgY(d.x)})
  }

      function highlightImage(d) {
      var newWidth = parseFloat(d3.select("div.gallery").node().clientWidth);
      var imageSize = newWidth / 8;
    d3.select(this).transition().duration(500).style("width", imageSize * 2)
    .style("background", "rgba(255,255,255,1)")
    .style("border-color", "rgba(0,0,0,1)");
    this.parentNode.appendChild(this)

  }

  function dehighlightImage(d) {
      var newWidth = parseFloat(d3.select("div.gallery").node().clientWidth);
      var imageSize = newWidth / 8;
    d3.select(this).transition().duration(500).style("width", imageSize)
    .style("background", "rgba(255,255,255,0)")
    .style("border-color", "rgba(0,0,0,0)")
  }

  function zoomTo() {
      var selectValue = d3.select("select").node().value;
      var newWidth = parseFloat(d3.select("div.gallery").node().clientWidth);
      var imageSize = newWidth / 8;
  var scrollTarget = Math.floor(selectValue / 8) * imageSize;

  d3.selectAll("img").filter(function(d) {return d.x == selectValue})
  .transition().duration(2000).style("width", imageSize * 2)
    .style("background", "rgba(255,255,255,1)")
    .style("border-color", "rgba(0,0,0,1)");

  var selectedNode = d3.selectAll("img")
.filter(function(d) {return d.x == selectValue}).node();
  selectedNode.parentNode.appendChild(selectedNode);

    d3.select("div.gallery").transition().duration(2000)
        .tween("scrollTween", scrollTopTween(scrollTarget));

function scrollTopTween(scrollTo) {
    return function() {
        var i = d3.interpolateNumber(this.scrollTop, scrollTo);
        return function(t) { this.scrollTop = i(t); };
    };
}
}

  window.onresize = function(event) {
	redrawGallery();
  }

</script>
</footer>
</html>
```

![f8.11](fig8_11.png)

[1]: Fig_08_02.html
[2]: Fig_08_03.html
[3]: Fig_08_04.html
[4]: Fig_08_05.html
[5]: Fig_08_06.html
[6]: Fig_08_08.html
[7]: Fig_08_09.html
[8]: Fig_08_10.html
[9]: Fig_08_11.html
