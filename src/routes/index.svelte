<script>
    import { pokemon } from "../stores/pokestore.js";
    import PokeCard from "../components/pokeCard.svelte";

    let searchTerm = "";
    let filteredPokemon = [];

    $: {
    if(searchTerm){
        filteredPokemon = $pokemon.filter( poke => poke.name.toLowerCase().includes(searchTerm.toLowerCase()));
    }
    else {
        filteredPokemon = [...$pokemon];
    }
}
</script>

<svelte:head>
    <title>Pokedex in Svelte</title>
</svelte:head>
<h1 class="text-6xl text-center my-8 uppercase">Svelte Kit Pokedex</h1>

<input bind:value={searchTerm} class="w-full rounded-md text-lg p-4 border-2 border-gray-200" type="text" placeholder="Search Pokemon">

<div class=" py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
    {#each filteredPokemon as poke}
        <PokeCard poke={poke}/>
    {/each}
</div>
