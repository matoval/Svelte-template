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
  if(document.body.clientWidth < 600) {
    isMobile = true;
  } 
  else {
    isMobile = false;
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
        <li><button>Nav1</button></li>
        <li><button>Nav1</button></li>
        <li><button>Nav1</button></li>
        <li><button>Nav1</button></li>
      </ul>
    </div>
    {:else if isMobile}
    <div class="mobile-nav">
      <button class="open-menu" on:click="{toggleMenu}">&#9776</button>
      {#if menu}
        <ul>
          <li><button>Nav1</button></li>
          <li><button>Nav1</button></li>
          <li><button>Nav1</button></li>
          <li><button>Nav1</button></li>
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
    color: var(--light-font);
  }

  .nav {
    margin-right: 25px;
  }

  button {
    border-radius: 5px;
    border: none;
    cursor: pointer;
  }

  .nav li {
    color: var(--light-font);
    list-style: none;
    float: left;
    padding: 5px 15px;
  }

  h1 {
    margin: 0;
  }

  .mobile-nav ul {
    position: fixed;
    padding: 5px;
    right: 10px;
    top: 30px;
    list-style: none;
    display: flex;
    flex-direction: column;
    background-color: var(--primary);
    border-radius: 0 0 5px 5px;
  }

  .mobile-nav li {
    padding: 8px;
    color: var(--light-font);
  }

  .open-menu {
    position: fixed;
    right: 0;
    border: none;
    width: 35px;
    color: var(--light-font);
    background-color: var(--secondary);
    margin: 5px;
  }

  @media only screen and (max-device-width: 600px) {
    
  } 
	
</style>