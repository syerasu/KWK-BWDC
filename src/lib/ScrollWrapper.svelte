<script>
    let { children } = $props();
</script>

<div class="scroll-wrapper">
    {@render children?.()}
</div>

<style>
    div.scroll-wrapper {
        width: 50vw;
    }
</style>
