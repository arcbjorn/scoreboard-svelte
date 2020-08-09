<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

	export let name;
	export let points;
	let showControls = false;

	const addPoint = () => (points += 1);
	const removePoint = () => (points -= 1);
	const toggleControls = () => (showControls = !showControls);
  const onDelete = () => dispatch("removeplayer", name);
</script>

<div class="card">
  <div class="d-flex flex-row p-3 justify-content-between align-items-center">
    <div class="d-flex flex-column">
      <h1>
        {name}
        <button class="btn btn-sm" on:click={toggleControls}>
          {#if showControls}-{:else}+{/if}
        </button>
        <button
          class="btn btn-danger btn-sm"
          on:click={onDelete}
        >
          x
        </button>
      </h1>
      <h3>Points: {points}</h3>
    </div>
    <div class="d-flex flex-column justify-content-center align-items-center">
      <div class="d-flex flex-row">
        {#if showControls}
        <button type="button" class="btn btn-sm btn-success m-1" on:click={addPoint}>+1</button>
        <button type="button" class="btn btn-sm btn-danger m-1" on:click={removePoint}>-1</button>
        <input type="number" bind:value={points} />
        {/if}
      </div>
    </div>
   
  </div>
  
</div>