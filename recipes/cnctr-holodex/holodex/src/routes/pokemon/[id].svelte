<script context="module">
    export async function load({page}) {
        const id = page.params.id;
        const url = `https://pokeapi.co/api/v2/pokemon/${id}`;
        const result = await fetch(url);
        const pokemon = await result.json();
        return {props: {pokemon}};
    }
</script>
<script>
    export let pokemon;
    const type = pokemon.types[0].type.name
</script>


<div class="flex flex-col items-center">
    <h1 class="text-4xl text-center my-8 uppercase">
        <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-pink-100 text-gray-800">
        {pokemon.name}
        </span>
    </h1>
    <p>Type: <strong>{type}</strong> | Height: <strong>{pokemon.height}</strong>
        | Weight: <strong>{pokemon.weight}</strong>
    </p>
    <img class="card-image h-80 w-80" src={pokemon.sprites['front_default']}
         alt={pokemon.name}
    />
</div>