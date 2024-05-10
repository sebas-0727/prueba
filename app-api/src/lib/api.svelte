<script>
    export let id;

    const fetchNew = (async () => {
        try {
			const response = await fetch(`https://hacker-news.firebaseio.com/v0/item/${id}.json?print=pretty`);
			if(!response.ok){
				throw new Error("API broken")
			}
			return await response.json();
		} catch (error) {
			
		}
    })()

</script>

{#await fetchNew}
    <p>Esperando noticias..</p>
{:then data} 
    <article>
        <h3><a target="_blank" rel="noreferrer" href={data?.url}>{data.title}</a></h3>
        <p>Publicado por {data.by}	</p>
    </article>
{/await}

<style>
	article {
		position: relative;
		padding: 0 0 0 2em;
		border-bottom: 1px solid #eee;
	}

	h3 {
		font-size: 1.1rem;
		margin: 0.5em 0;
		text-align: left;
	}

	a {
		color: aliceblue;

	}
</style>