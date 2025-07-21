<script>
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

  let options = {
    chart: {
      type: "pie",
    },
    title: {
      text: "Average Household Expenditure in the Bronx, New York (2024)",
    },
    plotOptions: {
      pie: {
        allowPointSelect: true,
        dataLabels: [
          {
            enabled: true,
            distance: 20,
          },
          {
            enabled: true,
            distance: -40,
            format: "{point.percentage:.1f}%",
            style: {
              fontSize: "1.2em",
              textOutline: "none",
            },
            filter: {
              operator: ">",
              property: "percentage",
              value: 10,
            },
          },
        ],
      },
    },
    series: [
      {
        name: "Group",
        data: [
          { name: "Food", y: 12.5 },
          { name: "Household", sliced: true, selected: true, y: 37.5 },
          { name: "Transportation", y: 37.5 },
          { name: "Health Services", y: 15.5 },
          { name: "Other", y: 20 },
        ],
      },
    ],
  };
</script>

<div>
  <Scroller layout="right">
    {#snippet sticky()}
      <div class="chart">
        <Chart {options} highcharts={Highcharts} />
      </div>
      <p>
        (Data from
        <a href="https://fred.stlouisfed.org/series/MHINY36005A052NCEN" target="_blank" rel="noopener noreferrer">
          The Federal Reserve Bank of St. Louis
        </a>.)
      </p>
      <p>
        📊 This chart represents estimated 2024 household spending breakdowns in the Bronx.
      </p>
      <p>
        Want to learn how to build your own? Check out the
        <a href="https://www.highcharts.com/demo">Highcharts demo gallery</a> or
        explore the <a href="https://api.highcharts.com/highcharts/">API reference</a>.
      </p>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        As seen in the pie chart, more than <strong>60%</strong> of the average household expenditure in the Bronx is allocated to housing and transportation costs, leaving less than <strong>40%</strong> for other essential needs like food and health services.
      </ArticleText>

      <ArticleText>
        We are privileged not to have to worry about having a roof over our heads or about where the money for necessities like food or healthcare will come from.
      </ArticleText>

      <ArticleText>
        The lack of worry about these basic needs allows us to focus on our education and personal growth, which is a luxury that we are lucky enough to take advantage of. <strong>This is a privilege not afforded to many.</strong>
      </ArticleText>
    {/snippet}
  </Scroller>
</div>

<style>
  .chart {
    width: 90%;
    margin: 0px auto;
  }

  a {
    color: #1e90ff;
    text-decoration: underline;
  }
</style>