<script>
  import { each } from "svelte/internal";

  export let user;
</script>

<div class="card">
  <div class="title">{user.userName}</div>
  <ul class="tags">
    {#each user.skills as item}
      <li>{item}</li>
    {/each}
  </ul>
  <p class="user-info">{user.information}</p>
</div>

<style lang="scss">
  .card {
    border: 1px solid black;
    padding: 10px;
    width: fit-content;
    border-radius: 6px;
    margin-bottom: 20px;
    margin-left: 20px;
    transition: all 0.3s ease;
    &:hover {
      transition: all 0.3s ease;
      border: 1px solid rgb(3, 65, 181);
      // background: #3fd3f946;
    }
    .title {
      font-size: 1.7rem;
      font-weight: 700;
      padding-left: 9px;
      color: #1a53fd;
    }
    ul {
      list-style-type: none;
      display: flex;
      margin: 2px;
      padding: 3px;

      li {
        text-transform: capitalize;
        padding: 5px;
        border-radius: 4px;
        border: 1px solid black;
        margin: 0px 4px;
        font-family: monospace;
        font-size: 0.9rem;
        cursor: pointer;
        &:hover {
          transition: all 0.3s ease;
          background: #fff67ef6;
          border: 1px solid #090909;
        }
      }
    }
    p {
      text-transform: capitalize;
      padding: 0;
      margin: 4px 10px;
    }
  }
</style>
