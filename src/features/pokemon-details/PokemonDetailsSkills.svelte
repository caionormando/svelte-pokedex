<script>
  import Chart from "svelte-frappe-charts";

  let data = {
    labels: ["Attack", "Defense", "Speed"],
    datasets: [
      {
        values: [randomIntFromInterval(1,30), randomIntFromInterval(1,30), randomIntFromInterval(1,30)],
      },
      {
        values: [randomIntFromInterval(31,70), randomIntFromInterval(31,70), randomIntFromInterval(31,70)],
      },
      {
        values: [randomIntFromInterval(71,100), randomIntFromInterval(71,100), randomIntFromInterval(71,100)],
      },
    ],
  };

  function randomIntFromInterval(min, max) {
  return Math.floor(Math.random() * (max - min + 1) + min);
}

</script>

<div class="skill-container">
  <Chart
    {data}
    type="bar"
    height="185"
    title="Stats evolution by level (1-30, 31-70, 71-100)"
  />
</div>

<style>
  .skill-container {
    height: 100%;
  }
</style>
