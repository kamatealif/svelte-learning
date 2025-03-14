<script>
    export let logo = "Logo";
    export let links = [
      { name: "Home", href: "/" },
      { name: "About", href: "/about" },
      { name: "Services", href: "/services" },
      { name: "Contact", href: "/contact" }
    ];
  </script>
  
  <header class="header">
    <div class="logo">
      {#if typeof logo === 'string'}
        <span>{logo}</span>
      {:else}
        {logo}
      {/if}
    </div>
  
    <nav class="navbar">
      {#each links as { name, href }}
        <a href={href} class="nav-link">{name}</a>
      {/each}
    </nav>
  </header>
  
  <style>
    .header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem 2rem;
      background-color: #333;
      color: #fff;
      
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
  
    .logo {
      font-size: 1.5rem;
      font-weight: bold;
    }
  
    .navbar {
      display: flex;
      gap: 1.5rem;
    }
  
    .nav-link {
      text-decoration: none;
      color: #fff;
      font-family: Verdana, Geneva, Tahoma, sans-serif;
      font-weight: 500;
      transition: color 0.3s ease;
    }
  
    .nav-link:hover {
      color: #4CAF50; /* Highlight color */
    }
  </style>
  