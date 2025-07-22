<script>
  import { onMount } from "svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
  import { fly, fade } from "svelte/transition";

  export let visible = true; // control animation on mount

  // Your chart data and config inputs
  const title = "Rate of Degree Attainment vs Average Yearly Expenditures";
  const subtitle =
    'Source: <a target="_blank" href="https://www.indexmundi.com/agriculture/?commodity=corn">indexmundi</a>';
  const categories = [
    "Bachelors Degree or Higher Attainment",
    "Population with Health Insurance",
    "Population with Broadband Internet Access",
    "Population Using Broadband Internet Access",
  ];
  const series = [
    {
      name: "Bronx, NY",
      data: [27, 92.7, 88.4, 50.0],
      color: "#4096fa",
    },
  ];

  let chartContainer;

  onMount(() => {
    import("highcharts").then((Highcharts) => {
      Highcharts.chart(chartContainer, {
        chart: {
          type: "bar",
          backgroundColor: "transparent",
          animation: visible ? { duration: 1000 } : false,
        },
        title: {
          text: title,
          style: {
            fontSize: "1.5rem",
            fontWeight: "bold",
          },
        },
        subtitle: {
          text: subtitle,
          useHTML: true,
          style: {
            color: "#666",
          },
        },
        xAxis: {
          categories,
          title: { text: null },
          labels: {
            style: {
              fontSize: "1.1rem",
              fontWeight: "bold",
            },
          },
        },
        yAxis: {
          min: 0,
          max: 100,
          title: {
            text: "Percentage",
            style: {
              fontSize: "1.1rem",
            },
          },
          labels: {
            format: "{value}%",
            style: {
              fontSize: "1rem",
            },
          },
        },
        plotOptions: {
          bar: {
            pointPadding: 0.1,
            groupPadding: 0.2,
            dataLabels: {
              enabled: true,
              style: {
                fontSize: "0.9rem",
                fontWeight: "bold",
                textOutline: "none",
              },
            },
          },
          series: {
            animation: visible ? { duration: 1000 } : false,
            states: {
              hover: {
                brightness: 0.1,
              },
            },
          },
        },
        legend: {
          enabled: true,
          reversed: false,
          itemStyle: {
            fontWeight: "bold",
            fontSize: "1rem",
          },
        },
        tooltip: {
          headerFormat: "<b>{point.key}</b><br>",
          pointFormat: "{series.name}: <b>{point.y}%</b>",
        },
        credits: {
          enabled: false,
        },
        series,
      });
    });
  });
</script>

<div>
  <Scroller layout="left">
    {#snippet sticky()}
      <div bind:this={chartContainer} class="chart-container"></div>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        Observe the percentage of the population that holds a Bachelor's Degree or
        Higher vs the percentage of the population that has access to internet usage.
        (There are <strong>MUCH</strong> more people with access to the internet than
        those with a Bachelor's Degree or Higher.)
      </ArticleText>

      <ArticleText>
        <strong>Access ≠ Attainment</strong> — While the internet is accessible to a large
        portion of the population, it does not guarantee that individuals know how to
        use it effectively for educational purposes.
      </ArticleText>

      <ArticleText>
        Digital literacy is not emphasized enough today, leading to gaps in people's lives
        and education.
      </ArticleText>

      <ArticleText>
        <strong>
          There are many free sites online that can help the underprivileged learn how to
          use the internet effectively, such as
          <a href="https://www.khanacademy.org" target="_blank" rel="noopener noreferrer">
            Khan Academy
          </a>,
          <a href="https://www.codecademy.com" target="_blank" rel="noopener noreferrer">
            Codecademy
          </a>, and
          <a href="https://www.coursera.org" target="_blank" rel="noopener noreferrer">
            Coursera
          </a>.
        </strong>
      </ArticleText>
    {/snippet}
  </Scroller>
</div>

<!-- Section 1 -->
<section class="left-aligned-section">
  <h2>Disconnected—and left behind</h2>
  <p>The digital divide mirrors another long-standing barrier: education.</p>
  <p>In the Bronx, only <strong>22% of adults</strong> hold a bachelor’s degree. That’s nearly half the citywide average.</p>
  <p>How can students thrive when <em>30% of low-income families</em> with kids can’t get online at home?</p>
</section>

<!-- Image Between Sections -->
<div class="section-image">
  <img src="pexels-maoriginalphotography-2168975.jpg" alt="Bronx education gap" />
</div>

<!-- Section 3 -->
<section class="left-aligned-section">
  <h2>Broadband is a basic right</h2>
  <p>No student should have to chase WiFi in a fast food parking lot to finish homework.</p>
  <p>No family should have to choose between groceries and a $90/month internet bill.</p>
  <p><strong>Digital equity is a racial, economic, and educational justice issue.</strong></p>
</section>

<style>
  .chart-container {
    width: 100%;
    height: 500px;
    margin: 0 auto;
  }

  @media (max-width: 768px) {
    .chart-container {
      height: 400px;
    }
  }
  .left-aligned-section {
    margin: 0 auto;
    font-family: 'Inter', sans-serif;
    color: #f5f2ea;
    background-color: #02022d;
    margin-bottom: 2rem;
  }

  .left-aligned-section h2 {
    font-size: 2rem;
    margin-bottom: 1rem;
    color: #f5f2ea;
  }

  .left-aligned-section p {
    font-size: 1.2rem;
    line-height: 1.6;
    margin-bottom: 1rem;
  }

  .left-aligned-section strong {
    color: #f5f2ea;
  }
  .left-aligned-section em {
    font-style: italic;
    color: #f5f2ea;
  }

  .left-aligned-section a {
    color: #90CAF9;
    font-weight: bold;
  }

  @media (max-width: 600px) {
    .left-aligned-section {
    }

    .left-aligned-section h2 {
      font-size: 1.6rem;
    }

    .left-aligned-section p {
      font-size: 1rem;
    }
  }
  .section-image {
  text-align: center;
  margin: 2rem auto;
  max-width: 800px;
}

.section-image img {
  width: 100%;
  max-height: 400px;
  object-fit: cover;
  border-radius: 0.5rem;
  box-shadow: 0 4px 20px rgba(0,0,0,0.3);
}
</style>
