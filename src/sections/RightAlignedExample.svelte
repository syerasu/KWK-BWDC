<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    let options = {
        chart: {
            type: "pie",
            zooming: {
                type: "xy",
            },
        },

        title: {
            text: "An Example Pie Chart",
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
                    {
                        name: "Group 1",
                        y: 151,
                    },
                    {
                        name: "Group 2",
                        sliced: true,
                        selected: true,
                        y: 180,
                    },
                    {
                        name: "Group 3",
                        y: 32,
                    },
                    {
                        name: "Group 4",
                        y: 103,
                    },
                    {
                        name: "Group 5",
                        y: 77,
                    },
                ],
            },
        ],
    };
</script>

<div>
    <Scroller layout="right">
        <svelte:fragment slot="sticky">
            <Chart {options} highcharts={Highcharts} />
            <p>
                Here's an example chart using
                <a href="https://www.highcharts.com/">Highcharts</a>!
            </p>
            <p>
                Highcharts is a super-flexible library for creating all kinds of
                charts. See demos of different chart types <a
                    href="https://www.highcharts.com/demo">here</a
                >.
            </p>
            <p>
                Since we're using Highcharts through Svelte, the syntax is a
                little different from what you might see in the demos. But all
                of Highcharts' functionality is available through the Highcharts
                for Svelte package. The configuration is done through the
                <code>options</code> json object passed to the chart, which you'll
                see in the source code for this template.
            </p>
            <p>
                Use the
                <a href="https://api.highcharts.com/highcharts/"
                    >API reference</a
                >
                to understand what each element in the <code>options</code> object
                does.
            </p>
        </svelte:fragment>

        <svelte:fragment slot="scrolly">
            <ArticleText>
                <svelte:fragment slot="text">
                    Welcome to the KWK Data Scrollytelling Template!
                </svelte:fragment>
            </ArticleText>

            <ArticleText>
                <svelte:fragment slot="text">
                    This is a basic example of how you might create a
                    scrollytelling piece using Svelte and Highcharts.
                </svelte:fragment>
            </ArticleText>

            <ArticleText>
                <svelte:fragment slot="text">
                    You can use this template as a starting point for your
                    project. Or, if you want to build something from scratch,
                    you can use it as a reference for specific functionality.
                </svelte:fragment>
            </ArticleText>

            <ArticleText>
                <svelte:fragment slot="text">
                    This is only one way that scrollytelling can look. If you
                    use this template, be sure to modify it and make it your
                    own!
                </svelte:fragment>
            </ArticleText>
        </svelte:fragment>
    </Scroller>
</div>
