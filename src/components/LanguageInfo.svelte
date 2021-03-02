<script>
  export let lang;
  export let data = [];
  let scrollY;
</script>

<style>
  .container {
    padding-bottom: 75px;
    width: 100%;
    margin-bottom: auto;
  }

  .logo {
    height: 80px;
    padding-left: 20px;
    position: sticky;
    top: 0;
    background-color: var(--clr-background);
    transition: box-shadow 100ms ease-in-out;
    box-shadow: none;
    display: flex;
    align-items: center;
  }

  .logo.scrolled {
    box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.05);
  }

  .logo img {
    width: 50px;
    height: 50px;
    transform: scale(1.5);
    opacity: 1;
    transition: all 100ms ease-in-out;
    transform-origin: top left;
  }

  .logo.scrolled img {
    transform: scale(1);
  }

  .logo.noimg img {
    transform: scale(0);
    opacity: 0;
  }

  .lang-info {
    width: 100%;
    padding: 0 20px;
    max-width: 500px;
    margin: 0 auto;
  }

  :global(.lang-info p) {
    font-weight: lighter;
    font-size: 1rem;
  }

  :global(.lang-info img) {
    margin: 10px 0;
    width: calc(100% - 20px);
    max-height: 300px;
    object-fit: contain;
    object-position: left;
  }

  :global(.lang-info a) {
    text-decoration: none;
    font-size: inherit;
    color: var(--clr-blue);
    font-weight: normal;
  }

  :global(.lang-info a:hover, .lang-info a:focus, .lang-info a:active) {
    color: var(--clr-blue-dark);
  }

  .header {
    display: flex;
    align-items: center;
    margin-top: 20px;
    padding-top: 10px;
    border-top: 1px solid rgba(0, 0, 0, 0.1);
  }

  .header:first-of-type {
    border-top: none;
  }

  .header h4 {
    font-size: 1rem;
    font-weight: normal;
  }

  .header > img {
    max-height: 20px;
    width: 25px;
    margin: 2px;
  }

  .header img:first-of-type {
    margin-left: auto;
  }

  @media (min-width: 600px) {
    .logo {
      display: none;
    }

    .container {
      padding-top: 75px;
      max-width: 750px;
      margin-bottom: 0;
    }

    .lang-info {
      padding: 0 130px;
      max-width: none;
    }

    .header:first-of-type {
      margin-top: 0;
      padding-top: 0;
    }
  }
</style>

<svelte:window bind:scrollY />

<div class="container">
  <div class="logo" class:scrolled={scrollY > 25} class:noimg={!lang}>
    <img src={`langs/${lang}.svg`} alt={`${lang} logo`} class:noimg={!lang} />
  </div>
  <div class="lang-info">
    {#each data as d}
      <div class="header">
        <h4>{d.year}</h4>
        {#each d.langs as l}
          <img src={`langs/${l}.svg`} alt={`${l} logo`} />
        {/each}
      </div>
      {@html d.html}
    {/each}
  </div>
</div>
