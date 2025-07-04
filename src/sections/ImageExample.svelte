<script>
    import ScrollWrapper from "../lib/ScrollWrapper.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
    <ScrollWrapper layout="right">
        <svelte:fragment slot="sticky">
            <img class="duck-img" src="duck.png" alt="KWK rubber duck!" />
        </svelte:fragment>

        <svelte:fragment slot="scrolly">
            <ArticleText>
                <svelte:fragment slot="text">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                    do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua. Ut enim ad minim veniam, quis nostrud exercitation
                    ullamco laboris nisi ut aliquip ex ea commodo consequat.
                    Duis aute irure dolor in reprehenderit in voluptate velit
                    esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
                    occaecat cupidatat non proident, sunt in culpa qui officia
                    deserunt mollit anim id est laborum."
                </svelte:fragment>
            </ArticleText>

            <ArticleText>
                <svelte:fragment slot="text">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                    do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua.
                </svelte:fragment>
            </ArticleText>

            <ArticleText>
                <svelte:fragment slot="text">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                    do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua. Ut enim ad minim veniam, quis nostrud exercitation
                    ullamco laboris nisi ut aliquip ex ea commodo consequat.
                </svelte:fragment>
            </ArticleText>
        </svelte:fragment>
    </ScrollWrapper>
</div>

<style>
    .duck-img {
        width: 25%;
        margin: 0px auto;
    }
</style>