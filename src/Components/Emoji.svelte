<script>
    export let name;

    let emojis = {
        joy: "😂",
        rofl: "🤣",
        "100": "💯",
        ok: "👌",
    }

    const emoji = emojis[name]
</script>



<p>{name} {emoji}</p>
