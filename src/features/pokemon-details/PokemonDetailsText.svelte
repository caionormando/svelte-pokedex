<script>
  import { RingLoader } from "svelte-loading-spinners";

  import { onMount } from "svelte";

  import PokemonDetailsInfo from "./PokemonDetailsInfo.svelte";
  import PokemonDetailsType from "./PokemonDetailsType.svelte";
  import PokemonDetailsSkills from "./PokemonDetailsSkills.svelte";

  const weightMax = 10000;
  const heightMax = 200;
  const expMax = 500;

  export let itemTitle;
  export let pokemonId;
  let statusParameters;
  let types;

  function setStatBarSize(stat, maxValue){
    return (stat * 100) / maxValue;
  }

  function generateRandomValue() {
    return Math.floor(Math.random() * 980);
  }

  onMount(async () => {
    await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonId}`)
      .then((r) => r.json())
      .then((data) => {
        statusParameters = data;
        types = data.types.map((obj) => obj.type.name);
      });
  });
</script>

<div class="text-container">
  {#if itemTitle === "Status" && statusParameters}
    <PokemonDetailsInfo
      parameterName={"Weight"}
      parameterValue={statusParameters.weight}
      width={setStatBarSize(statusParameters.weight, weightMax)}
      color={"orange"}
    />
    <PokemonDetailsInfo
      parameterName={"Height"}
      parameterValue={statusParameters.height}
      width={setStatBarSize(statusParameters.height, heightMax)}
      color={"blue"}
    />
    <PokemonDetailsInfo
      parameterName={"Base exp"}
      parameterValue={statusParameters.base_experience}
      width={setStatBarSize(statusParameters.base_experience, expMax)}
      color={"red"}
    />
    <PokemonDetailsInfo
      parameterName={"Sp.Atk"}
      parameterValue={generateRandomValue()}
      width={generateRandomValue()}
      color={"green"}
    />
    <PokemonDetailsInfo
      parameterName={"Sp.Def"}
      parameterValue={generateRandomValue()}
      width={generateRandomValue()}
      color={"#25facf"}
    />
  {:else if itemTitle === "Types"}
    <PokemonDetailsType {types} />
  {:else if itemTitle === "Skills"}
    <PokemonDetailsSkills />
  {:else}
    <div class="spinner-container">
      <RingLoader size="100" color="#000" unit="px" duration="1s" />
    </div>
  {/if}
</div>

<style>
  .text-container {
    height: 84%;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .spinner-container {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
