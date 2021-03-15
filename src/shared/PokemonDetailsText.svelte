<script>
  import { RingLoader } from "svelte-loading-spinners";

  import { onMount } from "svelte";

  export let itemTitle;
  export let pokemonId;
  let statusParameters;
  let typeParameters;

  function setWeightBarSize(weight) {
    return (weight * 980) / 10000;
  }
  function setHeightBarSize(height) {
    return (height * 980) / 200;
  }
  function setExperienceBarSize(exp) {
    return (exp * 980) / 500;
  }

  onMount(async () => {
    await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonId}`)
      .then((r) => r.json())
      .then((data) => {
        statusParameters = data;
      });
  });
</script>

<div class="text-container">
  {#if itemTitle === "Status" && statusParameters}
    <div class="info-container">
      <p>Weight:</p>
      <div
        class="info-bar"
        style="width: {setWeightBarSize(
          statusParameters.weight
        )}px; background-color: orange"
      />
      <p>{statusParameters.weight} kg</p>
    </div>
    <div class="info-container">
      <p>Height:</p>
      <div
        class="info-bar"
        style="width: {setHeightBarSize(
          statusParameters.height
        )}px; background-color: blue"
      />
      <p>{statusParameters.height} m</p>
    </div>
    <div class="info-container">
      <p>Base exp:</p>
      <div
        class="info-bar"
        style="width: {setExperienceBarSize(
          statusParameters.base_experience
        )}px; background-color: red"
      />
      <p>{setExperienceBarSize(statusParameters.base_experience)}</p>
    </div>
  {:else if itemTitle === "Types" && typeParameters}
    <h3>Type: {typeParameters.name.toUpperCase()}</h3>
  {:else}
    <div class="spinner-container">
      <RingLoader size="100" color="#000" unit="px" duration="1s" />
    </div>
  {/if}
</div>

<style>
  .text-container {
    height: 84%;
  }

  .info-container {
    display: flex;
    align-items: baseline;
  }

  .info-bar {
    width: 980px;
    height: 10px;
    max-width: 180px;
    margin: 0 3px 0 7px;
    border-radius: 50px;
  }

  .spinner-container {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
