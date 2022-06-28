<script>
  import { Router, Route } from "svelte-routing";

  import Navigation from "./components/Navigation.svelte";

  import Home from "./pages/Home.svelte";
  import Wedding from "./pages/Wedding.svelte";
  import Events from "./pages/Events.svelte";
  import Pictures from "./pages/Pictures.svelte";
  import Credit from "./pages/Credit.svelte";

  export let url = "";
</script>

<main>
  <Router {url}>
    <div class="border border-top">
      <span class="border-top-text">
        <img
          src="/src/assets/hornements/head.svg"
          alt="line"
          width="16px"
          style="vertical-align: middle;"
        />
        Kate, Lieu-dit Le Mas Blanc 66200 ALENYA
      </span>
      <span class="border-top-text">
        <img
          src="/src/assets/hornements/head.svg"
          alt="line"
          width="16px"
          style="vertical-align: middle;"
        />
        Téléphone :
        <a href="tel:+33689715221" class="mobile-text">06.89.71.52.21</a>
      </span>
    </div>

    <div class="border border-left" />
    <div class="border border-right" />
    <div class="border border-bottom" />

    <Navigation />

    <div>
      <Route path="mariage" component={Wedding} />
      <Route path="evenementiel" component={Events} />
      <Route path="photos" component={Pictures} />
      <Route path="credit" component={Credit} />
      <Route path="/"><Home /></Route>
    </div>
  </Router>
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Playfair+Display&family=Roboto+Slab&display=swap");
  .border-top-text {
    font-family: "Roboto Slab", serif;
    font-size: small;
    padding: 0 38px;
  }

  .mobile-text {
    color: black;
    text-decoration: none;
    cursor: default;
  }

  main {
    border: 38px solid white;
    background-color: #f7f3f3;
  }

  .border {
    position: fixed;
    background-color: white;
  }

  .border-top,
  .border-bottom {
    width: 100%;
    height: 38px;
    z-index: 11;
  }

  .border-left,
  .border-right {
    width: 38px;
    height: 100%;
    z-index: 10;
  }

  .border-top {
    top: 0;
    left: 0;

    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .border-left {
    top: 0;
    left: 0;
  }

  .border-right {
    top: 0;
    right: 0;
  }

  .border-bottom {
    bottom: 0;
    left: 0;
  }

  @media (max-width: 992px) {
    .border-left,
    .border-right,
    .border-bottom {
      display: none;
    }

    main {
      border-left: none;
      border-right: none;
      border-bottom: none;
    }

    .border-top-text {
      padding: 0 8px;
    }
  }
</style>
