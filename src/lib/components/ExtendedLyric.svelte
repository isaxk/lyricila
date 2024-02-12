<script lang="ts">
	import { browser } from "$app/environment";
	import { lyrics } from "$lib/lyrics";
	import "$lib/css/lyricstyles.css";

	export let lyric: { word: string; time: number };
	export let i: number;
	export let currentLyricId: number;

	let lyricClass: string = "lyric";

	let timeoutLength: number = 300;

    export let extendedActive: boolean;

	function addPreviousLyricTimes() {
		var timeoutLength: number = 0;
		for (let a = 0; a < i; a = a + 1) {
			var data = lyrics[currentLyricId].extendedLyrics[a];
			console.log(data.time);
			timeoutLength += data.time;
		}
		return timeoutLength + 250;
	}

	if (i === 0) {
		timeoutLength = lyric.time;;
	} else {
		timeoutLength = addPreviousLyricTimes();
	}

	if (browser && extendedActive) {
		window.setTimeout(() => {
			lyricClass = "lyric focus";
			window.setTimeout(()=>{
				lyricClass = "lyric timed";
			}, lyrics[currentLyricId].extendedLyrics[i].time)
		}, timeoutLength);
	}
</script>

{#if lyric.word === "NEWLINE"}
	<br />
{:else}
	<div class={lyricClass}>
		{lyric.word}
	</div>
{/if}

