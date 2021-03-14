<script>
    import { onMount } from "svelte";
    import Pokemon from "./Pokemon.svelte";
    // define the data holding variable
    let pokemons;
    onMount(async () => {
    await fetch(`https://pokeapi.co/api/v2/pokemon/?limit=-1`)
      .then(r => r.json())
      .then(data => {
        pokemons = data.results;
    });
  })
</script>

<div class='cards-container'>
  {#if pokemons}
    {#each pokemons as pokemon }
      <ul>
        <li>    
          <Pokemon {pokemon} />
        </li>
      </ul>
    {/each}
  {:else}
    <p class="loading">loading...</p>
  {/if}
</div>



<style>

  .cards-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  .loading {
    opacity: 0;
    animation: 0.4s 0.8s forwards fade-in;
  }
  @keyframes fade-in {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  li {
    list-style-type: none;
  }
</style>