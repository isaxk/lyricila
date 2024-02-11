<script lang="ts">
	import { Howl, Howler } from "howler";
	import { playlists } from "$lib/playlists";
	import { lyrics } from "$lib/lyrics";
	import GameHeader from "$lib/components/GameHeader.svelte";
	import Lyrics from "$lib/components/Lyrics.svelte";
	import { browser } from "$app/environment";

	const playlistId = 0;

	const playlistData = playlists[playlistId];

	let lyricId = 0;

	let sound: any;

	Howler.volume(0.5);

	let beforeFinished: boolean = false;

	let enteredLyrics: string = "";

	let lyricData:any;

	function nextLyric() {
		beforeFinished=false;
		enteredLyrics="";
		lyricId++;
	}

	$: lyricData = lyrics[lyricId];

	$: {
		sound = new Howl({
			src: [lyricData.beforeMp3path],
			onend: () => {
				beforeFinished = true;
			},
		});

		if (browser) {
			sound.play();
		}
	}

	$: {
		console.log(enteredLyrics);
		if (enteredLyrics !== "") {
			sound = new Howl({
				src: [lyricData.afterMp3path],
				onend: ()=>nextLyric()
			});
			sound.play();
		}
	}
</script>

{#key lyricId}
<GameHeader {playlistData} {lyricData} />

<div class="game-body">
	<Lyrics
		{lyricData}
		currentLyricId={lyricId}
		bind:enteredLyrics
		{beforeFinished}
	/>
</div>
{/key}
