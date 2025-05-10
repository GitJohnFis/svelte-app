<script>
	import { createEventDispatcher } from "svelte";
	$: note = "";
	const dispatch = createEventDispatcher();
	let note = "";
	function saveNoteDispatched() {
		dispatch("saveNoteDispatched", { note: note });
		note = "";
	}
</script>

<form on:submit|preventDefault={saveNoteDispatched}>
	<h2>Add new notes</h2>
	<textarea type="text" placeholder="Type a new note here"> </textarea>
	<input type="submit" value="Save" />
</form>
