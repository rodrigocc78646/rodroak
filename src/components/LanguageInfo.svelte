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
    padding: 20px;
    padding-bottom: 10px;
    position: sticky;
    top: 0;
    background-color: var(--clr-background);
    transform: scaleY(1);
    transform-origin: top;
    transition: transform 200ms ease-in-out;
    box-shadow: none;
  }

  .logo img {
    width: 100px;
    height: 100px;
    object-fit: contain;
    transform: scale(1);
    transform-origin: top left;
    transition: transform 200ms ease-in-out;
  }

  .logo.small {
    box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.05);
    transform: scaleY(0.55);
    padding-bottom: 20px;
  }

  .logo.small img {
    transform: scale(0.55, 1);
  }

  .logo.smallnoimg {
    box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.05);
  }

  .logo img.noimg {
    opacity: 0;
    padding-top: 30px;
  }

  .lang-info {
    width: 100%;
    padding: 0 20px;
    max-width: 500px;
    margin: 0 auto;

  }
  
  .header {
    display: flex;
    align-items: center;
    margin-top: 20px;
    padding-top: 10px;
    border-top: 1px solid rgba(0, 0, 0, 0.1)
  }

  .header:first-of-type {
    border-top: none;
  }

  .header h4 {
    font-size: 1rem;
    font-weight: normal;
  }

  .header img {
    width: 20px;
    height: auto;
    margin-left: -5px;
  }

  .header img:first-of-type {
    margin-left: auto;
  }

  :global(.lang-info p) {
    font-weight: lighter;
    font-size: 1rem;
  }

  :global(.lang-info img) {
    margin: 10px;
    width: calc(100% - 20px);
    max-height: 300px;
    object-fit: contain;
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
  }
</style>

<svelte:window bind:scrollY />

<div class="container">
  <div
    class="logo"
    class:small={lang && scrollY > 25}
    class:smallnoimg={!lang && scrollY > 25}>
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
