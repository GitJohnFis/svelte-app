<script>
	$: note = '';
	let note_id = 0;
	let notes = [
		{
			id: 0,
			content: "Lorem ipsum testing a first",
			editing: false,
		},
	];

	function saveNote() {
		notes.push([...notes, 	{
				id: note_id + 1,
				content: note,
				editing: false
			}]);
			notes = notes;
			note_id = note_id + 1;
			note = '';
	}

	function deleteNote(id) {
		notes =notes.filter(note_to_delete => note_to_delete.id != id);
	}
	
	function editNote(note_to_edit) {
		note_to_edit.editing = true;
		notes = notes;
	}
	
	function finishEdit(note_to_edit) {
		note_to_edit.editing = false;
		notes = notes;

	}

	function onKeyEdit(event, note_to_edit) {
 if (event.key === 'Enter') {
	finishEdit(note_to_edit);
 }
	}
	
</script>

<main>
	<div>
		<form on:submit|preventDefault={saveNote}>
			<h2>Add new notes</h2>
			<textarea 
			type="text"
			 placeholder="Type a new note here">
			</textarea>
			<input type="submit" value="Save" />
		</form>
		<hr />
		<h2>Latest Notes</h2>
		{#if notes.length > 0}
			{#each notes as note}
				<div style="border: 1px solid #000;padding: 15px;">
					{#if note.editing}
					<textarea bind:value={note.content} on:keypress={onKeyEdit(event, note)}/>
					{:else }
					<p>{note.content}</p>
					{/if}
					<p>{notes.content}</p>
					<hr />
					<button on:click={deleteNote(note.id)}>Delete</button>
					<button on:click={editNote(note)}>Edit</button>
				</div>
			{/each}
		{:else}
			<p>There is not any notes</p>
		{/if}
	</div>
</main>