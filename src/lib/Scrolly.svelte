<script>
    let { children } = $props();
</script>

<div class="scrolly">
    {@render children?.()}
</div>

<style>
    div.scrolly {
        border-color: #ff99fc;
        border-style: solid;
    }
</style>