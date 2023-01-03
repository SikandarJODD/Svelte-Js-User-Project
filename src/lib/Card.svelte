<script>
  let imgDoc = [
    {
      src: "https://cdn-icons-png.flaticon.com/512/9175/9175333.png",
      title: "Nice",
    },
    {
      src: "https://cdn-icons-png.flaticon.com/512/9094/9094304.png",
      title: "Preety",
    },
    {
      src: "https://cdn-icons-png.flaticon.com/512/9175/9175296.png",
      title: "Buddy",
    },
  ];

  let i = 0;
</script>

<main>
  <button on:click={() => (i = i + 1)}>Increment</button>
  <div>
    <img src={imgDoc[i].src} alt={imgDoc[i].title} />
    <h1 class="title">{imgDoc[i].title}</h1>
  </div>
  <button on:click={() => (i = i - 1)}>Decrement</button>
</main>
