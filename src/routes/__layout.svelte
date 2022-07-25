<script>
  import Navigation from "../components/Navigation.svelte";
</script>

<template>
  <div id="container" class="container">
    <div class="border top">
      <span class="text left">
        <img src="/ornaments/top.svg" alt="line" class="img" />
        Kate, Lieu-dit Le Mas Blanc, 66200 ALENYA
      </span>

      <span class="text right">
        <img src="/ornaments/top.svg" alt="line" class="img" />
        Téléphone :
        <a href="tel:+33689715221" class="text-mobile">06.89.71.52.21</a>
      </span>
    </div>

    <div class="border left" />
    <div class="border right" />
    <div class="border bottom" />

    <Navigation />

    <slot />
  </div>
</template>

<style scoped>
  .container {
    border: 38px solid var(--color-main);

    background-color: var(--color-blush);
    background-image: url("/images/background.svg");
    background-repeat: repeat;
    background-size: 256px;

    /* TEMP */
    /* background-color: black; */
    height: 200vh;
    /* TEMP */

    --color-main: #ffffff;
    --color-second: #36393b;
    --color-blush: #faefef;
    --color-green: #b8e2c8;
  }

  .border {
    position: fixed;
    background-color: var(--color-main);
  }

  .border.top,
  .border.bottom {
    width: 100%;
    height: 38px;
    z-index: 11;
  }

  .border.left,
  .border.right {
    width: 38px;
    height: 100%;
    z-index: 10;
  }

  .border.top {
    top: 0;
    left: 0;

    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .border.left {
    top: 0;
    left: 0;
  }

  .border.right {
    top: 0;
    right: 0;
  }

  .border.bottom {
    bottom: 0;
    left: 0;
  }

  .text {
    font-family: "Roboto Slab", serif;
    font-size: small;
    padding: 0 38px;
  }

  .text.left {
    text-align: left;
  }

  .text.right {
    text-align: right;
  }

  .text-mobile {
    color: var(--color-second);
    text-decoration: none;
    cursor: default;
  }

  .img {
    width: 16px;
    vertical-align: middle;
  }

  @media (max-width: 992px) {
    .border.left,
    .border.right,
    .border.bottom {
      display: none;
    }

    .container {
      border-left: none;
      border-right: none;
      border-bottom: none;
    }

    .text {
      padding: 0 8px;
    }
  }
</style>
