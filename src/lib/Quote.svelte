<script>
    let { title, subtitle } = $props();
</script>

<div class="title-card">
    <div class="content">
        <h1>{title}</h1>
        <p>{subtitle}</p>
    </div>
</div>

<style>
    .title-card {
        background-color:#02022d;
        background-size: cover;
        height: 50vh;
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
        border: 6px solid #D4AF37;
        box-shadow: 16px 16px #FFECB3
;
    }

    h1 {
        font-size: 3rem;
        margin: 0;
        color: #f5f2ea;
        text-shadow: 1px 1px 0 #FFECB3 
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