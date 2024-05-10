<script>
  import Form from './lib/api.svelte'
  
  const PAGE_SIZE = 20;

  const latest_stories = (async () => {
    try {
      const res = await fetch(`https://hacker-news.firebaseio.com/v0/newstories.json?print=pretty`)
      if(!res.ok){
        throw new Error ("Fail API")
      }
      return await res.json();

    } catch (error) {
      console.log(error)
    }
  })()
</script>

<main>

  <div class="list__container">
    <div class="list__header">
      <h1>Noticias para mí</h1>
    </div>
    {#await latest_stories}
      <p>Cargando...</p>
    {:then data} 
      <div class=" list__content">
        {#each data as id}
          <Form {id}></Form>
        {/each}

      </div>
    {/await}
  </div>
</main>

<style>
  :global(main){
    box-sizing: border-box;
    font-size: 62.5%; 
    /* 1 rem = 10px */

   text-align: center;
   margin: 0 auto;
  }
  h1{
    font-size: 3rem;
    text-align: left;
  }
</style>