<script>
	import Note from "./Note.svelte";
	import NoteCreate from "./NoteCreate.svelte";

	let note_id = 0;
	let notes = [
		{
			id: 0,
			content: "Lorem ipsum testing a first",
			editing: false,
		},
	];

	function saveNote() {
		notes.push([
			...notes,
			{
				id: note_id + 1,
				content: event.detail.note,
				editing: false,
			},
		]);
		notes = notes;
		note_id = note_id + 1;
		note = "";
	}

	function deleteNote(id) {
		notes = notes.filter((note_to_delete) => note_to_delete.id != id);
	}

	function editNote(note_to_edit) {
		note_to_edit.editing = true;
		notes = notes;
	}

	function finishEdit(note_to_edit) {
		note_to_edit.editing = false;
		notes = notes;
	}

	function onKeyEdit(event) {
		finishEdit(event.detail.note);
	}
</script>

<main>
	<div>
		<NoteCreate on:saveNoteDispatched={saveNote} />
		<hr />
		<h2>Latest Notes</h2>
		{#if notes.length > 0}
			{#each notes as note}
				<Note
					on:onKeyEditDispatched={(event) => onKeyEdit(event)}
					on:deleteNoteDispatched={(event) =>
						deleteNote(event.detail.id)}
					on:editNoteDispatched={(event) =>
						editNote(event.detail.note)}
					{note}
				/>
			{/each}
		{:else}
			<p>There is not any notes</p>
		{/if}
	</div>
</main>
