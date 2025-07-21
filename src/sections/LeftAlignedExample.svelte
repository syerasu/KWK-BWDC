<script>
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

  let chart;

  let options = {
    chart: {
      type: "column"
    },
    title: {
      text: "Rate of Degree Attainment vs Average Yearly Expenditures"
    },
    subtitle: {
      text:
        'Source: <a target="_blank" href="https://www.indexmundi.com/agriculture/?commodity=corn">indexmundi</a>'
    },
    xAxis: {
      categories: [
        "Bachelors Degree or Higher Attainment",
        "Population with Health Insurance",
        "Population with Broadband Internet Access",
        "Population Using Broadband Internet Access"
      ],
      crosshair: true,
      accessibility: {
        description: "Percentage"
      }
    },
    yAxis: {
      min: 0,
      title: {
        text: "100%"
      }
    },
    tooltip: {
      valueSuffix: " (100%)"
    },
    plotOptions: {
      column: {
        pointPadding: 0.2,
        borderWidth: 0
      }
    },
    series: [
      {
        name: "Bronx, NY",
        data: [27, 92.7, 88.4, 50.0],
        color: "#4096fa"
      }
    ]
  };

  function toggleExampleSeries() {
    const existing = chart.series.find((s) => s.name === "Example Group");

    if (existing) {
      existing.remove();
    } else {
      chart.addSeries({
        name: "Example Group",
        data: [35, 80, 70, 60],
        color: "#ff99fc"
      });
    }
  }
</script>

<div>
  <Scroller layout="left">
    {#snippet sticky()}
      <div class="chart">
        <Chart bind:chart {options} highcharts={Highcharts} />
      </div>

    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        Observe the percentage of the population that holds a Bachelor's Degree or Higher vs the percentage of the population that has acess to internet usage. (There are <strong>MUCH</strong> more people with acess to the internet than those with a Bachelor's Degree or Higher.)
      </ArticleText>

      <ArticleText>
        <strong> Access ≠ Attainment</strong> 
        While the internet is accessible to a large portion of the population, it does not guarantee that individuals know how to use it effectively for educational purposes.
      </ArticleText>

      <ArticleText>
        Digital literacy is not emphasized enough today, leading to gaps in peoples lives and education.
      </ArticleText>

<ArticleText>
  <strong>
    There are many free sites online that can help the underprivileged learn how to use the internet effectively, such as 
    <a href="https://www.khanacademy.org" target="_blank" rel="noopener noreferrer">Khan Academy</a>, 
    <a href="https://www.codecademy.com" target="_blank" rel="noopener noreferrer">Codecademy</a>, and 
    <a href="https://www.coursera.org" target="_blank" rel="noopener noreferrer">Coursera</a>.
  </strong>
</ArticleText>

    {/snippet}
  </Scroller>
</div>

<style>
  .chart {
    width: 100%;
    margin: 0px auto;
  }
</style>
