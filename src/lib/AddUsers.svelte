<script>
  import { createEventDispatcher } from "svelte";

  let userInfo = {};

  let dispatch = createEventDispatcher();
  let addUser = () => {
    userInfo.skills = userInfo.skills.split(",");
    dispatch("adduser", userInfo);
    userInfo.name="";
    userInfo.skills=[];
    userInfo.information="";
  };
</script>

<main>
  <div>
    <form on:submit|preventDefault={addUser}>
      <div>
        <label for="name">Name : </label>
        <input type="text" name="name" id="name" bind:value={userInfo.name} />
      </div>
      <div>
        <label for="skills">Skills : </label>
        <textarea
          name="skills"
          id="skills"
          cols="10"
          rows="5"
          bind:value={userInfo.skills}
        />
      </div>
      <div>
        <label for="inform">Information : </label>
        <textarea
          name="inform"
          id="inform"
          cols="10"
          rows="10"
          bind:value={userInfo.information}
        />
      </div>
      <button class="submitBtn" type="submit">Submit </button>
    </form>
  </div>
  <div>
    <!-- {name}
    {skills}
    {information} -->
  </div>
</main>

<style lang="scss">
  form {
    width: 280px;
    padding: 20px;
    border: 1px solid black;
    border-radius: 8px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    div {
      display: flex;
      flex-direction: column;
      label {
        font-size: 1.2rem;
        margin: 4px 0;
      }
      input,
      textarea {
        width: 250px;
        padding: 4px;
        border-radius: 4px;
        outline: none;
        border: 1px solid rgb(80, 79, 79);
        &:focus {
          border: 2px solid rgb(25, 60, 237);
        }
      }
      input,
      textarea {
        font-size: 1.1rem;
      }
    }
    .submitBtn {
      padding: 5px 10px;
      margin: 10px;
      border-radius: 4px;
      border: 1px solid #1717f5;
      font-size: 1.2rem;
      transition: all 0.3s ease;
      &:hover {
        transition: all 0.3s ease;
        background: #cceef9;
        box-shadow: 3px 3px rgb(21, 98, 241);
      }
    }
  }
</style>
