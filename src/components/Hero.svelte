<script>
  export let focusScroll;
</script>

<style>
  figure, img {
    height: 87vw;
  }

  @media screen and (min-width: 1024px) {
    figure, img {
      height: 36vw;
    }

    img {
      padding-left: 54%;
    }
    
    .btn {
      width: fit-content;
    }
  }

  @media screen and (min-width: 1066px) {
    section {
      padding: 0;
      margin-left: auto;
      margin-right: auto;
    }
  }

  @media screen and (min-width: 1280px) {
    section {
      padding-left: 1.25rem;
      margin-left: 0;
      margin-right: 0;
    }
  }
  
  @media screen and (min-width: 1320px) {
    section {
      padding: 0;
      margin-left: auto;
      margin-right: auto;
    }
  }
</style>

<section class="container mx-auto px-5 text-grey-200 sm:mt-5 lg:flex lg:mt-10 lg:mx-0 xl:px-5">
  <figure class="h-64 w-full lg:w-1/2">
    <img class="absolute inset-x-0 pl-5 object-cover object-left -mt-2 lg:pl-0" src="images/illustration-working.svg" alt="illustration">
  </figure>
  <div class="pt-5 text-center lg:pt-0 lg:pr-5 lg:pb-24 lg:w-1/2 lg:order-first lg:text-left lg:flex lg:flex-col lg:justify-center">
    <h1 class="font-bold leading-tight text-4xl text-grey-300 md:text-5xl lg:6xl">More than just shorter links</h1>
    <p class="mt-4 leading-relaxed md:text-2xl lg:text-xl lg:mt-1">Build your brand’s recognition and get detailed insights on how your links are performing.</p>
    <button on:click={focusScroll()} class="mt-6 btn focus:outline-none md:text-2xl sm:px-10 lg:text-lg lg:z-20">Get Started</button>
  </div>
</section>
