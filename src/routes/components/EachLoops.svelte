<script>
    let items = [
      { id: 1, name: 'Item 1' },
      { id: 2, name: 'Item 2' },
      { id: 3, name: 'Item 3' }
    ];
  </script>
  
  <ul>
    {#each items as item}
      <li>{item.name}</li>
    {/each}
  </ul>