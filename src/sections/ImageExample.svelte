<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
    <Scroller layout="right">
        <svelte:fragment slot="sticky">
            <img class="duck-img" src="duck.png" alt="KWK rubber duck!" />
        </svelte:fragment>

        <svelte:fragment slot="scrolly">
            <ArticleText>
                <svelte:fragment slot="text">
                    Your final project might look totally different from this template! 
                </svelte:fragment>
            </ArticleText>

            <ArticleText>
                <svelte:fragment slot="text">
                    It's yours to create.
                </svelte:fragment>
            </ArticleText>
        </svelte:fragment>
    </Scroller>
</div>

<style>
    .duck-img {
        width: 25%;
        margin: 0px auto;
    }
</style>