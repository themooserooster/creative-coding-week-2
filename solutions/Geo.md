Geo's solution
==============

[http://tributary.io/inlet/6444326](http://tributary.io/inlet/6444326)

This solution uses [Tributary](http://tributary.io/) and [d3.js](http://d3js.org)
```
var svg = d3.select('svg');

var drawLine =  function(x1,y1,x2,y2) {
  svg.append("svg:line")
    .attr('x1',x1)
    .attr('x2',x2)
    .attr('y1',y1)
    .attr('y2',y2)
    .style('stroke',"#33B98E").style('stroke-width',22)
}

var drawPoint = function(x,y) {
  svg.append("svg:circle")
    .attr('cx',x)
    .attr('cy',y)
    .attr('r',10)
    .style('fill',"#997430").style('stroke-width',22)
}

var makeStar = function(x1,y1,n) {
  s = 167
  sinner = s/2
  centerX = x1;
  centerY = y1;
  degreeNext = 2*(Math.PI) / n
  x1 = centerX
  x2 = x1 + s
  y2 = y1 + s
  drawPoint(centerX,centerY)
  points = []//[{x:centerX,y:centerY}]
  degree = 0
  for (i = 0; i < n; i++) { 
    xn = centerX + s * Math.cos(degree)
    yn = centerY + s * Math.sin(degree)
    drawPoint(xn,yn)
    degree = degree + degreeNext;
    points.push({x:xn,y:yn})
  }
  for (i = 0; i < points.length*2; i++) {
    var index = i;
    var index2 = i;
    if (i >= points.length -2)  {
        index = i;
      index2 = i-n; 
    }
    try{
    drawLine(points[index].x,points[index].y,points[index2+2].x,points[index2+2].y)
    }
    catch(err){}
  }
  
  
}

// make more stars :)
makeStar(337,187,6);
makeStar(195,530,7);
```
