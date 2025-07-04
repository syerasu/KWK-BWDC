<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import ScrollWrapper from "../lib/ScrollWrapper.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    const series = [
        {
            name: "Group 1",
            data: [
                [1990, 3],
                [2000, 4],
                [2010, 1],
                [2020, 1],
            ],
            color: "#8427c9",
        },
        {
            name: "Group 2",
            data: [
                [1990, 2],
                [2000, 5],
                [2010, -2],
                [2020, 2],
            ],
            color: "#ff99fc",
        },
        {
            name: "Group 3",
            data: [
                [1990, 4],
                [2000, 3],
                [2010, 0],
                [2020, 3],
            ],
            color: "#4096fa",
        },
    ];

    let chart;
    let thirdSeriesVisible = true;

    let options = {
        chart: {
            type: "line",
            backgroundColor: "#e3ff00",
            borderColor: "#007052",
            borderWidth: 5,
            borderRadius: 20,
        },
        title: {
            text: "Another Example Chart",
        },
        subtitle: {
            text: "With a subtitle! And styling!",
        },
        series: [series[0], series[1]],
    };

    function toggleThirdSeries() {
        const existingSeries = chart.series.find((s) => s.name === "Group 3");

        if (existingSeries) {
            existingSeries.remove();
            thirdSeriesVisible = false;
        } else {
            chart.addSeries(series[2]);
            thirdSeriesVisible = true;
        }
    }
</script>

<div>
    <ScrollWrapper layout="left">
        <svelte:fragment slot="sticky">
            <div class="chart">
                <Chart bind:chart {options} highcharts={Highcharts} />
            </div>
            <button on:click={toggleThirdSeries} class="toggle-button">
                {thirdSeriesVisible ? "Remove Group 3" : "Add Group 3"}
            </button>
        </svelte:fragment>

        <svelte:fragment slot="scrolly">
            <ArticleText>
                <svelte:fragment slot="text">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                    do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua. Ut enim ad minim veniam, quis nostrud exercitation
                    ullamco laboris nisi ut aliquip ex ea commodo consequat.
                    Duis aute irure dolor in reprehenderit in voluptate velit
                    esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
                    occaecat cupidatat non proident, sunt in culpa qui officia
                    deserunt mollit anim id est laborum."
                </svelte:fragment>
            </ArticleText>

            <ArticleText>
                <svelte:fragment slot="text">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                    do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua.
                </svelte:fragment>
            </ArticleText>

            <ArticleText>
                <svelte:fragment slot="text">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed
                    do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua. Ut enim ad minim veniam, quis nostrud exercitation
                    ullamco laboris nisi ut aliquip ex ea commodo consequat.
                    Duis aute irure dolor in reprehenderit in voluptate velit
                    esse cillum dolore eu fugiat nulla pariatur. Excepteur sint
                    occaecat cupidatat non proident, sunt in culpa qui officia
                    deserunt mollit anim id est laborum."
                </svelte:fragment>
            </ArticleText>
        </svelte:fragment>
    </ScrollWrapper>
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
