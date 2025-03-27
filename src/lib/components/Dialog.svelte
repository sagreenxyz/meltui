<script>
  export let open = false;
  export let title = '';
  export let content = '';
  export let onClose = () => {};

  function closeDialog() {
    open = false;
    onClose();
  }
</script>

{#if open}
  <div class="dialog-backdrop" on:click={closeDialog}>
    <div class="dialog" on:click|stopPropagation>
      <header class="dialog-header">
        <h2>{title}</h2>
        <button class="dialog-close" on:click={closeDialog} aria-label="Close dialog">✖</button>
      </header>
      <div class="dialog-content">
        {content}
      </div>
      <footer class="dialog-footer">
        <slot name="footer"></slot>
      </footer>
    </div>
  </div>
{/if}

<style>
  .dialog-backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
  }

  .dialog {
    background: white;
    border-radius: 8px;
    max-width: 500px;
    width: 90%;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
  }

  .dialog-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    border-bottom: 1px solid #ccc;
  }

  .dialog-close {
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
  }

  .dialog-content {
    padding: 1rem;
  }

  .dialog-footer {
    padding: 1rem;
    border-top: 1px solid #ccc;
    text-align: right;
  }
</style>
