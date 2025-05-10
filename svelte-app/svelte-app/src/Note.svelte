<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();
    export let note;

    function onKeyEdit(event, note) {
        if (event.key === 'Enter') {
        dispatch("onKeyEditDispatched", { note: note });
        }
    }
    function deleteNote(id){
dispatch('deleteNoteDispatched', {id: id});
    }
    function editNote(note) {
        dispatch('editNoteDispatched', {note: note});
    }
</script>

<div style="border: 1px solid #000;padding: 15px;">
    {#if note.editing}
        <textarea
            bind:value={note.content}
            on:keypress={onKeyEdit(event, note)}
        />
    {:else}
        <p>{note.content}</p>
    {/if}
    <p>{note.content}</p>
    <hr />
    <button on:click={deleteNote(note.id)}>Delete</button>
    <button on:click={editNote(note)}>Edit</button>
</div>
