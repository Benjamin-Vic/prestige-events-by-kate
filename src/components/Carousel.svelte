<script>
  import { onMount } from "svelte";
  import { fade, fly } from "svelte/transition";

  const arrow = "/src/assets/icons/arrow.svg";

  export let data;
  export let duration;
  export let delay;

  let is_top = true;
  let is_hover = false;
  let index = 0;
  let interval;

  const carouselTopFunc = () => {
    is_top = window.scrollY <= 10 ? true : false;
  };

  const setHover = (event) =>
    (is_hover = event.type === "mouseenter" ? true : false);

  const scaleAnimation = (event) => {
    if (data.length <= 1) return;
    event.srcElement.style["transform"] = "scale(1.1)";
  };

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
    return () => {
      clearInterval(interval);
    };
  });

  document.addEventListener("scroll", carouselTopFunc, false);
</script>

<carousel>
  <div class="carousel-container">
    {#if data.length > 1 && is_hover}
      <button
        on:click={prevIndex}
        class="button-prev"
        transition:fade
        on:mouseenter={setHover}
        on:mouseleave={setHover}
      >
        <img src={arrow} alt="prev" class="arrow-carousel" />
      </button>
      <button
        on:click={nextIndex}
        class="button-next"
        transition:fade
        on:mouseenter={setHover}
        on:mouseleave={setHover}
      >
        <img src={arrow} alt="prev" class="arrow-carousel" />
      </button>
    {/if}
    {#each data as { img }, i}
      {#if index === i}
        <img
          src={img}
          alt={img}
          class="img-carousel"
          transition:fade={{ duration: duration }}
          on:introstart={scaleAnimation}
          on:mouseenter={setHover}
          on:mouseleave={setHover}
        />
      {/if}
    {/each}
    {#if is_top}
      <div class="shadow" on:mouseenter={setHover} on:mouseleave={setHover} />
    {/if}
  </div>
</carousel>

<style scoped>
  .carousel-container {
    position: relative;
    height: 100vh;
    overflow: hidden;
  }

  .button-prev,
  .button-next {
    position: absolute;
    margin: auto;
    z-index: 1;
    top: 50%;

    background-color: transparent;
    padding: 0;
    border: 0;
    z-index: 2;
  }

  .button-prev {
    left: 0;
    transform: rotate(90deg);
  }

  .button-next {
    right: 0;
    transform: rotate(-90deg);
  }

  .arrow-carousel {
    width: 40px;
    filter: invert(99%) sepia(0%) saturate(0%) hue-rotate(17deg)
      brightness(105%) contrast(100%) drop-shadow(0px 0px 8px #000000);
  }

  .arrow-carousel:hover {
    cursor: pointer;
    filter: invert(100%) sepia(9%) saturate(86%) hue-rotate(161deg)
      brightness(113%) contrast(89%) drop-shadow(0px 0px 8px #000000);
  }

  .img-carousel {
    position: absolute;
    width: 100%;
    height: 100vh;
    top: 0;

    object-fit: cover;
    object-position: top;

    transition: transform 4s;
  }

  .shadow {
    position: absolute;
    height: 100vh;
    width: 100%;
    top: 0%;

    box-shadow: 0px 256px 64px -64px rgb(0 0 0 / 25%) inset;
    z-index: 1;
  }

  @media (max-width: 992px) {
    .button-prev,
    .button-next {
      display: none;
    }
  }
</style>
