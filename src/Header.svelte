<script>
import { onMount } from 'svelte';
let menu = false;
let isMobile = false;

function toggleMenu() {
  menu = !menu;
}

onMount(() => {
  resizing();
})

function resizing() {
  console.log(document.body.clientWidth);
  if(document.body.clientWidth < 600) {
    isMobile = true;
    console.log(isMobile);
  } 
  else {
    isMobile = false;
    console.log(isMobile);
  }
}

window.addEventListener("resize", resizing);

</script>

<main on:resize="{resizing}">
  <div class="topbar">
    <div class="logo">
      <h1>LOGO</h1>
    </div>
    {#if !isMobile}
    <div class="nav">
      <ul>
        <li on:click="">Nav1</li>
        <li on:click="">Nav1</li>
        <li on:click="">Nav1</li>
        <li on:click="">Nav1</li>
      </ul>
    </div>
    {:else if isMobile}
    <div class="mobile-nav">
      <button class="open-menu" on:click="{toggleMenu}">&#9776</button>
      {#if menu}
        <ul>
          <li on:click="">Nav1</li>
          <li on:click="">Nav1</li>
          <li on:click="">Nav1</li>
          <li on:click="">Nav1</li>
        </ul>
      {/if}
    </div>
    {/if}
  </div>
	
</main>

<style>
  .topbar {
    width: 100vw;
    background-color: var(--primary);
    position: fixed;
    top: 0;
    display: flex;
    justify-content: space-between;
  }

  .logo {
    padding: 5px;
    margin-left: 20px;

  }

  .nav {
    margin-right: 25px;
  }

  .nav li {
    list-style: none;
    float: left;
    padding: 5px 15px;
  }

  h1 {
    margin: 0;
  }

  .mobile-nav {
    position: fixed;
    right: 0;
    background-color: var(--primary);
    display: flex;
    flex-direction: column;
    border-radius: 5px;
    margin: 5px;
  }

  .mobile-nav li {
    list-style: none;
  }

  .open-menu {
    border: none;
    width: 35px;
    background-color: var(--secondary);
    margin: 5px;
  }

  @media only screen and (max-device-width: 600px) {
    .nav {
      display: none;
    }

    .mobile-nav {
    display: flex;
    }
  } 
	
</style>