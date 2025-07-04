<script>
    let { children } = $props();
</script>

<div class="sticky">
    {@render children?.()}
</div>

<style>
    div.sticky {
        position: sticky;
        top: 0;
        border-color: #007052;
        border-style: solid;
        background-color: #0bd956;
        z-index: -1;
    }
</style>