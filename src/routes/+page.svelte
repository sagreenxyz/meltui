<script>
  import Accordion from '$lib/components/Accordion.svelte'; // Fixed spelling

  // Define the accordion items
  const accordionItems = [
    { id: 'item-1', title: 'Section 1', content: 'This is the content for Section 1.' },
    { id: 'item-2', title: 'Section 2', content: 'This is the content for Section 2.' },
    { id: 'item-3', title: 'Section 3', content: 'This is the content for Section 3.' },
  ];
</script>

<main>
  <h1>Welcome to the Landing Page</h1>
  <p>This is the main content of the landing page.</p>

  <!-- Add the accordion component -->
  <Accordion items={accordionItems} collapsible={true} />
</main>

<style>
  main {
    padding: 2rem;
    font-family: Arial, sans-serif;
  }

  h1 {
    font-size: 2rem;
    margin-bottom: 1rem;
  }

  p {
    margin-bottom: 2rem;
  }
</style>