<script>
  let menu = { hide: true };

  function showHide() {
    ( menu.hide == true ) 
      ? document.getElementById('menu').classList.remove('invisible')
      : document.getElementById('menu').classList.add('invisible')

    menu.hide = !menu.hide;
  };
</script>

<header class="p-5">
  <nav class="flex justify-between container mx-auto sm:items-center">
    <figure class="sm:mr-6 md:mr-8 lg:mr-12">
      <img src="images/logo.svg" alt="logo">
    </figure>
    <div id="menu" class="w-11/12 absolute z-10 inset-x-0 divide-y divide-grey-200 divide-opacity-25 mx-auto mt-12 px-5 py-10 rounded-lg bg-violet text-white invisible sm:visible sm:static sm:mt-0 sm:p-0 sm:bg-transparent sm:flex sm:justify-between sm:divide-y-0 sm:text-grey-200 sm:mx-0 sm:w-full">
      <ul class="text-center sm:font-bold sm:flex sm:items-center">
        <li class="mb-6 sm:mb-0 sm:hover:text-grey-300 sm:cursor-pointer">Features</li>
        <li class="mb-6 sm:mb-0 sm:ml-4 sm:hover:text-grey-300 sm:cursor-pointer md:ml-6 lg:ml-8">Pricing</li>
        <li class="mb-6 sm:mb-0 sm:ml-4 sm:hover:text-grey-300 sm:cursor-pointer md:ml-6 lg:ml-8">Resources</li>
      </ul>
      <div class="flex flex-col sm:flex-row">
        <button class="mt-6 focus:outline-none sm:font-bold sm:mt-0 sm:mr-5 lg:mr-6">Login</button>
        <button class="mt-6 py-2 rounded-full bg-cyan focus:outline-none sm:mt-0 sm:font-bold sm:text-white sm:px-5">Sign Up</button>
      </div>
    </div>
    <span on:click={showHide} class="text-4xl -mt-3 text-grey-200 cursor-pointer sm:hidden">&equiv;</span>
  </nav>
</header>