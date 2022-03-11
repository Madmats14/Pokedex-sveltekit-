<script>
    import { pokemon } from "../stores/pokestore.js";
    
</script>

<svelte:head>
    <title>Pokedex in Svelte</title>
</svelte:head>
<h1>Svelte Kit Pokedex</h1>

{#each $pokemon as poke}
<p>{poke.name}</p>
{/each}
