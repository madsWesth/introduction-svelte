<script>
    import Header from "./Header.svelte";
    export let title;
    export let text;
</script>

<Header title={title}/>
{#if text}
<p>{text}</p>
{/if}

