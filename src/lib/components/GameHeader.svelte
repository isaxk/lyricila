<script lang="ts">
    export let playlistData:{id:number,name:string,image:string,lyrics:Array<number>};
    export let lyricData:{ songName: string, albumCover: string, artist: string};
    export let lyricId:number;
</script>

<div class="header">
	<div class="info">
		<div class="playlist">Playlist: {playlistData.name}</div>
		<div class="counter">Lyric: {lyricId+1}/{playlistData.lyrics.length}</div>
	</div>
    <div class="currentsonginfo">
        <div class="albumcover">
            <img src={lyricData.albumCover} alt="albumcover">
        </div>
        <div class="info">
            <div class="name">{lyricData.songName}</div>
            <div class="artist">{lyricData.artist}</div>
        </div>
    </div>
</div>

<style>
	.counter {
		font-size: 18px;
		font-weight: 400;
		letter-spacing: 0.1em;
	}
    .albumcover img {
        width: 75px;
        border-radius: 5px;
    }
    .currentsonginfo {
        display: grid;
        align-items: center;
        grid-template-columns: max-content 1fr;
        gap: 10px;
        margin-top: 20px;
    }
    .name {
        font-size: 20px;
        font-weight: 600;
    }
    .artist {
        font-size: 15px;
    }
</style>