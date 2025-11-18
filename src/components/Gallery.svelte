<script lang="ts">
  import { ChevronLeft, ChevronRight } from "lucide-svelte";
  export let images: string[] = [];

  let currentImageIndex = 0;

  function nextImage() {
    currentImageIndex = (currentImageIndex + 1) % images.length;
  }

  function prevImage() {
    currentImageIndex = (currentImageIndex - 1 + images.length) % images.length;
  }

  function selectImage(index: number) {
    currentImageIndex = index;
  }
</script>

<div class="space-y-4">
  <div class="relative aspect-video overflow-hidden rounded-t-xl bg-gray-100">
    <img
      src={images[currentImageIndex]}
      alt="Property"
      class="w-full h-full object-cover"
    />

    {#if images.length > 1}
      <!-- Previous Button - Hidden on mobile -->
      <button
        on:click={prevImage}
        class="absolute cursor-pointer left-4 top-1/2 -translate-y-1/2 bg-white/90 backdrop-blur-sm hover:bg-white p-3 rounded-full shadow-lg transition-all hidden sm:block"
      >
        <ChevronLeft class="w-6 h-6 text-gray-900" />
      </button>

      <!-- Next Button - Hidden on mobile -->
      <button
        on:click={nextImage}
        class="absolute cursor-pointer right-4 top-1/2 -translate-y-1/2 bg-white/90 backdrop-blur-sm hover:bg-white p-3 rounded-full shadow-lg transition-all hidden sm:block"
      >
        <ChevronRight class="w-6 h-6 text-gray-900" />
      </button>

      <!-- Image Counter - Hidden on mobile -->
      <div
        class="absolute bottom-4 left-1/2 -translate-x-1/2 bg-black/50 backdrop-blur-sm text-white px-4 py-2 rounded-full text-sm hidden sm:block"
      >
        {currentImageIndex + 1} / {images.length}
      </div>
    {/if}
  </div>

  {#if images.length > 1}
    <div class="grid grid-cols-4 sm:grid-cols-8 gap-4 px-4 pb-4">
      {#each images as image, index}
        <button
          on:click={() => selectImage(index)}
          class="aspect-video cursor-pointer overflow-hidden rounded-lg {currentImageIndex ===
          index
            ? 'ring-4 ring-primary-600'
            : 'opacity-70 hover:opacity-100'} transition-all"
        >
          <img
            src={image}
            alt="Thumbnail {index + 1}"
            class="w-full h-full object-cover"
          />
        </button>
      {/each}
    </div>
  {/if}
</div>
