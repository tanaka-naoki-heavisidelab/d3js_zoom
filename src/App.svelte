<script lang="ts">
  import { onMount } from "svelte";
  import * as d3 from "d3";

  let _svg: d3.Selection<d3.BaseType, unknown, HTMLElement, any>;
  let svg = _svg as unknown | SVGElement;
  var container;
  onMount(() => {
    _svg = d3.select("svg");

    _svg
      .attr("width", 400)
      .attr("height", 400)
      .attr("style", "background: #AAA");

    let circleData = [0, 1, 2, 3, 4, 5];
    let inc = (Math.PI * 2) / circleData.length;

    let zoom = d3.zoom().scaleExtent([1, 10]).on("zoom", zoomed);
    container = _svg.append("g").call(zoom);

    circleData.forEach((d) => {
      let x = 30 * Math.cos(inc * d);
      let y = 30 * Math.sin(inc * d);
      container
        .append("circle")
        .attr("transform", "translate(200,200)")
        .attr("cx", x)
        .attr("cy", y)
        .attr("r", 5)
        .style("fill", "gold");
    });
  });

  function zoomed(event) {
    container.attr(
      "transform",
      "translate(" +
        event.transform.x +
        "," +
        event.transform.y +
        ") scale(" +
        event.transform.k +
        ")"
    );
  }
</script>

<svg bind:this={svg} />
