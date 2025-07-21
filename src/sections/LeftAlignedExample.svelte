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

                <p>
                    You can use Svelte to add and remove data from a Highcharts
                    chart.
                </p>
                <p>
                    When you click the button above, a third group is toggled in
                    the chart. Check out the source code to see how it's done.
                </p>
                <p>
                    <strong
                        >🤔 How might you use other HTML elements, like
                        checkboxes or radio buttons, in a similar way to filter
                        data?</strong
                    >
                </p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                You might notice that this basic template doesn't have certain
                features that are common in scrollytelling.
            </ArticleText>

            <ArticleText>
                For example, you might want a component that doesn't feature a
                sticky component at all. Or a component that is solely a sticky
                component.
            </ArticleText>

            <ArticleText>
                You might also want to add more interactivity or gamify parts of
                your scrollytelling piece.
            </ArticleText>

            <ArticleText>
                <strong>
                    It's up to you to research how to create the effects and
                    functionality that you envision!
                </strong>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 90%;
        margin: 0px auto;
    }

    .toggle-button {
        margin: 20px;
        padding: 20px;
        color: #007052;
        background-color: #0bd956;
        border: solid 2px #007052;
        border-radius: 16px;
        font-size: large;
        cursor: pointer;
        transition: all 0.2s ease;
        box-shadow: 0 4px 0 #007052;
    }

    .toggle-button:active {
        transform: translateY(2px);
        box-shadow: 0 2px 0 #007052;
    }
</style>
