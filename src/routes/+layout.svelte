<script lang="ts">
    import "$lib/css/app.css";
</script>

<main>
    <slot />
</main>

<style>
    main {
        width: 800px;
        max-width: 100%;
        margin: auto;
        padding-top: 100px;
    }
</style>