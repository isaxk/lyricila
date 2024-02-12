<script lang="ts">
</script>

<div class="header">
	<div class="header-content">
		<a class="title" href="/">Lyricila</a>
		<div class="options">
			<a href="/settings">
				<span class="material-symbols-rounded"> settings </span>
			</a>
		</div>
	</div>
</div>

<style>
	.header {
		position: fixed;
		height: 50px;
		width: 100%;
		top: 0;
		background-color: #272727;
		padding: 0px 10px;
		box-sizing: border-box;
	}
	.header-content {
		width: 100%;
		height: 100%;
		max-width: 800px;
		padding: 0px 10px;
		box-sizing: border-box;
		margin: auto;
		display: grid;
		align-items: center;
		grid-template-columns: 1fr max-content;
	}
	.title {
		font-size: 25px;
		font-weight: 600;
		color: white;
		text-decoration: none;
	}
	.options {
		display: flex;
		align-items: center;
	}
	.options a {
		display: flex;
		align-items: center;
		text-decoration: none;
		color: white;
	}
</style>
