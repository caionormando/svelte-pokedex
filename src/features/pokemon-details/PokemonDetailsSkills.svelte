<script>
  import { beforeUpdate } from "svelte";

  import Chart from "svelte-frappe-charts";

  let chartHeight;
  let data = {
    labels: ["Attack", "Defense", "Speed"],
    datasets: [
      {
        values: [
          randomIntFromInterval(1, 30),
          randomIntFromInterval(1, 30),
          randomIntFromInterval(1, 30),
        ],
      },
      {
        values: [
          randomIntFromInterval(31, 70),
          randomIntFromInterval(31, 70),
          randomIntFromInterval(31, 70),
        ],
      },
      {
        values: [
          randomIntFromInterval(71, 100),
          randomIntFromInterval(71, 100),
          randomIntFromInterval(71, 100),
        ],
      },
    ],
  };

  beforeUpdate(() => {
    if (screen.width > 400) {
      chartHeight = 580;
    }
    else {
      chartHeight = 185;
    }
  });

  function randomIntFromInterval(min, max) {
    return Math.floor(Math.random() * (max - min + 1) + min);
  }
</script>

<div class="skill-container">
  <Chart
    {data}
    type="bar"
    height={chartHeight}
    title="Stats evolution by level (1-30, 31-70, 71-100)"
  />
</div>

<style>
  .skill-container {
    height: 100%;
  }
</style>
