<script>
    let { title, subtitle , subtitleLink} = $props();
</script>

<div class="household-income">
    <div class="content">
        <h1>{title}</h1>
        <p>{subtitle}</p>
        <a href={subtitleLink} target="_blank" rel="noopener">{subtitle}</a>
    </div>
</div>

<style>
    .household-income {
        background: #f5f2ea;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        padding: 2rem;
        box-sizing: border-box;
        font-family: "Inter", sans-serif;
    }

    .content {
        max-width: 700px;
        background-color: #02022d ;
        padding: 2rem;
        border: 6px solid  #f5f2ea;
        border-radius: 2rem;
        box-shadow: 16px 16px #333333
;
    }

    h1 {
        font-size: 3rem;
        margin: 0;
        color: #f5f2ea;
        text-shadow: 1px 1px 0 #333333
;
    }

    p {
        font-size: 1.3rem;
        color: #f5f2ea;
        margin-top: 1rem;
    }

    @media (max-width: 600px) {
        h1 {
            font-size: 2.2rem;
        }

        p {
            font-size: 1.1rem;
        }
    }
</style>