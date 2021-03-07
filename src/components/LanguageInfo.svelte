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
    z-index: 2;
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
    line-height: 130%;
  }

  :global(.lang-info p strong) {
    font-weight: normal;
  }

  :global(.lang-info img) {
    margin: 15px 0;
    width: 100%;
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

  .header img {
    max-height: 18px;
    width: 25px;
    margin: 2px;
  }

  .header .langs {
    margin-left: auto;
  }

  @media (min-width: 600px) {
    .logo {
      display: none;
    }

    .container {
      padding-top: 75px;
      max-width: 700px;
      margin-bottom: 0;
    }

    .lang-info {
      padding: 0 130px;
      max-width: none;
    }

    .header {
      margin-top: 30px;
      padding-top: 15px;
      margin-bottom: 5px;
    }

    .header:first-of-type {
      margin-top: 0;
      padding-top: 0;
    }
  }

  @media (min-width: 1000px) {
    .container {
      max-width: 750px;
    }

    .header h4,
    :global(.lang-info p) {
      font-size: 1.125rem;
    }
  }

  /* ANIMATION */

  @keyframes enter {
    from {
      opacity: 0;
      transform: translateY(-30px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .header,
  .body {
    animation-name: enter;
    animation-duration: 300ms;
    animation-timing-function: ease-in-out;
    animation-fill-mode: both;
  }
</style>

<svelte:window bind:scrollY />

<div class="container">
  <div class="logo" class:scrolled={scrollY > 25} class:noimg={!lang}>
    <img src={`langs/${lang}.svg`} alt={`${lang} logo`} class:noimg={!lang} />
  </div>
  <div class="lang-info">
    {#each data as d, i (`${lang}-${i}`)}
      <div class="header" style="animation-delay: {i * 100}ms">
        <h4>{d.year}</h4>
        <div class="langs">
          {#each d.langs as l}
            <img src={`langs/${l}.svg`} alt={`${l} logo`} />
          {/each}
        </div>
      </div>
      <div class="body" style="animation-delay: {i * 100 + 50}ms">
        {@html d.html}
      </div>
    {/each}
  </div>
</div>
