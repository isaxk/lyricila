<script lang="ts">
	import { fade } from "svelte/transition";
	import HomeHeader from "$lib/components/HomeHeader.svelte";
	import "$lib/css/app.css";
	import { onDestroy, onMount } from "svelte";
	import { Howl, Howler } from "howler";

	export let data;

</script>

{#key data.url}
	<HomeHeader />
	<main
		in:fade={{duration: 100, delay: 100 }}
		out:fade={{duration: 100 }}
	>
		<slot />
	</main>
{/key}

<style>
	main {
		width: 800px;
		max-width: 100%;
		box-sizing: border-box;
		padding: 0px 20px;
		margin: auto;
		padding-top: 150px;
	}
</style>
