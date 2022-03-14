<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    function emitEvent() {
        dispatch('custom-event', {
            someData: "data from custom event forwarded from inner component "
        })
    }

</script>

<button on:click|once={emitEvent}>Button from inner component with event modifier</button>