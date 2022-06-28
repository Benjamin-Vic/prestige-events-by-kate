<script>
  import Carousel from "../components/Carousel.svelte";

  const data = [{ img: "/src/assets/carousel/carousel_1.png" }];
</script>

<body>
  <Carousel {data} duration={0} delay={5000}/>
</body>

<style>
</style>
