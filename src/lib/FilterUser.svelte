<script>
  import { createEventDispatcher } from "svelte";

  let dispatch = createEventDispatcher();
  let filterData = (e) => {
    dispatch("filteruser", e.target.value);
  };
</script>

<main>
  <div class="card">
    <label for="skillValue">Filter User : </label>
    <select name="skillValue" id="skillVal" on:change={filterData}>
      <option value="all" selected>All Users</option>
      <option value="artifical intelligence">Artifial Intelligence</option>
      <option value="python">Python</option>
      <option value="html">Html</option>
      <option value="css">CSS</option>
      <option value="svelteJs">Svelte Js</option>
      <option value="sass">SASS</option>
      <option value="frontend"> Frontend Developer</option>
      <option value="react js">React Js Developer </option>
      <option value="backend"> Backend Developer</option>
      <option value="node js">Node Js </option>
    </select>
  </div>
</main>

<style lang="scss">
  .card {
    label {
      font-size: 1.2rem;
      margin-left: 10px;
    }
    select {
      border: 1px solid black;
      border-radius: 4px;
      font-size: 1rem;
      padding: 2px 3px;
    }
  }
</style>
