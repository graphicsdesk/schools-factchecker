<script>
  import DATA from '../data/schools_players.json';

  const schools = Object.keys(DATA);
  const MIN_LETTERS = 3;

  let search = '';
  $: results = schools.filter(s => {
    if (search.length < MIN_LETTERS)
      return false;
    if (search.charAt(0) === '/') {
      let re;
      try {
        return s.match(new RegExp(search.replace('/', '')));
      } catch (e) {}
    }
    return s.includes(search)
  });
</script>

<main>
  <input bind:value={search} placeholder="enter at least {MIN_LETTERS} letters">
  <p><b>Search (prefix '/' makes a regex pattern): {search}</b></p>

  <i>Results: {results.length}</i>
  {#each results as result}
    <p>{result}</p>
  {/each}
</main>

<style>
</style>