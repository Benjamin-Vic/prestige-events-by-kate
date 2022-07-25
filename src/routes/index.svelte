<script>
  import Carousel from "../components/Carousel.svelte";

  const carousel = [
    { img: "/images/carousel/carousel_1.png", alt: "carousel_1" },
    { img: "/images/carousel/carousel_2.jpg", alt: "carousel_2" },
    { img: "/images/carousel/carousel_3.png", alt: "carousel_3" },
    { img: "/images/carousel/carousel_4.jpg", alt: "carousel_4" },
    { img: "/images/carousel/carousel_5.jpg", alt: "carousel_5" },
  ];
</script>

<svelte:head>
  <title>Wedding Planner - Prestige Events by Kate</title>
</svelte:head>

<template>
  <Carousel data={carousel} duration={1000} delay={5000} />

  <div class="container-body">Salut</div>
</template>

<style scoped>
  .container-body {
    border: 1px solid red;
    margin: 0 15%;
  }

  @media (max-width: 992px) {
    .container-body {
      margin: 0 10%;
    }
  }

  @media (max-width: 768px) {
    .container-body {
      margin: 0 5%;
    }
  }

  @media (max-width: 576px) {
    .container-body {
      margin: 0 1%;
    }
  }
</style>
