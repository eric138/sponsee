<template>
  <a-row type="flex" justify="space-between">
    <a-col :span="24">
      <a-card size="small">
        <div id="myDiv"></div>
      </a-card>
    </a-col>
  </a-row>
</template>

<script>
import Plotly from "plotly.js-dist";

export default {
  name: "Home",
  mounted() {
    var trace1 = {
      x: [1, 2, 3, 4],
      y: [10, 15, 13, 17],
      mode: "markers",
      type: "scatter",
    };

    var trace2 = {
      x: [2, 3, 4, 5],
      y: [16, 5, 11, 9],
      mode: "lines",
      type: "scatter",
    };

    var trace3 = {
      x: [1, 2, 3, 4],
      y: [12, 9, 15, 12],
      mode: "lines+markers",
      type: "scatter",
    };

    var data = [trace1, trace2, trace3];
    var config = { responsive: true };

    Plotly.newPlot("myDiv", data, config);
  },
};
</script>

<style lang="scss" scoped>
.ant-card {
  border: 1px solid black;
  border-radius: 12px;
  box-shadow: 6px 6px 6px 2px rgb(17, 0, 29, 0.4);
}
.ant-row + .ant-row {
  margin-top: 12px;
}
</style>
