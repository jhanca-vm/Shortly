<script>
  import Header from './components/Header.svelte';
  import Hero from './components/Hero.svelte';
  import MainContent from './components/MainContent.svelte';

  const focusScroll = () => document.getElementById('texbox').focus({preventScroll:false})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@500;700&display=swap');

  :global(body) {
    font-family: 'Poppins', sans-serif;
    font-weight: 500;
  }
</style>

<Header />
<Hero {focusScroll}/>
<MainContent {focusScroll}/>
