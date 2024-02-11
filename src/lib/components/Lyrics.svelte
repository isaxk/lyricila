<script lang="ts">
	import { fade } from "svelte/transition";
	import Lyric from "./Lyric.svelte";
	import ExtendedLyric from "./ExtendedLyric.svelte";

	export let lyricData: {
		beforeLyrics: { word: string; time: number }[];
		afterLyrics: string;
		extendedLyrics: { word: string; time: number }[];
	};

	export let enteredLyrics: string;

	export let currentLyricId: number;

	export let beforeFinished: boolean;

	let extendedActive: boolean;

	let typedLyrics: string = "";
	let inputClass: string = "";

	function handleSubmit(e: any) {
		e.preventDefault();
		enteredLyrics = typedLyrics;
		extendedActive = true;
		inputClass = "submitted";
	}
</script>

<form class="lyrics" on:submit={handleSubmit}>
	{#each lyricData.beforeLyrics as lyric, i}
		<Lyric {lyric} {i} {currentLyricId} />
	{/each}
	{#if beforeFinished === true}
		{#if inputClass === "submitted"}
			<input
				class="lyricinput submitted"
				readonly
				bind:value={typedLyrics}
				type="text"
			/>
		{:else}
			<input
				class="lyricinput {inputClass}"
				bind:value={typedLyrics}
				type="text"
				autofocus
			/>
		{/if}
	{/if}
	<br />
	<div class="extended-lyrics">
		{#key extendedActive}
			{#each lyricData.extendedLyrics as lyric, i}
				<ExtendedLyric {lyric} {i} {currentLyricId} {extendedActive} />
			{/each}
		{/key}
	</div>
</form>

<style>
	.lyrics {
		padding: 50px 0px;
	}

	.lyricinput {
		font-family: "Red Hat Display", sans-serif;
		letter-spacing: 0.05em;
		font-weight: 500;
		display: inline-block;
		border: none;
		background-color: transparent;
		padding: 10px 5px 0px 0px;
		/* 		border-bottom: 2px solid grey; */
		width: 300px;
		color: white;
		outline: none;
		font-size: 20px;
	}
	.submitted {
		border: none;
	}
</style>
