<script lang="ts">
	export let playlist: {
		id: number;
		name: string;
		image: string;
		lyrics: Array<number>;
	};
	export let i: number;
</script>

<div class="playlist">
	<div class="id">{i + 1}</div>
	<div class="image-container">
		<img src={playlist.image} alt="Album Cover" />
	</div>
	<div class="info">
		<div class="name">{playlist.name}</div>
	</div>
	<div class="options">
		<a href="/play" class="play">
			<span class="material-symbols-rounded"> play_arrow </span>
        </a>
	</div>
</div>

<style>
	.playlist {
		display: grid;
		grid-template-columns: max-content 60px 1fr max-content;
		height: 60px;
		padding: 10px 20px;
		align-items: center;
		gap: 20px;
		background-color: #272727;
		border-radius: 5px;
	}
	.image-container img {
		width: 100%;
		height: 100%;
		border-radius: 5px;
	}
	.info .name {
		font-size: 20px;
		font-weight: 500;
	}
	.options {
		display: grid;
		align-items: center;
	}
	.play {
		background-color: #2c5affbe;
        color: white;
        text-decoration: none;
		width: 40px;
		height: 40px;
		border-radius: 50%;
		display: grid;
		place-content: center;
	}
</style>
