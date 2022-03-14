<script context="module">
    export async function load({params, fetch}) {
        const id = params.id;
        const url = `https://pokeapi.co/api/v2/pokemon/${id}`;
        const res = await fetch(url);
        const poke = await res.json();
        return {props: {poke}};
    }
</script>
<script>
    export let poke;
    const tipos = poke.types[0].type.name
</script>

<div class="flex flex-col items-center">

    <h1 class="text-4xl text-center my-8 uppercase">{poke.name}</h1>
    <p>Type: <strong>{tipos}</strong> | Height: <strong>{poke.height}</strong>
        | Weight: <strong>{poke.weight}</strong>
    </p>
    <img class="card-image" src={poke.sprites['front_default']} 
    alt={poke.name}
    />
</div>

{#if (poke.types.length > 1)}
    {#each poke.types as tipo}
        <p class="capitalize">{tipo.type.name}</p>
    {/each}
{:else}
    <p class="capitalize">{poke.types[0].type.name}</p>    
{/if}