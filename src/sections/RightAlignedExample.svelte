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
        This chart represents estimated 2024 household spending breakdowns in the Bronx.
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

<!-- Broadband Gap Section -->
<section class="background-image-section">
  <div class="overlay">
  <h2>The Bronx is buffering.</h2>
  <p> The Bronx is home to over 1.4 million people, yet it’s often left behind in the digital age. Nearly <strong>1 in 4 households</strong> in the Bronx still don’t have reliable broadband internet.
  </p>
  <p>
    Compare that to just <strong>1 in 10</strong> in Manhattan. This isn’t just a tech issue—it’s a symptom of something deeper.
  </p>
  <p> Only 22% of Bronx residents (age 25+) hold a bachelor’s degree, among the lowest in NYC.
  </p>
</div>
</section>

<style>
  .chart {
    width: 90%;
    margin: 0px auto;
  }

  a {
    color: #1e90ff;
    text-decoration: underline;
  }
.title-card {
    background-color: #02022d;
    background-size: cover;
    height: 50vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    box-sizing: border-box;
    font-family: "Inter", sans-serif;
  }

  .content {
    max-width: 700px;
    background-color: #02022d;
    padding: 2rem;
    border: 6px solid #D4AF37;
  }

  h1 {
    font-size: 3rem;
    margin: 0;
    color: #f5f2ea;
    text-shadow: 1px 1px 0 #FFECB3;
  }

  p {
    font-size: 1rem;
    color: #f5f2ea;
    margin-top: 1rem;
  }

  @media (max-width: 600px) {
    h1 {
      font-size: 2.2rem;
    }

    p {
      font-size: 1rem;
    }
  }
  /* Section Styling */
.left-aligned-section {
  background-color: #02022d;
  padding: 3rem 2rem;
  max-width: 800px;
  margin: 3rem auto;
  border-left: 6px solid #D4AF37;
  border-radius: 8px;
  box-shadow: 12px 12px 0 #FFECB3;
  font-family: "Inter", sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.left-aligned-section h2 {
  font-size: 2.3rem;
  color: #f5f2ea;
  margin-bottom: 1rem;
  text-shadow: 1px 1px 0 #FFECB3;
}

/* Section Image Block */
.section-image {
  max-width: 800px;
  margin: 2rem auto;
  text-align: center;
}

@media (max-width: 600px) {
  .left-aligned-section h2 {
    font-size: 1.6rem;
  }

  .left-aligned-section p {
    font-size: 1rem;
  }

  .section-image img {
    max-height: 280px;
  }
}
.background-image-section {
  background-image: url('/us.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  color: #f5f2ea;
  padding: 8rem 6rem;
  text-align: left;
  position: relative;
}

.background-image-section .overlay {
  background-color: rgba(2, 2, 45, 0.8); 
  padding: 2rem;
  border: 4px solid #D4AF37;
  max-width: 700px;
  box-shadow: 12px 12px #FFECB3;
  font-family: 'Inter', sans-serif;
}

.background-image-section h2 {
  font-size: 2.5rem;
  color: #FFECB3;
  margin-bottom: 1rem;
  text-shadow: 1px 1px 0 #02022d;
}

.background-image-section p {
  font-size: 1.2rem;
  margin-top: 1rem;
  color: #f5f2ea;
}
</style>