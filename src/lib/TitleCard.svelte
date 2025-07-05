<script>
    export let title = "Welcome to the KWK Scrollytelling Template";
    export let subtitle =
        "An unforgettable journey through code and creativity.";
</script>

<div class="title-card">
    <div class="content">
        <h1>{title}</h1>
        <p>{subtitle}</p>
    </div>
</div>

<style>
    .title-card {
        background-color: #e3ff00;
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
        background-color: #8427c9;
        padding: 2rem;
        border: 6px solid #ff99fc;
        border-radius: 2rem;
        box-shadow: 16px 16px #8aa6df;
    }

    h1 {
        font-size: 3rem;
        margin: 0;
        color: #0bd956;
        text-shadow: 1px 1px 0 #007052;
    }

    p {
        font-size: 1.3rem;
        color: #f7f5eb;
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
