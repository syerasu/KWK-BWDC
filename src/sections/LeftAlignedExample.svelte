<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
Highcharts.chart('container', {
    chart: {
        type: 'column'
    },
    title: {
        text: 'Household Income vs Amount Spent on Rent for 2023'
    },
    subtitle: {
        text:
            'Source: <a target="_blank" ' +
            'href="https://www.indexmundi.com/agriculture/?commodity=corn">indexmundi</a>'
    },
    xAxis: {
        categories: ['Bachelors Degree or Higher Attainment', 'Population with Health Insurance', 'Population with Broadband Internet Access', 'Population Using Broadband Internet Access'],
        crosshair: true,
        accessibility: {
            description: 'Percentage'
        }
    },
    yAxis: {
        min: 0,
        title: {
            text: '100%'
        }
    },
    tooltip: {
        valueSuffix: ' (100%)'
    },
    plotOptions: {
        column: {
            pointPadding: 0.2,
            borderWidth: 0
        }
    },
    series: [
        {
            name: 'Bronx, NY',
            data: [27, 92.7, 88.4, 50.0]
        },

    ]
});
</script>