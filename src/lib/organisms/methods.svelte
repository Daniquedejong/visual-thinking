<script>
  export let data;
</script>

<section class="grid">
  <h2>Alle methodes ({data.length})</h2>
  {#if data && data.length > 0}
    {#each data as method, index}
    <div class="methods-focus-state">
      <article class="methods-container" data-index={index}>
        <a href="/tekenmethodes/{method.slug}">
          {#if method.template && method.template.url}
            <picture>
              <img
                src={method.template.url.replace(":webp", ":png")}
                alt={"Voorbeeld van " + method.title}
                class={method.categories[0].title.replaceAll(" ", "-")}
              />
            </picture>
          {:else}
            <img
              class={method.categories[0].title.replaceAll(" ", "-")}
              src="/placeholder.webp"
              alt="Placeholder"
            />
          {/if}
        </a>
      </article>
      <h3>{method.title}</h3>
    </div>
    {/each}
  {/if}
</section>

<style>
  .grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 1.5rem;
    margin: 1rem 0;
  }

  h2 {
    grid-column: 1 / -1
  }

  h3 {
    font-family: var(--vtPrimaryFont);
    color: var(--vtDarkBlue);
    font-size: 19px;
    font-weight: 400;
    margin: 0;
    width: 100%;
  }

  a {
    text-decoration: none;
    color: black;
    margin-bottom: 5px;
  }

  article {
    display: flex;
    flex-direction: column;
    transition: 0.25s;
    border: 1px solid #ccc;
  }

  article img {
    width: 100%;
    height: auto;
  }

  .methods-focus-state:hover,
  .methods-focus-state:hover h3 {
    border: 1em solid #f9f8f8;
    border-bottom: 0.2em solid #feb51e;
    background-color: #f9f8f8;
    /* background: no-repeat; */
  }

  @media screen and (min-width: 36em) {
    .grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media screen and (min-width: 60em) {
    .grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }
</style>