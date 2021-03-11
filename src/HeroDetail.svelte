<script>
  import { createEventDispatcher } from "svelte";

  export let hero;
  const dispatch = createEventDispatcher();

  function saveHero() {
    dispatch("saveHero", hero);
  }
</script>

<div>
  <label for="name">Name</label>
  <input type="text" name="name" bind:value={hero.name} />
  <button type="submit" on:click={saveHero}>Kaydet</button>
</div>

<style></style>
