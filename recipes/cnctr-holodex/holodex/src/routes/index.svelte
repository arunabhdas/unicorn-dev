<script context="module">
    export async function load({page}) {
        const url = `https://pokeapi.co/api/v2/pokemon?limit=$150&offset=0`;
        const res = await fetch(url);
        const data = await res.json();
        const loadedPokemons = data.results.map((data, index) => {
            return {
                name: data.name,
                id: index + 1,
                image: `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${
                    index + 1
                }.png`
            };
        });
        return {props: {pokemons: loadedPokemons}}
    }
</script>

<script>
  import PokemonCard from "../components/pokemonCard.svelte";
  // import {pokemons, fetchPokemons} from "../stores/holostore";
  export let pokemons;
  // fetchPokemons(150);
  let searchTerm = "";
  let filteredPokemon = [];

  $: {
      if (searchTerm) {
          // search
          filteredPokemon = pokemons.filter(pokemon => pokemon.name.toLowerCase().includes(searchTerm.toLowerCase()));
      } else {
          filteredPokemon = [...pokemons];
      }
  }
</script>
<svelte:head>
    <title>Cnctr Dex</title>
</svelte:head>
<h1 class="text-4xl text-center my-8">Cnctr Dex</h1>
<input class="mx-4 w-full rounded-md text-lg p-4 border-2 border-gray-200 text-gray-600" type="text" bind:value={searchTerm} placeholder="Search">
<div class="mx-4 py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
{#each filteredPokemon as pokemon}
      <PokemonCard pokemon="{pokemon}"/>
{/each}
</div>