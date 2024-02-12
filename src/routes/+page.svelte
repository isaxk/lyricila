<script lang="ts">
	import Playlist from "$lib/components/Playlist.svelte";
	import { playlists } from "$lib/playlists";
</script>

<svelte:head>
	<title>Lyricila</title>
</svelte:head>

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
	.playlist-selection {
		width: 100%;
		max-width: 600px;
	}
</style>
