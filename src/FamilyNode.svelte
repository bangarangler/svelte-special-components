<script context="module">
  console.log('runs once!')

  let deactivateNode;
</script>

<script>
  console.log('runs multiple times')

  function deactivate() {
    isActive = false;
  }
  export let member;

  let isActive;

  function activate() {
    if (deactivateNode) {
      deactivateNode()
    }
    isActive = true;
    deactivateNode = deactivate;
  }
</script>

<style>
  div {
    margin-left: 2rem;
  }

  .active {
    color: red;
  }
</style>

<div on:click={activate} class:active={isActive}>
  <h1>{member.name}</h1>
  {#if member.isParent}
    {#each member.children as child}
      <svelte:self member={child} />
    {/each}
  {/if}
</div>

