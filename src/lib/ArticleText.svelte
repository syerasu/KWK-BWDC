<script>
    let { children } = $props();
</script>

<div class="article-text">
    <p>
        {@render children()}
    </p>
</div>

<style>
    .article-text {
        margin: 50vh auto;
        width: 50%;
        background-color: #DBE9FA;
        color: #030352;
        border: solid #8427c9 3px;
        border-radius: 20px;
        padding: 20px;
        box-shadow: 16px 16px #DBE9FA;
    }
</style>
