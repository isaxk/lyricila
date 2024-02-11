<script lang="ts">
	import Playlist from "$lib/components/Playlist.svelte";
	import { playlists } from "$lib/playlists";
</script>

<svelte:head>
	<title>Lyricila</title>
</svelte:head>

<div class="header">
	<h1>Lyricila</h1>
	<h3>The minimal finish the lyric game</h3>
</div>

<div class="playlist-selection">
	<h2>Choose playlist:</h2>
	{#each playlists as playlist, i}
		<Playlist {playlist} {i} />
	{/each}
</div>

<style>
	.header {
		border-bottom: 2px solid grey;
		padding: 20px 0px;
	}
</style>
