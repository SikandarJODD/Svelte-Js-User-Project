<script>
  import AddUsers from "./AddUsers.svelte";
  import FilterUser from "./FilterUser.svelte";
  import User from "./User.svelte";

  let usersDoc = [
    {
      userName: "Ramesh Shet",
      skills: [
        "html",
        "css",
        "sass",
        "tailwind css",
        "bootstrap",
        "python",
        "cpp",
      ],
      information:
        "Working in JP Morgan as AWS Developer | 3 Year Experience in AWS",
    },
    {
      userName: "Kritik Sathe",
      skills: ["python", "cpp", "ai", "backend developer"],
      information:
        "AI Engineer in Bolt | 4 Year Experience in AI and Object Recognigation",
    },
    {
      userName: "Aditya Kuber",
      skills: ["MERN", "react js", "mongoDB", "nodeJs", "python"],
      information:
        "Data Analyst at Dalal Street | 2 Years Exprience in Stock Prediction",
    },
    {
      userName: "Vishal Shenoy",
      skills: [
        "sveltejs",
        "sveltekit",
        "frontend",
        "Tailwind CSS",
        "sass",
        "cpp",
        "css",
      ],
      information: "Fronted Developer at CRED | 2 Year Expericne in Adobe",
    },
  ];
  let addUser = ({ detail }) => {
    usersDoc = [
      {
        userName: detail.name,
        skills: detail.skills,
        information: detail.information,
      },
      ...usersDoc,
    ];
  };
  $: orignalUser = usersDoc;

  let usersfilter = ({ detail }) => {
    let value = detail.toLowerCase();
    orignalUser = usersDoc.filter((stu) => stu.userName === "Ramesh Shet");
    if (value === "all") {
      orignalUser = usersDoc;
    } else {
      orignalUser = usersDoc.filter((person) => {
        let updatedSkills = person.skills.map((m) => m.toLowerCase());
        // console.log(updatedSkills.includes(value), updatedSkills, value);
        return updatedSkills.includes(value);
      });
    }
  };
  $: brocode = orignalUser.length;
</script>

<main>
  <div class="container">
    <FilterUser on:filteruser={usersfilter} />
    <h1>{brocode}</h1>
  </div>
  <div class="container">
    <div>
      <AddUsers on:adduser={addUser} />
    </div>
    <div>
      {#if orignalUser.length !== 0}
        {#each orignalUser as student}
          <User user={student} />
        {/each}
      {:else}
        <div class="badge">No user Found</div>
      {/if}
    </div>
  </div>
</main>

<style lang="scss">
  .container {
    display: flex;
    padding: 10px 3%;
    justify-content: center;
    margin: 10px auto;
    width: fit-content;
    &:nth-child(1) {
      border-radius: 10px;
      border: 1px solid #393939;
    }
    .badge {
      border-radius: 6px;
      padding: 10px 15px;
      font-size: 1.4rem;
      text-transform: capitalize;
      border: 1px solid blue;
      margin: 10px;
      &:hover {
        background: rgba(21, 57, 236, 0.085);
      }
    }
  }
</style>
