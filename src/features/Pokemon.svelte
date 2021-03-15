<script>
  import { Router, Route, Link } from "svelte-navigator";
  import PokemonDetails from "./PokemonDetails.svelte";

  export let pokemon;
  let pokemonUrlParts = pokemon.url.split("/");
  export let pokemonId = pokemonUrlParts[pokemonUrlParts.length - 2];
</script>

<Router>
  <Route path="/">
    <div class="pokemon-container">
      <h1>{pokemon.name.toUpperCase()}</h1>
      <div class="image-container">
        <img
          src={`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${pokemonId}.png`}
          alt="pokeball"
        /><br />
      </div>
      <div class="view-button">
        <nav><Link to="pokemon/{pokemonId}">View Pokémon</Link></nav>
      </div>
    </div>
  </Route>

  <Route path="pokemon/{pokemonId}">
    <PokemonDetails {pokemonId} {pokemon} />
  </Route>
</Router>

<style>
  .pokemon-container {
    border: solid 3px;
    border-radius: 5px;
    width: 280px;
    background-image: linear-gradient(to bottom right, red, white);
	margin-bottom: 10px;
	
  }

  .pokemon-container .image-container {
    display: flex;
    justify-content: center;
  }

  h1 {
    font-size: 1.4em;
    margin: 0;
    display: block;
    text-align: center;
  }

  img {
    width: 33%;
    text-align: center;
  }

  .pokemon-container .view-button {
    margin: 0 auto 15px auto;
    text-align: center;
    border: solid 1px;
    border-radius: 8%;
    width: 38%;
    font-size: 14px;
    background-color: black;
  }
  /* ##################################################################DESKTOP VERSION############################################################################################## */

  @media (min-width: 768px){
	.pokemon-container{
		margin-right: 60px;
		margin-bottom: 18px;
	}
  }
</style>
