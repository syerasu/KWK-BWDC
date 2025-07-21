<script>
    import HouseholdIncome from "../lib/HouseholdIncome.svelte";

    const title = "The median household income in the US in 2022 was $76,330";
    const subtitle = "United States Census Bureau";
    const subtitleLink = "https://www.census.gov/library/publications/2023/demo/p60-279.html";
</script>

<HouseholdIncome {title} {subtitle} {subtitleLink} />
