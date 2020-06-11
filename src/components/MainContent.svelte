<script>
  import Description from './Description.svelte';

  export let focusScroll;

  let urls = [];
  let alert = false;

  const API = 'https://rel.ink/api/links/';

  async function getShortUrl() {
    alert = false;

    let url = document.shortener.link.value;
    let data = { url: `${url}` };

    const response = await fetch(API, {
      method: 'POST',
      body: JSON.stringify(data),
      headers: { 'Content-Type': 'application/json' }
    });

    const result = await response.json();

    urls = urls.concat(result);
  };

  function showAlert() { alert = true };

  function copyUrl(id) {
    let element = document.getElementById(`${id}`);
    let selection = document.createRange();

    selection.selectNodeContents(element);

    window.getSelection().removeAllRanges();
    window.getSelection().addRange(selection);

    let copied = document.execCommand('copy');

    window.getSelection().removeRange(selection);
  }

  function success(id) {
    let btn = document.getElementById(`${id}`);

    btn.lastChild.nodeValue = 'Copied!';
    btn.classList.add('bg-violet')
  }
</script>

<style>
  form {
    background-image: url("/images/bg-shorten-mobile.svg");
  }
  form input:focus {
    outline-color: rgb(245, 101, 101);
  }
  form input:focus::placeholder {
    color: rgb(245, 101, 101);
    opacity: .5;
  }

  .input {
    width: 88.89%;
  }

  .boost {
    background-image: url("/images/bg-boost-mobile.svg");
  }

  @media screen and (min-width: 768px) {
    form {
      background-image: url("/images/bg-shorten-desktop.svg");
    }

    .boost {
      background-image: url("/images/bg-boost-desktop.svg");
    }

    button {
      width: 200px;
    }

    .btn-copy {
      width: 100px;
      height: 35px;
    }
  }
</style>

<section class="w-full bg-grey-100 px-5 md:px-8 lg:px-10 text-grey-200 bg-opacity-25 mt-40 lg:px-20">
  <div class="input container mx-auto -mt-20 absolute inset-x-0">
    <form name="shortener" onsubmit="return false" on:submit={getShortUrl} class="bg-no-repeat md:bg-cover bg-violet md:flex rounded-lg p-6 bg-right-top md:p-12 md:mb-6">
      <div class="w-full md:mr-5 box-border">
        <input name="link" id="texbox" class="rounded-md w-full box-border p-3" type="url" placeholder="Shorten a link here..." required on:invalid={showAlert}>
        {#if alert == true}
          <p class="mt-1 text-red-500 md:absolute md:mt-2"><i>Please add a link</i></p>
        {/if}
      </div>
      <button class="main-btn py-3 mt-4 w-full hover:bg-teal-300 focus:outline-none md:mt-0 md:w-auto">Shorten It!</button>
    </form>
  </div>
  {#if urls.length !== 0}
    <div class="pt-24 -mb-24 md:pt-20 md:-mb-16 container mx-auto sm:px-2 md:px-0">
      {#each urls as { url, hashid }, i}
        <div class="mt-6 py-4 bg-white divide-y divide-grey-100 divide-opacity-75 rounded-md md:flex md:divide-y-0 md:items-center md:justify-between md:px-6 md:py-4 md:mt-4">
          <p class="text-grey-400 px-4 pb-2 md:p-0 truncate">{url}</p>
          <div class="px-4 md:flex md:p-0 md:items-center">
            <p id={hashid} class="text-cyan pb-2 pt-3 md:p-0 md:mx-5">https://rel.ink/{hashid}</p>
            <button id={i} on:click={copyUrl(hashid), success(i)} class="btn-copy hover:bg-teal-300 font-medium md:text-sm main-btn w-full md:p-0 focus:outline-none">Copy</button>
          </div>
        </div>
      {/each}
    </div>
  {/if}
  <Description />
  <div class="boost mt-20 -mx-5 py-16 text-center bg-violet bg-no-repeat bg-cover bg-center lg:-mx-20 xl:mt-32">
    <h2 class="text-white font-bold text-2xl sm:text-3xl lg:text-4xl">Boost your links today</h2>
    <button on:click={focusScroll} class="mt-4 btn hover:bg-teal-300 focus:outline-none md:text-xl lg:text-lg lg:z-20">Get Started</button>
  </div>
</section>