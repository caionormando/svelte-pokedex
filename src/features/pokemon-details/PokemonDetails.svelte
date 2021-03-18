<script>
  import PokemonDetailsText from "./PokemonDetailsText.svelte";

  export let pokemonId;
  export let pokemon;
  let item = "Status";
  let itemTitles = ["Status", "Types", "Skills"];

  function setItem(itemTitle) {
    item = itemTitle;
  }
</script>

<div class="details-container">
  <div class="pokemon-container">
    <img
      src={`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${pokemonId}.png`}
      alt="pokeball"
    />
    <h1>{pokemon.name.charAt(0).toUpperCase() + pokemon.name.slice(1)}</h1>
  </div>
  <div class="details-panel">
    <nav class="details-panel-header">
      {#each itemTitles as itemTitle}
        <button class="item-header" on:click={() => setItem(itemTitle)}
          >{itemTitle}</button
        >
      {/each}
    </nav>
    <PokemonDetailsText itemTitle={item} {pokemonId} />
  </div>
</div>

<style>
  .details-container {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .pokemon-container{
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
  }

  .pokemon-container img {
    width: 60%;
  }

  .details-container h1 {
    font-family: pokemon-hollow;
    color: #0663a5;
    text-shadow: 2px 2px yellow;
    margin: 0;
  }

  .details-panel {
    border: solid 3px;
    border-radius: 10px;
    height: 40%;
    width: 80%;
    background-color: white;
  }

  .details-panel-header {
    height: 15%;
    display: flex;
    justify-content: space-around;
    align-items: center;
    background-color: black;
  }

  .item-header {
    height: 70%;
    color: white;
    background-color: black;
    border: none;
    border-radius: 0;
    font-size: 14px;
  }

  .item-header:hover {
    cursor: pointer;
  }

  /* ##################################################################DESKTOP VERSION############################################################################################## */

  @media (min-width: 768px) {
    .details-container {
      flex-direction: row;
      align-items: auto;
      justify-content: space-around;
    }

    .pokemon-container {
      width: 45%;
    }
    .pokemon-container img {
      width: 50%;
    }

    .pokemon-container h1{
      font-size: 5em;
    }

    .details-panel {
      height: 90%;
      width: 60%;
    }
  }
</style>
