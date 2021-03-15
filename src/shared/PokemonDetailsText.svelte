<script>
  import { onMount } from "svelte";
  export let itemTitle;
  export let pokemonId;
  let statusParameters;
  let typeParameters;

  onMount(async () => {
    await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonId}`)
      .then((r) => r.json())
      .then((data) => {
        statusParameters = data;
      });
    await fetch(`https://pokeapi.co/api/v2/type/${pokemonId}`)
      .then((r) => r.json())
      .then((data) => {
        typeParameters = data;
      });
  });
</script>

<div class="text-container">
  {#if itemTitle === "Status" && statusParameters}
    <h3>Name: {statusParameters.name.toUpperCase()}</h3>
    <h3>Weight: {statusParameters.weight}</h3>
  {:else if itemTitle === "Types" && typeParameters}
    <h3>Type: {typeParameters.name.toUpperCase()}</h3>
  {/if}
</div>

<style>
  .text-container {
    height: 84%;
  }
</style>
