<script>
  export let items = [];
  export let collapsible = false;

  console.log('Accordion items:', items); // Debugging log

  let openItem = collapsible ? null : items[0]?.id;

  function toggleItem(id) {
    openItem = collapsible && openItem === id ? null : id;
  }
</script>

<div class="accordion">
  {#if items.length === 0}
    <p>No items to display.</p> <!-- Fallback message -->
  {:else}
    {#each items as { id, title, content }}
      <div class="accordion-item">
        <button class="accordion-header" on:click={() => toggleItem(id)}>
          {title}
        </button>
        {#if openItem === id}
          <div class="accordion-content">
            {content}
          </div>
        {/if}
      </div>
    {/each}
  {/if}
</div>

<style>
  .accordion {
    border: 1px solid #ccc;
    border-radius: 4px;
  }

  .accordion-item {
    border-bottom: 1px solid #ccc;
  }

  .accordion-item:last-child {
    border-bottom: none;
  }

  .accordion-header {
    background: #f9f9f9;
    border: none;
    padding: 1rem;
    width: 100%;
    text-align: left;
    cursor: pointer;
    font-size: 1rem;
  }

  .accordion-content {
    padding: 1rem;
    background: #fff;
  }
</style>
