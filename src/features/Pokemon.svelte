<script>
	export let pokemon;
	let pokemonUrlParts = pokemon.url.split('/');
	export let pokemonId = pokemonUrlParts[pokemonUrlParts.length-2];
</script>

<div class='pokemon-container'>
		<h1>{pokemon.name.toUpperCase()}</h1>
		<div class='image-container'>
			<img src={`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${pokemonId}.png`} alt='pokeball'><br/>
		</div>
		<br/>
</div>

<style>
	.pokemon-container{
		border: solid 3px;
		border-radius: 5px;
		width: 280px;
		background-image: linear-gradient(to bottom right, red, white);
	}

	.pokemon-container .image-container{
		display: flex;
		justify-content: center;
	}

	h1 {
	  font-size: 1.4em;
	  margin: 0;
	  display: block;
	  text-align: center;
	}
	
	img{
		width:33%;
		text-align: center;
	}
  </style>