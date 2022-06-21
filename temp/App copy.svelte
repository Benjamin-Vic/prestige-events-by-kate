<script>
  import logo from "./assets/svelte.png";
  import Counter from "./src/src/lib/Counter.svelte";
</script>

<main>
  <div class="border-container">
    <div class="border-top">
      <span class="border-top-text">
        Kate, Lieu-dit Le Mas Blanc 66200 ALENYA
      </span>

      <span class="border-top-text"> Téléphone : 06 89 71 52 21 </span>
    </div>

    <div class="border-body">
      <div class="border-left" />


      <div class="border-right" />
    </div>

    <div class="border-bottom" />
  </div>

  <span>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla id placerat
    leo. Mauris sem metus, congue in lobortis sit amet, faucibus a tortor.
    Nullam vitae lectus vel dui condimentum facilisis sed ac ex. Donec posuere,
    nunc ut interdum gravida, dolor justo ornare nisi, vel finibus neque risus
    quis erat. Morbi a aliquet lectus, ac tincidunt diam. Integer blandit vel
    sem in lobortis. Suspendisse fringilla turpis eget sodales commodo. Nunc non
    leo scelerisque eros congue dictum. Donec id sem et neque pretium auctor a
    in neque. Cras et vehicula dui. Vestibulum sit amet eros id leo imperdiet
    tristique. Integer sed erat ac magna bibendum malesuada. Vivamus sed justo
    non tellus consectetur fermentum. Etiam fermentum elit in ullamcorper
    consequat. Phasellus volutpat sollicitudin nulla a lacinia. Nulla tincidunt
    ultricies sapien eget tempus. Aliquam eu metus non diam ultricies
    consectetur. Fusce gravida dapibus sapien, ut tempus eros rutrum vitae. Nam
    volutpat laoreet est quis commodo.
  </span>

  <!-- <img src={logo} alt="Svelte Logo" />
  <h1>Hello world!</h1>

  <Counter />

  <p>
    Visit <a href="https://svelte.dev">svelte.dev</a> to learn how to build Svelte
    apps.
  </p>

  <p>
    Check out <a href="https://github.com/sveltejs/kit#readme">SvelteKit</a> for
    the officially supported framework, also powered by Vite!
  </p> -->
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Roboto+Slab&display=swap");

  .border-container {
    position: absolute;
    width: 100%;
  }

  .border-top {
    /* width: 100vw; */
    height: 32px;
    background-color: white;

    display: flex;
    align-items: center;
    justify-content: space-between;

    padding: 0 32px;

    /* border: 1px solid red; */
  }

  .border-top-text {
    font-family: "Roboto Slab", serif;
    font-size: small;
  }

  .border-body {
    display: flex;
    justify-content: space-between; 
  }

  .border-left {
    width: 32px;
    height: calc(100vh - 64px);
    background-color: white;

    /* border: 1px solid green; */
  }

  .border-right {
    width: 32px;
    height: calc(100vh - 64px);
    background-color: white;

    /* border: 1px solid blue; */
  }

  .border-bottom {
    width: 100%;
    height: 32px;
    background-color: white;

    /* border: 1px solid red; */
  }

  .view {
    width: 100%;
    height: calc(100vh - 64px);

    /* border: 1px solid violet; */
  }

  /* :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  } */
</style>
