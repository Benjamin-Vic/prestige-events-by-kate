<script>
  import { onMount } from "svelte";
  import { fly } from "svelte/transition";

  let is_top = null;
  let is_mobile = null;
  let is_sidenav = false;

  let funcHandler = () => {};

  let funcTop = () => {};
  let funcMobile = () => {};
  let funcSidenav = () => {};

  onMount(async () => {
    funcTop = async () => (is_top = window.scrollY <= 10);
    funcMobile = async () => (is_mobile = window.innerWidth <= 992);
    funcSidenav = () => (is_sidenav = !is_sidenav);

    const handlerDesktop = () => {
      document.getElementById("container").style.borderTop =
        "38px solid var(--color-main)";

      const container = document.getElementById("container-nav-desktop");
      if (container == null) return;

      container.style.boxShadow = is_top
        ? "rgb(0 0 0 / 75%) 0px 275px 115px -150px inset"
        : "none";
      container.style.paddingBottom = is_top ? "5%" : "0";
      container.style.backgroundColor = is_top
        ? "transparent"
        : "var(--color-main)";

      const buttons = container.getElementsByClassName("button");

      for (let i = 0; i < buttons.length; i++) {
        if (!buttons[i].style) continue;
        buttons[i].style["color"] = is_top
          ? "var(--color-main)"
          : "var(--color-second)";
        buttons[i].style["border-color"] = is_top
          ? "var(--color-main)"
          : "var(--color-second)";
      }
    };

    const handlerMobile = () => {
      const container = document.getElementById("container-nav-mobile");
      if (container == null) return;

      const menuClientHeight =
        container.getElementsByClassName("sub-container menu")[0].clientHeight;

      document.getElementById("container").style.borderTop =
        menuClientHeight + 38 + "px solid var(--color-main)";
    };

    funcHandler = async () => {
      await funcMobile();
      await funcTop();

      !is_mobile ? handlerDesktop() : handlerMobile();
    };

    funcHandler();
  });
</script>

<svelte:window on:resize={funcHandler} on:scroll={funcHandler} />

<template>
  {#if is_mobile === false}
    <div
      id="container-nav-desktop"
      class="container-nav-desktop"
      transition:fly={{ y: -200, duration: 500 }}
    >
      <div class="sub-container left">
        <a class="button nav" href="/"> Accueil </a>
        <a class="button nav" href="/wedding"> Mariage </a>
        <a class="button nav" href="/events"> Événementiel </a>
        <a class="button nav" href="/pictures"> Photos </a>
      </div>

      {#if is_top}
        <a class="button logo" href="/" in:fly={{ y: -200, duration: 500 }}>
          <img src="/images/logo.png" alt="logo" class="logo" />
        </a>
      {:else}
        <a class="button logo" href="/" in:fly={{ y: -200, duration: 500 }}>
          <img src="/images/logo_bis.png" alt="logo_bis" class="logo" />
        </a>
      {/if}

      <div class="sub-container right">
        <a class="button nav" href="/"> EVJF / EVJG </a>
        <a class="button nav" href="/"> Bridal Shower </a>
        <a class="button nav" href="/"> Baby Shower </a>
        <a class="button nav" href="/"> Contact </a>
      </div>
    </div>
  {:else if is_mobile === true}
    <div
      id="container-nav-mobile"
      class="container-nav-mobile"
      transition:fly={{ y: -200, duration: 500 }}
    >
      <div class="sub-container menu">
        <button class="button menu" on:click={funcSidenav}>
          <img src="/icons/menu.svg" alt="menu" class="menu" />
        </button>

        <a class="button logo" href="/">
          <img src="/images/logo_bis.png" alt="logo_bis" class="logo" />
        </a>
      </div>

      {#if is_sidenav === true}
        <div
          class="container-sidenav"
          transition:fly={{ y: -1000, duration: 500 }}
        >
          <div class="sub-container">
            <a class="button nav" href="/"> Accueil </a>
            <a class="button nav" href="/"> Mariage </a>
            <a class="button nav" href="/"> Événementiel </a>
            <a class="button nav" href="/"> Photos </a>
            <a class="button nav" href="/"> EVJF / EVJG </a>
            <a class="button nav" href="/"> Bridal Shower </a>
            <a class="button nav" href="/"> Baby Shower </a>
            <a class="button nav" href="/"> Contact </a>
          </div>
        </div>
      {/if}
    </div>
  {/if}
</template>

<style scoped>
  .container-nav-desktop {
    position: fixed;
    width: calc(100% - 76px);
    left: 38px;
    padding: 16px 0px;

    display: flex;
    justify-content: space-between;
    z-index: 5;
  }

  .container-nav-desktop .sub-container {
    width: 100%;

    display: flex;
    justify-content: space-around;
    align-items: center;
  }

  .container-nav-desktop .logo {
    width: 160px;
  }

  .container-nav-mobile {
    position: fixed;
    width: 100%;
    height: 82px;
    padding: 0;
    top: 38px;

    display: flex;
    flex-direction: column;
    align-items: center;
    z-index: 5;
  }

  .container-nav-mobile .sub-container.menu {
    width: 100%;

    background-color: var(--color-main);
    z-index: 2;

    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container-nav-mobile .button.menu {
    position: absolute;
    width: 32px;
    left: 2%;
  }

  .container-nav-mobile .button .menu {
    vertical-align: middle;
  }

  .container-nav-mobile .button .logo {
    height: 48px;
  }

  .container-nav-mobile .container-sidenav {
    width: 100%;

    background-color: var(--color-main);
  }

  .container-nav-mobile .container-sidenav .sub-container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .container-nav-mobile .container-sidenav .sub-container .button {
    color: var(--color-second);
    padding: 1% 0;
  }

  .button {
    border: 0;
    margin: 0;
    padding: 0;

    font-family: "Playfair Display", serif;
    font-size: 100%;
    font-weight: 600;

    color: var(--color-main);
    background-color: transparent;

    text-decoration: none;
    line-height: 2em;
  }

  .button.nav:after {
    display: block;
    content: "";

    border-bottom: solid 3px;

    transform: scaleX(0);
    transition: transform 250ms ease-in-out;
  }

  .button.nav:hover:after {
    transform: scaleX(1);
  }
</style>
