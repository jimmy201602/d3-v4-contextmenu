# d3-v4-contextmenu
context menu with d3.js v4.

# Demo
http://plnkr.co/edit/i84SdzHnhKwHgZB21lpe?p=info

# Install
```
npm i @atago0129/d3-v4-contextmenu
```

# Useage
```html
<script type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
<script type="text/javascript" src="./dist/d3-v4-contextmenu.js"></script>
<script type="text/javascript">
  var items = [
    {
      label: function (d) {
        return d;
      },
      items: [
        {
          label: "red",
          onClick: function () {
            this.style.fill = "#ff0000";
          }
        },
        {
          label: "blue",
          action: function () {
            this.style.fill = "#0000ff";
          }
        },
        {
          label: "index",
          action: function (d, i) {
            alert(i + 1);
          }
        }
      ]
    },
    {
      label: "background",
      items: [
        {
          label: "red",
          onClick: function () {
            svg.node().style.background = "#ff0000";
          }
        },
        {
          label: "blue",
          action: function () {
            svg.node().style.background = "#0000ff";
          }
        },
        {
          label: "pink",
          action: function() {
            alert('pink is clicked!');
          },
          items: function() {
            return [
              {
                label: "deep pink",
                action: function () {
                  svg.node().style.background = "#ff1493";
                }
              },
              {
                label() {
                  return "shocking pink";
                },
                action() {
                  svg.node().style.background = "#fc0fc0";
                }
              }
            ];
          }
        }
      ]
    }
  ];

  svg = d3.select('#main')
    .append('svg')
    .attr('width', '100%')
    .attr('height', '100%');

  svg.selectAll('circles')
    .data(['circle1', 'circle2', 'circle3', 'circle4'])
    .enter()
    .append('circle')
    .attr('r', 20)
    .attr('fill', '#ff6040')
    .attr('cx', function(d, i) {
      return (i + 1) * 100;
    })
    .attr('cy', function() {
      return 100;
    })
    .on('contextmenu', d3.contextmenu(items));

  svg.selectAll('rect')
    .data(['rect1', 'rect2', 'rect3', 'rect4'])
    .enter()
    .append('rect')
    .attr('x',  function(d, i) {
      return (i + 1) * 100 - 20;
    })
    .attr('y', function() {
      return 200;
    })
    .attr('width', 40)
    .attr('height', 40)
    .attr('fill', '#8bff5b')
    .on('contextmenu', d3.contextmenu(items));
</script>
```
or
```ecmascript 6
import {contextmenu} from "@atago0129/d3-v4-contextmenu";

rect.on('contextmenu', contextmenu(items));
```
