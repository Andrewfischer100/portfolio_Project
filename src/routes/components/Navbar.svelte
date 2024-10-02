<script>
    let navLinks = [
      { name: "Home", href: "/" },
      { name: "About Me", href: "about" },
      { name: "Portfolio", href: "portfolio" },
      { name: "Contact", href: "contact" }
    ];
  </script>
  
  <nav class="navbar">
    <ul>
      {#each navLinks as link}
        <li><a href={link.href}>{link.name}</a></li>
      {/each}
    </ul>
  </nav>
  
  <style>
    .navbar {
      background-color: #d4d4d4;
      padding: 1rem;
      position: fixed;
      top: 0;
      width: 100%;
      display: flex;
      justify-content: center;
      z-index: 1000;
    }
    ul {
      list-style: none;
      display: flex;
      gap: 2rem;
    }
    li a {
      color: rgb(85, 85, 85);
      text-decoration: none;
    }
  </style>
  