<script>
  import Slider from "./components/slider/Slider.svelte";
</script>

<main>
  <div class="border border-head">
    <span class="border-head-text">
      Kate, Lieu-dit Le Mas Blanc 66200 ALENYA
    </span>

    <span class="border-head-text"> Téléphone : 06 89 71 52 21 </span>
  </div>

  <div class="border border-left" />
  <div class="border border-right" />
  <div class="border border-foot" />

  <Slider />

  <span>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis et nulla id
    tellus tincidunt tempus in et lectus. Sed hendrerit metus quam. Donec
    tempor, nulla sed scelerisque eleifend, diam eros elementum tortor, nec
    venenatis nibh justo ut metus. Donec non turpis id lorem sagittis fringilla
    porttitor id lectus. Curabitur ornare placerat mauris, in venenatis justo.
    Phasellus volutpat sollicitudin risus ornare pellentesque. Mauris laoreet
    nulla sit amet scelerisque viverra. Integer orci lacus, sollicitudin vel
    imperdiet vel, lacinia nec ligula. Nulla vel velit id mauris fermentum
    sodales imperdiet at tortor. Sed ornare leo eu est accumsan porta. Sed a
    arcu id tellus commodo dignissim. Phasellus at quam molestie, ullamcorper
    dolor vitae, imperdiet ligula. Curabitur commodo est vel semper varius.
    Morbi nibh metus, luctus et suscipit a, tempus a mauris. Aenean velit nisi,
    lobortis sit amet ante in, venenatis vestibulum dui. Nulla facilisi.
    Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere
    cubilia curae; Maecenas maximus pellentesque ligula quis gravida. Phasellus
    maximus arcu vel lectus mollis pellentesque. Maecenas tincidunt eu nisl eget
    dictum. Donec non diam volutpat, laoreet velit et, malesuada lorem.
    Phasellus vulputate libero velit, ac efficitur magna elementum at.
    Vestibulum eros leo, accumsan eget rutrum nec, fermentum eu metus. Aenean
    mauris velit, faucibus eu elit a, egestas vestibulum tellus. Vivamus
    placerat nibh in erat pulvinar varius. In quis hendrerit urna. Proin
    ultricies tortor eu tortor sagittis hendrerit. Praesent faucibus urna ac
    condimentum rutrum. Ut lobortis lorem eget lectus consectetur, ac blandit
    tellus tempus. Morbi id aliquet orci, eget consectetur nunc. Vivamus euismod
    odio ut lectus tempus pretium. Phasellus id ex eget odio lobortis gravida.
    Integer ultricies vitae lacus eu pulvinar. Donec efficitur blandit dolor sed
    sagittis. Aliquam dui magna, maximus ut lectus a, interdum tincidunt enim.
    Nam urna sem, venenatis ut ex malesuada, posuere ultricies ligula. Quisque
    nunc tellus, imperdiet scelerisque tristique aliquet, tristique et nisi. Nam
    faucibus lacinia ligula, quis elementum tortor feugiat eget. Nam velit
    augue, pharetra a leo ac, porta sodales ex. Fusce cursus pulvinar elit
    vulputate pretium. Fusce quis risus a sapien laoreet pulvinar ut at sem.
    Curabitur sodales, lorem mattis dapibus vulputate, nisl mauris fermentum
    enim, vitae finibus justo sapien scelerisque mauris. Integer non tellus
    consequat, cursus augue id, cursus velit.
  </span>
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Roboto+Slab&display=swap");

  main {
    width: calc(100% - 64px);
    height: 100vh;

    border: 32px solid white;
  }

  .border-head-text {
    font-family: "Roboto Slab", serif;
    font-size: small;
    padding: 0 32px;
  }

  .border {
    background-color: rgb(204, 144, 144);
  }

  .border-head,
  .border-foot {
    width: 100%;
    height: 32px;
    z-index: 2;
  }

  .border-left,
  .border-right {
    width: 32px;
    height: 100%;
    z-index: 1;
  }

  .border-head {
    position: fixed;
    top: 0;
    left: 0;

    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .border-left {
    position: fixed;
    top: 0;
    left: 0;
  }

  .border-right {
    position: fixed;
    top: 0;
    right: 0;
  }

  .border-foot {
    position: fixed;
    bottom: 0;
    left: 0;
  }
</style>
