<script lang="ts">
  import { currentPage } from '../stores/navigation';

  let mobileMenuOpen = false;

  const navItems = [
    { id: 'home', label: 'Home' },
    { id: 'listings', label: 'Listings' },
    { id: 'about', label: 'About' },
    { id: 'contact', label: 'Contact' }
  ];

  function navigate(page: string) {
    currentPage.set(page);
    mobileMenuOpen = false;
  }
</script>

<nav class="bg-white shadow-md sticky top-0 z-50">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex justify-between items-center h-20">
<button
  type="button"
  on:click={() => navigate('home')}
  class="shrink-0 cursor-pointer focus:outline-none"
>
  <div class="flex items-center gap-2">
    <svg class="w-10 h-10 text-primary-600" fill="currentColor" viewBox="0 0 24 24">
      <path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/>
    </svg>
    <span class="text-2xl font-bold text-gray-900">
      Premium<span class="text-primary-600">Realty</span>
    </span>
  </div>
</button>
      <div class="hidden md:flex items-center gap-8">
        {#each navItems as item}
          <button
            on:click={() => navigate(item.id)}
            class="text-gray-700 cursor-pointer hover:text-primary-600 font-medium transition-colors duration-200 {$currentPage === item.id ? 'text-primary-600 border-b-2 border-primary-600 pb-1' : ''}"
          >
            {item.label}
          </button>
        {/each}
      </div>

      <div class="md:hidden">
        <button
          on:click={() => mobileMenuOpen = !mobileMenuOpen}
          class="text-gray-700 hover:text-primary-600 focus:outline-none"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            {#if mobileMenuOpen}
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            {:else}
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            {/if}
          </svg>
        </button>
      </div>
    </div>
  </div>

  {#if mobileMenuOpen}
    <div class="md:hidden bg-white border-t border-gray-200">
      <div class="px-4 py-4 space-y-3">
        {#each navItems as item}
          <button
            on:click={() => navigate(item.id)}
            class="block w-full text-left px-4 py-2 text-gray-700 hover:bg-primary-50 hover:text-primary-600 rounded-lg font-medium transition-colors {$currentPage === item.id ? 'bg-primary-50 text-primary-600' : ''}"
          >
            {item.label}
          </button>
        {/each}
      </div>
    </div>
  {/if}
</nav>
