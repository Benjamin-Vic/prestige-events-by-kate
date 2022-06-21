<script>
  import slider1 from "../../assets/slider/slider_1.png";
  import slider2 from "../../assets/slider/slider_2.jpg";
  import slider3 from "../../assets/slider/slider_3.png";
  import slider4 from "../../assets/slider/slider_4.jpg";

  import caretUp from "../../assets/icons/caret-up.svg";

  const imgs = [slider1, slider2, slider3, slider4];

  let index = 3;

  const set_index = (i) => {
    index = i;
  };

</script>

<main>
  <!-- <div class="slider-container"> -->

  <img class="imgs" src={imgs[index]} alt="Image Slider {index + 1}"/>

  <img src={caretUp} alt="Caret Up"/>



  <!-- <img src={logo} alt="Svelte Logo" /> -->

  <!-- </div> -->
</main>

<style>
  main {
    width: 100%;
    height: 100vh;

    background-color: aquamarine;
  }

  .imgs {
    width: 100%;
    height: 100vh;
    object-fit: cover;
    object-position: top;
  }
</style>
