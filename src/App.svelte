<script>
  import DATA from '../data/schools_players.json';

  const schools = Object.keys(DATA);
  let search = '';
  $: results = schools.filter(s => search.length > 2 && s.includes(search));
</script>

<main>
  <input bind:value={search} placeholder="enter at least 3 letters">
  <p><b>Search (at least 3 letters): {search}</b></p>

  {#each results as result}
    <p>{result}</p>
  {/each}

</main>

<style>
</style>