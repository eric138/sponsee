<template>
  <a-row type="flex" justify="space-between">
    <a-col :span="24">
      <a-card size="small">
        <DoughnutChart :chartData="doughnutTestData" />
      </a-card>
    </a-col>
  </a-row>
  <a-row type="flex" justify="space-between">
    <a-col :span="24">
      <a-card size="small">
        <ScatterChart :chartData="scatterTestData" />
      </a-card>
    </a-col>
  </a-row>
</template>

<script>
import { Chart, registerables } from "chart.js";
import { DoughnutChart, ScatterChart } from "vue-chart-3";

Chart.register(...registerables);

export default {
  name: "Profile",
  data() {
    return {
      doughnutTestData: {
        labels: ["Paris", "Nîmes", "Toulon", "Perpignan", "Autre"],
        datasets: [
          {
            data: [30, 40, 60, 70, 5],
            backgroundColor: [
              "#77CEFF",
              "#0079AF",
              "#123E6B",
              "#97B0C4",
              "#A5C8ED",
            ],
          },
        ],
      },
      scatterTestData: {
        datasets: [
          {
            label: "scatter dataset",
            data: [
              {
                x: 10,
                y: 20,
              },
              {
                x: 15,
                y: 10,
              },
              {
                x: 12.5,
                y: 15,
              },
            ],
            backgroundColor: "#56008F",
          },
        ],
      },
    };
  },
  components: {
    DoughnutChart,
    ScatterChart,
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
