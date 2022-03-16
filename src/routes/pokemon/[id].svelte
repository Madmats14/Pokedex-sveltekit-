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
    let shiny = false;
    let pokeDisplay = 'front_default';
    function pokeChange() {
        console.log("probando")
        if (shiny === false) {
            pokeDisplay = 'front_shiny'
            
        }
        if (shiny === true) {
            pokeDisplay = 'front_default';
            
        }
        shiny = !shiny
    }
</script>

<div class="flex flex-col items-center">

    <button on:click={pokeChange}>
        <h1 class="text-4xl text-center my-8 uppercase">{poke.name}</h1>
    
    </button>
    
    <p>Height: <strong>{poke.height}</strong>
     | Weight: <strong>{poke.weight}</strong>
    </p>
    <img class="card-image" src={poke.sprites[pokeDisplay]} 
    alt={poke.name}
    />
</div>
<div class="pokeTypeWrapper">
    <div class="flex justify-center w-full space-x-3">
        {#if (poke.types.length > 1)}
        {#each poke.types as tipo}
            <p class="text-2xl capitalize">{tipo.type.name}</p>
        {/each}
    {:else}
            <p class="text-2xl capitalize">{poke.types[0].type.name}</p>    
    {/if}
    </div>
</div>

