<script>
    export let control = "textarea"
    export let value
    export let placeholder
    export let type = "text"
    export let nombre
    export let id
</script>

<div class="form-group">
    <label for={id}>{nombre}</label>
    {#if control === 'textarea'}
        <textarea {id} {placeholder} {value} on:input rows="10" class="form-control"></textarea>
    {:else}
        <input {type} class="form-control" {id} {placeholder} {value} on:input>
    {/if}

</div>
