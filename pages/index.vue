<template>
  <div class="container">
    <button @click="print1">Primer Segmento</button>
    <button @click="print2">Segundo Segmento</button>
    <button @click="print3">Tercer Segmento</button>
    <button @click="print4">Cuarto Segmento</button>
    <button @click="print5">Todo Circulo</button>
    <button @click="print6">ULTIMA CAPA</button>
    <button @click="print5">PASO 1</button>
    <button @click="print7">PASO 2</button>
    <svg width="400" height="400"></svg>
    <!-- <svg width="400" height="400">
  	  <g id="base" transform="translate(200,200)"></g> -->
  	  <!-- <g id="steps-forward" transform="translate(200,200)"></g>
  	  <g id="steps-backward" transform="translate(200,200)"></g> -->
    <!-- </svg> -->
  </div>
</template>

<script>
import * as d3 from 'd3';

export default {
  methods: {
    print1() {
      var arcGenerator = d3.arc();
      var pathData = arcGenerator({
        startAngle: 0,
        endAngle: 1.25664,
        innerRadius: 95,
        outerRadius: 100
      });
      d3.select('g').append('path').attr('d', pathData).attr('fill', 'red');
    },
    print2() {
      var arcGenerator = d3.arc();
      var pathData = arcGenerator({
        startAngle: 1.25664,
        endAngle: 2.51327,
        innerRadius: 95,
        outerRadius: 100
      });
      d3.select('g').append('path').attr('d', pathData).attr('fill', 'red');
    },
    print3() {
      var arcGenerator = d3.arc();
      var pathData = arcGenerator({
        startAngle: 2.51327,
        endAngle: 5.02655,
        innerRadius: 95,
        outerRadius: 100
      });
      d3.select('g').append('path').attr('d', pathData).attr('fill', 'red');
    },
    print4() {
      var arcGenerator = d3.arc();
      var pathData = arcGenerator({
        startAngle: 5.02655,
        endAngle: 6.28319,
        innerRadius: 95,
        outerRadius: 100
      });
      d3.select('g').append('path').attr('d', pathData).attr('fill', 'red');
    },
    print6() {
      var arcGenerator = d3.arc();
      var pathData = arcGenerator({
        startAngle: 0,
        endAngle: 6.28319,
        innerRadius: 95,
        outerRadius: 100
      });
      d3.select('g').append('path').attr('d', pathData).attr('fill', 'green');
    },
    print5() {
       var arc = d3.arc()
        .innerRadius(95)
        .outerRadius(100);

      var svg = d3.select("svg")
        .attr("width", 400)
        .attr("height", 400)
        .append("g")
        .attr("transform", "translate(" + 200 + "," + 200 + ")")

      svg.append("path")
          .datum({
          endAngle: 72 * (Math.PI/180),
          startAngle: 0
          // endAngle: 0,
          // startAngle: 72 * (Math.PI/180)
      }).style("fill", "blue").attr("d", arc).transition().duration(750).attrTween("d", function(d) {
        //var interpolate = d3.interpolate(d.startAngle, d.endAngle);
        var interpolate = d3.interpolate(d.startAngle, d.endAngle);
        return function(t) {
          d.endAngle = interpolate(t);
          return arc(d);
        };
      })
    },
    print7() {
       var arc = d3.arc()
        .innerRadius(95)
        .outerRadius(100);

      var svg = d3.select("svg")
        .append("g")
        .attr("transform", "translate(" + 200 + "," + 200 + ")")

      svg.append("path")
          .datum({
          // endAngle: 72 * (Math.PI/180),
          // startAngle: 0
          endAngle: 0,
          startAngle: 72 * (Math.PI/180)
      }).style("fill", "grey").style("stroke", "grey").style("stroke-width", 2).attr("d", arc).transition().duration(750).attrTween("d", function(d) {
        //var interpolate = d3.interpolate(d.startAngle, d.endAngle);
        var interpolate = d3.interpolate(d.startAngle, d.endAngle);
        return function(t) {
          d.endAngle = interpolate(t);
          return arc(d);
        };
      })
    }
  }
}
</script>

<style>
svg {
  background: grey;
}
</style>
