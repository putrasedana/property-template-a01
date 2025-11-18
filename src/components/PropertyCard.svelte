<script lang="ts">
  import { currentPage, selectedPropertyId } from "../stores/navigation";
  import { MapPin, Bed, Bath, Ruler, Star } from "lucide-svelte";

  export let property: {
    id: any;
    title: string;
    price: number;
    type: string;
    featured?: boolean;
    location: string;
    bedrooms: number;
    bathrooms: number;
    area: number;
    images?: string[];
  };

  function viewDetails() {
    selectedPropertyId.set(property.id);
    currentPage.set("details");
  }

  function formatPrice(price: number): string {
    return new Intl.NumberFormat("en-US", {
      style: "currency",
      currency: "USD",
      minimumFractionDigits: 0,
      maximumFractionDigits: 0,
    }).format(price);
  }
</script>

<div
  class="bg-white rounded-xl shadow-md overflow-hidden hover:shadow-xl transition-shadow duration-300 group flex flex-col h-full"
>
  <div class="relative overflow-hidden h-64">
    <img
      src={property.images?.[0] ?? "/placeholder.jpg"}
      alt={property.title}
      class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
    />

    {#if property.featured}
      <div
        class="absolute top-4 left-4 bg-white text-black px-3 py-1 rounded-full text-sm font-medium flex items-center gap-1"
      >
        <Star class="w-4 h-4 fill-amber-200" />
        Featured
      </div>
    {/if}

    <div
      class="absolute top-4 right-4 bg-white/90 backdrop-blur-sm px-3 py-1 rounded-full text-sm font-medium text-gray-900"
    >
      {property.type}
    </div>
  </div>

  <div class="p-6 flex flex-col grow">
    <div class="flex items-start justify-between mb-3">
      <h3 class="text-xl font-bold text-gray-900">{property.title}</h3>
      <span class="text-2xl font-bold text-primary-600"
        >{formatPrice(property.price)}</span
      >
    </div>

    <div class="flex items-center gap-2 text-gray-600 mb-4">
      <MapPin class="w-5 h-5 text-primary-600 shrink-0" />
      <span class="text-sm truncate">{property.location}</span>
    </div>

    <div
      class="flex items-center justify-between pb-4 mb-4 border-b border-gray-200"
    >
      <div class="flex items-center gap-2">
        <Bed class="w-5 h-5 text-gray-500 shrink-0" />
        <span class="text-sm text-gray-700 whitespace-nowrap"
          >{property.bedrooms} Beds</span
        >
      </div>

      <div class="flex items-center gap-2">
        <Bath class="w-5 h-5 text-gray-500 shrink-0" />
        <span class="text-sm text-gray-700 whitespace-nowrap"
          >{property.bathrooms} Baths</span
        >
      </div>

      <div class="flex items-center gap-2">
        <Ruler class="w-5 h-5 text-gray-500 shrink-0" />
        <span class="text-sm text-gray-700 whitespace-nowrap"
          >{property.area} sqft</span
        >
      </div>
    </div>

    <div class="mt-auto pt-4">
      <button on:click={viewDetails} class="w-full cursor-pointer btn-primary">
        View Details
      </button>
    </div>
  </div>
</div>
