<script>
  export let width;
  export let parameterName;
  export let parameterValue;
  export let color;
</script>

<div class="info-container">
  <p>{parameterName}</p>
  <div class="info-bar" style="width: {width}px; background-color: {color}" />
  <p>{parameterValue}</p>
</div>

<style>
  .info-container {
    display: flex;
    align-items: baseline;
    font-size: 12px;
  }

  .info-bar {
    height: 10px;
    max-width: 180px;
    margin: 0 3px 0 7px;
    border-radius: 50px;
  }
</style>
