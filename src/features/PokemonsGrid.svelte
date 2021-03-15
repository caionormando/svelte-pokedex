<script>
  import { RingLoader } from "svelte-loading-spinners";

  import { onMount } from "svelte";
  import Pokemon from "./Pokemon.svelte";

  let pokemons;

  onMount(async () => {
    await fetch(`https://pokeapi.co/api/v2/pokemon/?limit=-1`)
      .then((r) => r.json())
      .then((data) => {
        pokemons = data.results;
      });
  });
</script>

<div class="cards-container">
  {#if pokemons}
    {#each pokemons as pokemon}
      <Pokemon {pokemon} />
    {/each}
  {:else}
    <div class="spinner-container">
      <RingLoader size="100" color="#000" unit="px" duration="1s" />
    </div>
  {/if}
</div>

<style>
  .cards-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    height: 100%;
  }
  .spinner-container {
    margin: auto;
  }
  @keyframes fade-in {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }
</style>
