<script>
  import { onMount } from "svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

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

<!-- Broadband Gap Section -->
<section class="left-aligned-section">
  <h2>The Bronx is buffering.</h2>
  <p>
    In one of the most vibrant, culturally rich places in the U.S., nearly <strong>1 in 4 households</strong> in the Bronx still don’t have reliable broadband internet.
  </p>
  <p>
    Compare that to just <strong>1 in 10</strong> in Manhattan. This isn’t just a tech issue—it’s a symptom of something deeper.
  </p>
</section>

<!-- Education + Internet Section -->
<section class="left-aligned-section">
  <h2>Disconnected—and left behind</h2>
  <p>
    The digital divide mirrors another long-standing barrier: education.
  </p>
  <p>
    In the Bronx, only <strong>22% of adults</strong> hold a bachelor’s degree. That’s nearly half the citywide average.
  </p>
  <p>
    How can students thrive when <em>30% of low-income families</em> with kids can’t get online at home?
  </p>
</section>

<!-- Visual Contrast Section (Insert chart or map here) -->
<section class="left-aligned-section">
  <h2>A map of modern-day inequity</h2>
  <p>
    This chart reveals a sobering correlation: neighborhoods with the <strong>lowest internet access</strong> often have the <strong>lowest college attainment</strong>, too.
  </p>
  <p>
    In communities like Mott Haven, the numbers drop to just <strong>16% with a bachelor’s degree</strong>.
  </p>
  <p>
    Technology—and opportunity—aren’t distributed equally.
  </p>
</section>

<!-- Personal/Local Voice Section -->
<section class="left-aligned-section">
  <h2>"We had WiFi, but it never worked"</h2>
  <p>
    <em>“During COVID, I had to write essays on my phone data. The WiFi at home barely loaded Google Docs.”</em>  
  </p>
  <p>
    Stories like this one, from a high school junior in the South Bronx, aren’t rare. They’re the norm.
  </p>
  <p>
    The Bronx isn’t behind—it’s been held back.
  </p>
</section>

<!-- Call to Action Section -->
<section class="left-aligned-section">
  <h2>Broadband is a basic right</h2>
  <p>
    No student should have to chase WiFi in a fast food parking lot to finish homework.
  </p>
  <p>
    No family should have to choose between groceries and a $90/month internet bill.
  </p>
  <p>
    <strong>Digital equity is a racial, economic, and educational justice issue.</strong>
  </p>
</section>

<!-- Closing: Hopeful note + resource -->
<section class="left-aligned-section">
  <h2>The future is fiber—and fair funding</h2>
  <p>
    Organizations like <a href="https://thebronx.org/digital-equity-coalition" target="_blank">The Bronx Digital Equity Coalition</a> are fighting for broadband for all.
  </p>
  <p>
    With the right investments, we can make sure every Bronx student logs in—equally.
  </p>
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
</style>
import { fly, fade } from "svelte/transition";