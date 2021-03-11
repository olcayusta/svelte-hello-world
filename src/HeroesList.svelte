<script>
  import HeroDetail from "./HeroDetail.svelte";

  // export let heroes;
  let selectedHero;

  let heroesPromise = getPeople();

  async function getPeople() {
    const response = await fetch("https://swapi.dev/api/people");
    const json = await response.json();
    return json.results;
  }

  function save({ detail: heroToSave }) {
    console.table(heroToSave);
  }
</script>

<h1>Heroes List</h1>
{#await heroesPromise}
  Heroes galaxy
{:then heroes}
  <ul>
    {#each heroes as hero}
      <li
        class="row"
        on:click={() => (selectedHero = hero)}
        class:selected={selectedHero === hero}
      >
        {hero.name}
      </li>
    {/each}
  </ul>
{:catch error}
  <div class="error">{error}</div>
{/await}

{#if selectedHero}
  <HeroDetail hero={selectedHero} on:saveHero={save} />
{/if}

<style>
  ul {
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 4px;
  }
  li {
    list-style-type: none;
    height: 48px;
    line-height: 48px;
    border-radius: 8px;
  }
  .selected {
    background-color: gainsboro;
  }
</style>
