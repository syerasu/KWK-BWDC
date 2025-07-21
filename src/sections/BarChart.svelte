<script>
  import { onMount } from 'svelte';
  import { scrollObserver } from '../lib/utils/scrollObserver.js';
  import BarChart from '../lib/components/BarChart.svelte';

  const groups = [
    { name: 'Median Monthly Income', values: { 2019: 47.1, 2021: 48.2 } },
    { name: 'Median Monthly Housing Cost', values: { 2019: 25, 2021: 20.7 } },
  ];

  const colors = ['#E91E63', '#FF9800', '#4CAF50', '#2196F3'];

  const categories = groups.map(group => group.name);

  const series = [
    {
      name: '2019',
      data: groups.map((group, i) => ({
        y: group.values[2019],
        color: `${colors[i]}88`
      })),
      dataLabels: {
        enabled: true,
        format: '{y}%',
        style: { color: '#333', fontWeight: 'bold' }
      }
    },
    {
      name: '2021',
      data: groups.map((group, i) => ({
        y: group.values[2021],
        color: colors[i],
        borderColor: '#333',
        borderWidth: 2
      })),
      dataLabels: {
        enabled: true,
        format: '{y}%',
        style: { color: '#333', fontWeight: 'bold', textOutline: 'none' }
      }
    }
  ];

  let visible = false;
  let sectionElement;

  onMount(() => {
    scrollObserver(sectionElement, () => { visible = true; });
  });
</script>

<section class="data-section" bind:this={sectionElement}>
  <h2>STEM Representation Changes by Race (2019–2021)</h2>

  <div class="chart-wrapper">
    <BarChart
      title="Household Income Trends"
      subtitle="Household Income and Housing Costs in the Bronx"
      {categories}
      {series}
      {visible}
    />
  </div>

  <div class="legend">
    <div><span class="box box-2019"></span> 2019</div>
    <div><span class="box box-2021"></span> 2021</div>
  </div>

  <div class="insights">
    <div class="insight-card decline">
      <div class="icon">▼</div>
      <div>
        <h3>Decline in Representation</h3>
        <p>Black women were the only group to show a decline in STEM — dropping 4.3% between 2019 and 2021.</p>
      </div>
    </div>

    <div class="insight-card growth">
      <div class="icon">▲</div>
      <div>
        <h3>Growth Across Other Groups</h3>
        <p>White women (+2.7%) had the highest growth, followed by Hispanic (+1.5%) and Asian women (+1.1%).</p>
      </div>
    </div>
  </div>
</section>

<style>
  .data-section {
    padding: 4rem 2rem;
    background-color: #f8f9fa;
    text-align: center;
  }

  h2 {
    font-size: 2.25rem;
    color: #263238;
    margin-bottom: 2rem;
  }

  .chart-wrapper {
    background: #fff;
    padding: 1.5rem;
    border-radius: 10px;
    box-shadow: 0 4px 18px rgba(0,0,0,0.1);
    margin-bottom: 2rem;
    max-width: 900px;
    margin-inline: auto;
  }

  .legend {
    display: flex;
    justify-content: center;
    gap: 2rem;
    margin-bottom: 2rem;
    font-weight: 500;
  }

  .box {
    display: inline-block;
    width: 20px;
    height: 20px;
    margin-right: 0.5rem;
    border: 1px solid #333;
    border-radius: 3px;
  }

  .box-2019 {
    background: rgba(0, 0, 0, 0.2);
  }

  .box-2021 {
    background: #333;
  }

  .insights {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    max-width: 800px;
    margin-inline: auto;
  }

  .insight-card {
    background: #fff;
    border-radius: 10px;
    padding: 1.5rem;
    display: flex;
    align-items: flex-start;
    gap: 1rem;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
    border-left: 5px solid;
  }

  .decline {
    border-color: #E91E63;
  }

  .growth {
    border-color: #4CAF50;
  }

  .icon {
    font-size: 1.75rem;
    font-weight: bold;
    width: 40px;
    height: 40px;
    background-color: #eee;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  @media (max-width: 768px) {
    .insight-card {
      flex-direction: column;
      align-items: center;
      text-align: center;
    }

    h2 {
      font-size: 1.75rem;
    }

    .legend {
      flex-direction: column;
    }
  }
</style>
