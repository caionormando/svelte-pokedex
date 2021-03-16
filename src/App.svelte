<script>
  import PokedexHeader from "./core/PokedexHeader.svelte";
  import PokemonsGrid from "./features/PokemonsGrid.svelte";
  
  let pokemons;
</script>

<div class="title-container">
  <PokedexHeader />
</div>
<div class="main-panel">
  <span>&#10148;</span>
  <div class="pokemons-container">
    <PokemonsGrid {pokemons} />
  </div>
</div>

<style>
  .title-container {
    display: flex;
    justify-content: center;
    width: 100%;
    height: 8%;
  }

  .main-panel {
    display: flex;
    align-items: center;
    height: 90%;
    margin-top: 30px;
  }
  .main-panel .pokemons-container {
    overflow: auto;
    height: 100%;
    width: 100%;
  }

  .main-panel span {
    display: none;
  }

  ::-webkit-scrollbar {
    width: 10px;
  }

  /* Track */
  ::-webkit-scrollbar-track {
    background: transparent;
  }

  /* Handle */
  ::-webkit-scrollbar-thumb {
    background: #888;
    border-radius: 5px;
  }

  /* Handle on hover */
  ::-webkit-scrollbar-thumb:hover {
    background: #555;
  }

  @media (min-width: 768px) {
    .title-container {
      height: 22%;
    }

    .main-panel {
      height: 75%;
    }

    .main-panel span {
      display: block;
      font-size: 10em;
      background: -webkit-linear-gradient(#f15a24, #edb825);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
	  margin-right: 4px;
    }
  }
</style>
