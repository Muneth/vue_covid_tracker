<template>
  <div class="p-10">
    <svg height="530" width="1400">
      <g transform="rotate(180)" fill="none" stroke="black" stroke-width="0">
        <rect
          width="90"
          :height="stats.NewConfirmed / 1000"
          style="fill:rgb(194, 189, 41)"
          x="-350"
          y="-500"
        ></rect>
        <rect
          width="90"
          :height="stats.TotalConfirmed / 1000"
          style="fill:rgb(156, 151, 6)"
          x="-500"
          y="-500"
        ></rect>
        <rect
          width="90"
          :height="stats.NewRecovered / 1000"
          style="fill:rgb(87, 121, 235)"
          x="-650"
          y="-500"
        ></rect>
        <rect
          width="90"
          :height="stats.TotalRecovered / 1000"
          style="fill:rgb(9, 51, 148)"
          x="-800"
          y="-500"
        ></rect>
        <rect
          width="90"
          :height="stats.NewDeaths / 1000"
          style="fill:rgb(227, 0, 0)"
          x="-950"
          y="-500"
        ></rect>
        <rect
          width="90"
          :height="stats.TotalDeaths / 1000"
          style="fill:rgb(15, 0, 2)"
          x="-1100"
          y="-500"
        ></rect>
      </g>
      <text x="260" y="530" fill="grey">New Cases</text>
      <text x="410" y="530" fill="grey">Total Cases</text>
      <text x="550" y="530" fill="grey">New Recovered</text>
      <text x="700" y="530" fill="grey">Total Recovered</text>
      <text x="860" y="530" fill="grey">New Deaths</text>
      <text x="1010" y="530" fill="grey">Total Deaths</text>
    </svg>
  </div>
</template>

<script>
export default {
  name: "Bar",
  props: ["stats"],
};
</script>
