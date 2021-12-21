<script>
    import { fade } from 'svelte/transition';
    export let pokemon;
</script>
<a class="p-6 bg-gray-100 text-gray-800 text-center rounded-md shadow-sm hover:shadow:md flex flex-col items-center" href={`/pokemon/${pokemon.id}`}>
    <img src="{pokemon.image}" alt="{pokemon.name}">
    <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-pink-100 text-gray-800">
    {pokemon.name}
    </span>
</a>
