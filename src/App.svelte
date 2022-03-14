<script>
import Emoji from "./Components/Emoji.svelte";
import Numbers from "./Components/Number.svelte";
import Outer from "./Components/Outer.svelte"

	import Section from "./Components/Section.svelte";

	let logo = "/1200px-Svelte_Logo.svg.png"

	let counter = 0

	let spreadExample = {
		one: "1",
		two: "2",
		three: "3"
	}

	let emojis = [
		{id: 1, name: "joy",},
		{id: 2, name: "rofl"},
		{id: 3,	name: "100"},
		{id: 4, name: "ok"}
	]
	let eachText = "I couldnt figure out a good way to showcase the issue that keyed each blocks solve. It has to do with the way it updates the DOM when you delete and add components, the order can be different to what you expect if you dont key it"

	function removeFirstEmoji(){
		emojis = emojis.slice(1)
	}
</script>

<main>
	<div>
		<img src="{logo}" alt="logo">
	</div>
	<h1>Svelte foolaround</h1>
	<Section title={"Basics, components and styling"} text={"Hi from inner component"}/>
	<Numbers {...spreadExample}/>

	<Section title="reactivity" text="Reactivity is done through assignments"/>
	<p>inline handler</p>
	<button on:click={() => counter++}>Stuff happens when im pressed. {counter === 0? "" :`${counter} clicks`}</button>
	{#if counter >= 10}
		<p>you pressed the button 10 or more times</p>
	{:else}
	<p>Try pressing the button 10 times</p>
	{/if}

	<Section title="each" text={eachText}/>
	<p>unkeyed each</p>
	{#each emojis as emoji}
	<p>
		<Emoji name={emoji.name}></Emoji> 
	</p>
	{/each}
	<br>
	<p>keyed each</p>
	{#each emojis as emoji (emoji.id)}
		<p>
			<Emoji name={emoji.name}/>
		</p>
	{/each}
<button on:click={removeFirstEmoji}>Remove first emoji</button>

<Section title="events"/>
<Outer on:custom-event={(event)=> alert(event.detail.someData)}/>


</main>

<style>
	main {
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		text-align: center;
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	div {
		display: flex;
	}

	img {
		width: 10%;
		justify-items: center;
		margin: 0 auto;
	}

</style>