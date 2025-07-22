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
        <strong>Access ≠ Attainment</strong>: While the internet is accessible to a large
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

<section class="image-with-text-overlays">
  <div class="text-box top-left">
    <h2>Disconnected and left behind</h2>
    <p>The digital divide mirrors another long-standing barrier: education.</p>
    <p>In the Bronx, only <strong>22% of adults</strong> hold a bachelor’s degree.</p>
  </div>

  <div class="text-box bottom-right">
    <h2>Broadband is a basic right</h2>
    <p>No student should have to chase WiFi in a fast food parking lot.</p>
    <p><strong>Digital equity is a justice issue.</strong></p>
  </div>
</section>

<style>
  .chart-container {
    width: 100%;
    height: 400px;
    margin: 0 auto;
  }

  @media (max-width: 768px) {
    .chart-container {
      height: 400px;
    }
  }

  .image-with-text-overlays {
  position: relative;
  background-image: url('/newyork.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 800px;
  width: 100%;
  margin-bottom: 2rem;
  font-family: 'Inter', sans-serif;
  color: #f5f2ea;
}

.text-box {
  position: absolute;
  max-width: 50%;
  padding: 1.5rem;
  background-color: rgba(2, 2, 45, 0.75); 
  border-radius: 0.5rem;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.4);
}

.text-box h2 {
  font-size: 1.5rem;
  margin-bottom: 0.75rem;
  color: #FFECB3;
}

.text-box p {
  font-size: 1.1rem;
  line-height: 1.6;
}

.top-left {
  top: 4rem;
  left: 2rem;
}

.bottom-right {
  bottom: 4rem;
  right: 2rem;
}

@media (max-width: 768px) {
  .image-with-text-overlays {
    height: auto;
    padding: 2rem 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .text-box {
    position: static;
    max-width: 100%;
    margin: 1rem 0;
  }
}
</style>
