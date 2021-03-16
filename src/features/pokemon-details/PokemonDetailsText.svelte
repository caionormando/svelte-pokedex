<script>
  import { RingLoader } from "svelte-loading-spinners";

  import { onMount } from "svelte";

  import PokemonDetailsInfo from "./PokemonDetailsInfo.svelte";
  import PokemonDetailsType from "./PokemonDetailsType.svelte";
  import PokemonDetailsSkills from "./PokemonDetailsSkills.svelte";

  export let itemTitle;
  export let pokemonId;
  let statusParameters;
  let types;

  function setWeightBarSize(weight) {
    return (weight * 980) / 10000;
  }
  function setHeightBarSize(height) {
    return (height * 980) / 200;
  }
  function setExperienceBarSize(exp) {
    return (exp * 980) / 500;
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
        console.log(types);
      });
  });
</script>

<div class="text-container">
  {#if itemTitle === "Status" && statusParameters}
    <PokemonDetailsInfo
      parameterName={"Weight"}
      parameterValue={statusParameters.weight}
      width={setWeightBarSize(statusParameters.weight)}
      color={"orange"}
    />
    <PokemonDetailsInfo
      parameterName={"Height"}
      parameterValue={statusParameters.height}
      width={setHeightBarSize(statusParameters.height)}
      color={"blue"}
    />
    <PokemonDetailsInfo
      parameterName={"Base exp"}
      parameterValue={statusParameters.base_experience}
      width={setExperienceBarSize(statusParameters.base_experience)}
      color={"red"}
    />
    <PokemonDetailsInfo
      parameterName={"Strenght"}
      parameterValue={generateRandomValue()}
      width={generateRandomValue()}
      color={"green"}
    />
    <PokemonDetailsInfo
      parameterName={"Speed"}
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
