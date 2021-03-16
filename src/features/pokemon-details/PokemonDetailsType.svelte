<script>
  export let types = [];
</script>

<div class="type-container">
  {#each types as type}
    <div class="image-container" style="width: {100 / types.length}%">
      <img src="./../images/types/{type}.png" alt="{type} type" />
      <p>{type.charAt(0).toUpperCase() + type.slice(1)}</p>
    </div>
  {/each}
</div>

<style>
  .type-container {
    display: flex;
    justify-content: space-around;
    height: 100%;
  }

  .image-container {
    display: flex;
    flex-direction: column;
    align-items: center;;
    margin: auto;
  }

  .image-container img {
    margin: auto;
  }
</style>
