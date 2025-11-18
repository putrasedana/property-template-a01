<script lang="ts">
  import PropertyCard from "../components/PropertyCard.svelte";
  import { properties } from "../data/properties";

  let selectedType = "All";
  let selectedBedrooms = "All";
  let priceRange = "All";

  const types = [
    "All",
    "House",
    "Apartment",
    "Villa",
    "Penthouse",
    "Townhouse",
    "Studio",
    "Estate",
  ];
  const bedroomOptions = ["All", "1", "2", "3", "4", "5+"];
  const priceRanges = [
    { label: "All", min: 0, max: Infinity },
    { label: "Under $500K", min: 0, max: 500000 },
    { label: "$500K - $1M", min: 500000, max: 1000000 },
    { label: "$1M - $2M", min: 1000000, max: 2000000 },
    { label: "$2M - $5M", min: 2000000, max: 5000000 },
    { label: "Over $5M", min: 5000000, max: Infinity },
  ];

  $: filteredProperties = properties.filter((property) => {
    const typeMatch = selectedType === "All" || property.type === selectedType;

    let bedroomMatch = true;
    if (selectedBedrooms !== "All") {
      if (selectedBedrooms === "5+") {
        bedroomMatch = property.bedrooms >= 5;
      } else {
        bedroomMatch = property.bedrooms === parseInt(selectedBedrooms);
      }
    }

    const selectedRange = priceRanges.find((r) => r.label === priceRange);
    const priceMatch = selectedRange
      ? property.price >= selectedRange.min &&
        property.price <= selectedRange.max
      : true;

    return typeMatch && bedroomMatch && priceMatch;
  });
</script>

<div class="min-h-screen bg-gray-50">
  <section class="bg-linear-to-br from-primary-600 to-accent-60 pt-16">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <h1 class="text-4xl md:text-5xl font-bold mb-4">Property Listings</h1>
      <p class="text-xl opacity-90">
        Discover your perfect home from our curated collection
      </p>
    </div>
  </section>

  <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
    <div class="bg-white rounded-xl shadow-md p-6 mb-8">
      <h2 class="text-xl font-bold text-gray-900 mb-4">Filter Properties</h2>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div>
          <label
            for="property-type"
            class="block text-sm font-medium text-gray-700 mb-2"
          >
            Property Type
          </label>
          <select
            id="property-type"
            bind:value={selectedType}
            class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent outline-none"
          >
            {#each types as type}
              <option value={type}>{type}</option>
            {/each}
          </select>
        </div>

        <div>
          <label
            for="bedrooms"
            class="block text-sm font-medium text-gray-700 mb-2"
          >
            Bedrooms
          </label>
          <select
            id="bedrooms"
            bind:value={selectedBedrooms}
            class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent outline-none"
          >
            {#each bedroomOptions as option}
              <option value={option}>{option}</option>
            {/each}
          </select>
        </div>

        <div>
          <label
            for="price-range"
            class="block text-sm font-medium text-gray-700 mb-2"
          >
            Price Range
          </label>
          <select
            id="price-range"
            bind:value={priceRange}
            class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent outline-none"
          >
            {#each priceRanges as range}
              <option value={range.label}>{range.label}</option>
            {/each}
          </select>
        </div>
      </div>

      <div class="mt-4 text-sm text-gray-600">
        Showing <span class="font-semibold text-gray-900"
          >{filteredProperties.length}</span
        >
        {filteredProperties.length === 1 ? "property" : "properties"}
      </div>
    </div>

    {#if filteredProperties.length > 0}
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        {#each filteredProperties as property}
          <PropertyCard {property} />
        {/each}
      </div>
    {:else}
      <div class="text-center py-16">
        <svg
          class="w-24 h-24 text-gray-300 mx-auto mb-4"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"
          />
        </svg>
        <h3 class="text-2xl font-bold text-gray-900 mb-2">
          No properties found
        </h3>
        <p class="text-gray-600">
          Try adjusting your filters to see more results
        </p>
      </div>
    {/if}
  </section>
</div>
