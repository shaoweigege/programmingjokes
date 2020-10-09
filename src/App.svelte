<script>
	import { onMount } from "svelte";

	import { Stretch } from "svelte-loading-spinners";
	const fetchJoke = () => {
		joke = "";
		loading.removeAttribute("hidden");
		fetch("https://sv443.net/jokeapi/v2/joke/Programming")
			.then((res) => res.json())
			.then((data) => {
				loading.setAttribute("hidden", "");
				joke = data.joke;
			});
	};

	onMount(() => {
		fetchJoke();
	});

	let joke = "";
</script>

<style>
	.container {
		margin-top: 100px;
	}
</style>

<div class="container">
	<center>
		<button class="btn btn-danger" on:click={fetchJoke}>Another one</button><br /><br />
		<div hidden id="loading">
			<Stretch size="60" color="#FF3E00" unit="px" />
		</div>
		<h1>{joke}</h1>
	</center>
</div>
