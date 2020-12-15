<script>
	let notes = [];
	let id = 0;
	let text = "";

	function handleAddNote(){
		if(text.trim().length > 0){
			notes.push({id, text});
			notes = notes;
			id = id + 1;
			text = "";
		}
	}

	function handleDeleteNote(note){
		notes = notes.filter(e => e.id !== note.id);
	}
</script>

<main>
	<h1>Notes</h1>
	<input type="text" name="note-text" id="note-text" bind:value={text}/>
	<button type="button" on:click={handleAddNote}>Add note</button>
	{#if notes.length === 0}
		<h2>You don't have any notes 😢</h2>
	{:else}
		<h2>My notes</h2>
		{#each notes as note}
			<div class="note-container">
				<p>{note.text} | </p><img src="trash.svg" alt="trash" on:click={handleDeleteNote(note)}/>
			</div>
		{/each}
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #001A23;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>