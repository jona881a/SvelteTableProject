<script>
  export let keys;
</script>

<thead>
  {#each keys as key}
  <th>{key}</th>
  {/each}
</thead>

<style>
  thead {
    background-color: #ff3e00;
    color: #ffffff;
    text-align: left;
    font-weight: bold;
  }

  th {
    padding: 12px 15px;
  }
</style>