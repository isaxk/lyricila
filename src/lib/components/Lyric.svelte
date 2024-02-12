<script lang="ts">
	import { browser } from "$app/environment";
	import { lyrics } from "$lib/lyrics";

	export let lyric: { word: string; time: number };
	export let i: number;
	export let currentLyricId: number;

	let lyricClass: string = "lyric";

	let timeoutLength: number = 300;

	function addPreviousLyricTimes() {
		var timeoutLength: number = 0;
		for (let a = 0; a <= i; a = a + 1) {
			var lyricsa = lyrics[currentLyricId].beforeLyrics;
			var data = lyricsa[a].time;
			timeoutLength += data;
		}
		return timeoutLength + 250;
	}

	if (i === 0) {
		timeoutLength = 0;
	} else {
		timeoutLength = addPreviousLyricTimes();
	}

	if (browser) {
		window.setTimeout(() => {
			lyricClass = "lyric focus";
			window.setTimeout(()=>{
				lyricClass = "lyric timed";
			}, lyrics[currentLyricId].beforeLyrics[i].time)
		}, timeoutLength);
	}
</script>

{#if lyric.word === "NEWLINE"}
	<div class="break"></div>
{:else}
	<div class={lyricClass}>
		{lyric.word}
	</div>
{/if}

<style>
	.lyric {
		display: inline-block;
		font-weight: 500;
		padding: 0px 3.5px;
		letter-spacing: 0.05em;
		font-size: 20px;
		color: rgb(40, 40, 40);
	}
	.lyric.timed {
		color: rgb(204, 204, 204);
		transition: 0.3s;
		transition-delay: 0.1s;
	}
	.lyric.focus {
		color: white;
		font-weight: 600;
		transition: 0.3s;
	}
	.break {
		margin: 15px 0px 0px 0px;
	}
</style>
