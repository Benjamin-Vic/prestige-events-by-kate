<script>
  import { onMount } from "svelte";
  import { fade } from "svelte/transition";

  export let data;
  export let duration;
  export let delay;

  let is_hover = false;
  let index = -1;
  let interval;

  const scaleAnimation = (event) => {
    if (data.length <= 1) return;
    event.srcElement.style["transform"] = "scale(1.1)";
  };

  const setHover = (event) => (is_hover = event.type === "mouseenter");

  const nextIndex = () => {
    index = index + 1 < data.length ? index + 1 : 0;
    createInterval();
  };

  const prevIndex = () => {
    index = index - 1 >= 0 ? index - 1 : data.length - 1;
    createInterval();
  };

  const createInterval = () => {
    if (data.length <= 1) return;
    if (interval) clearInterval(interval);
    interval = setInterval(() => {
      nextIndex();
    }, delay);
  };

  onMount(() => {
    createInterval();
    index = 0;
    return () => {
      clearInterval(interval);
    };
  });
</script>

<template>
  <div class="container-carousel">
    {#if data.length > 1 && is_hover}
      <button
        on:click={prevIndex}
        class="button prev"
        transition:fade
        on:mouseenter={setHover}
        on:mouseleave={setHover}
      >
        <img src="/icons/arrow.svg" alt="prev" class="arrow" />
      </button>
      <button
        on:click={nextIndex}
        class="button next"
        transition:fade
        on:mouseenter={setHover}
        on:mouseleave={setHover}
      >
        <img src="/icons/arrow.svg" alt="prev" class="arrow" />
      </button>
    {/if}
    {#each data as { img, alt }, i}
      {#if index === i}
        <img
          src={img}
          {alt}
          class="img"
          transition:fade={{ duration: duration }}
          on:introstart={scaleAnimation}
          on:mouseenter={setHover}
          on:mouseleave={setHover}
        />
      {/if}
    {/each}
  </div>
</template>

<style scoped>
  .container-carousel {
    position: relative;
    height: 95vh;
    overflow: hidden;
  }

  .container-carousel .button {
    position: absolute;
    width: 40px;
    z-index: 2;
    top: 50%;

    border: 0;
    margin: auto;
    padding: 0;

    background-color: transparent;
    cursor: pointer;
  }

  .container-carousel .button.prev {
    left: 0;
    transform: rotate(90deg);
  }

  .container-carousel .button.next {
    right: 0;
    transform: rotate(-90deg);
  }

  .container-carousel .button .arrow {
    filter: invert(99%) sepia(0%) saturate(0%) hue-rotate(17deg)
      brightness(105%) contrast(100%) drop-shadow(0px 0px 8px #000000);
  }

  .container-carousel .button .arrow:hover {
    filter: invert(100%) sepia(9%) saturate(86%) hue-rotate(161deg)
      brightness(113%) contrast(89%) drop-shadow(0px 0px 8px #000000);
  }

  .container-carousel .img {
    position: absolute;
    width: 100%;
    height: 100vh;
    top: 0;

    object-fit: cover;
    object-position: top;

    transition: transform 4s;
  }

  @media (max-width: 992px) {
    .container-carousel .button.prev,
    .container-carousel .button.next {
      display: none;
    }
  }
</style>
