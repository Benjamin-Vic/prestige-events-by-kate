<script>
  // @ts-nocheck
  import { fly } from "svelte/transition";

  let is_top = true;

  let container_html;
  let button_html;

  const navigationTopFunc = () => {
    is_top = window.scrollY <= 10 ? true : false;

    container_html = document.getElementsByClassName("navigation-container");
    button_html = document.getElementsByClassName("button-navigation");

    container_html[0].style["background-color"] = is_top
      ? "transparent"
      : "white";

    for (let i = 0; i < button_html.length; i++) {
      if (!button_html[i].style) continue;
      button_html[i].style["color"] = is_top ? "white" : "black";
      button_html[i].style["border-color"] = is_top ? "white" : "black";
    }
  };

  document.addEventListener("scroll", navigationTopFunc, false);
</script>

<navigation>
  <div class="navigation-container">
    <div class="navigation-container-left">
      <a class="button-navigation" href="/"> Accueil </a>
      <a class="button-navigation" href="/mariage"> Mariage </a>
      <a class="button-navigation" href="/evenementiel"> Événementiel </a>
      <a class="button-navigation" href="/photos"> Photos </a>
    </div>

    {#if is_top}
      <a class="button-navigation" href="/" in:fly={{ y: -200, duration: 500 }}>
        <img src="/src/assets/logo.png" alt="logo" width="160px" />
      </a>
    {:else}
      <a class="button-navigation" href="/" in:fly={{ y: -200, duration: 500 }}>
        <img src="/src/assets/logo_bis.png" alt="logo_bis" width="160px" />
      </a>
    {/if}

    <div class="navigation-container-right">
      <a class="button-navigation" href="/"> EVJF / EVJG </a>
      <a class="button-navigation" href="/"> Bridal Shower </a>
      <a class="button-navigation" href="/"> Baby Shower </a>
      <a class="button-navigation" href="/"> Contact </a>
    </div>
  </div>

  <div class="navigation-container-mobile">
    <div class="navigation-container-left">
      <button class="button-navigation" in:fly={{ y: -200, duration: 500 }}>
        <img src="/src/assets/icons/menu.svg" alt="menu" width="40px" />
      </button>
      <!-- <a class="button-navigation" href="/"> Accueil </a>
      <a class="button-navigation" href="/mariage"> Mariage </a>
      <a class="button-navigation" href="/evenementiel"> Événementiel </a>
      <a class="button-navigation" href="/photos"> Photos </a> -->
    </div>

    <a class="button-navigation" href="/" in:fly={{ y: -200, duration: 500 }}>
      <img src="/src/assets/logo_bis.png" alt="logo_bis" width="160px" />
    </a>

    <div class="navigation-container-right">
      <!-- <a class="button-navigation" href="/"> EVJF / EVJG </a>
      <a class="button-navigation" href="/"> Bridal Shower </a>
      <a class="button-navigation" href="/"> Baby Shower </a>
      <a class="button-navigation" href="/"> Contact </a> -->
    </div>
  </div>
</navigation>

<style scoped>
  .navigation-container {
    position: fixed;
    width: calc(100% - 76px);
    padding: 16px 0px;

    display: flex;
    justify-content: space-between;
    z-index: 2;

    transition: background-color 500ms linear;
  }

  .navigation-container-left {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-around;
  }

  .navigation-container-right {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-around;
  }

  .button-navigation {
    color: white;
    font-family: "Playfair Display", serif;
    font-size: 16px;
    font-weight: 600;
    text-decoration: none;
    line-height: 2em;
    background-color: transparent;
    border: 0;
    margin: 0;
    padding: 0;
  }

  .button-navigation:after {
    display: block;
    content: "";
    border-bottom: solid 3px;
    transform: scaleX(0);
    transition: transform 250ms ease-in-out;
  }

  .button-navigation:hover:after {
    transform: scaleX(1);
  }

  .navigation-container-mobile {
    display: none;

    position: fixed;
    width: 100%;
    padding: 16px 0px;

    justify-content: space-between;
    z-index: 2;

    background-color: white;
  }

  @media (max-width: 992px) {
    .navigation-container {
      display: none;
    }

    .navigation-container-mobile {
      display: flex;
    }
  }
</style>
