<script lang="ts">
  import { selectedPropertyId, currentPage } from "../stores/navigation";
  import Gallery from "../components/Gallery.svelte";
  import { properties } from "../data/properties";
  import {
    ArrowLeft,
    MapPin,
    Bed,
    Bath,
    Ruler,
    Calendar,
    Check,
    Phone,
    Mail,
    User,
  } from "lucide-svelte";

  $: property = properties.find((p) => p.id === $selectedPropertyId);

  function goBack() {
    currentPage.set("listings");
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

{#if property}
  <div class="min-h-screen bg-gray-50">
    <section class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <div class="max-w-7xl mx-auto pb-6">
        <button
          on:click={goBack}
          class="flex items-center gap-2 text-primary-600 cursor-pointer hover:text-primary-700 font-medium mb-4"
        >
          <ArrowLeft class="w-5 h-5" />
          Back to Listings
        </button>
      </div>

      <!-- Gallery Section - Full Width -->
      <div class="bg-white rounded-xl shadow-md overflow-hidden mb-8">
        <Gallery images={property.images} />
      </div>

      <!-- Property Details Section - Full Width -->
      <div class="bg-white rounded-xl shadow-md p-8 mb-8">
        <div class="flex flex-wrap items-start justify-between gap-4 mb-6">
          <div>
            <h1 class="text-3xl md:text-4xl font-bold text-gray-900 mb-2">
              {property.title}
            </h1>
            <div class="flex items-center gap-2 text-gray-600">
              <MapPin class="w-5 h-5 text-primary-600" />
              <span>{property.location}</span>
            </div>
          </div>
          <div class="text-right">
            <div class="text-3xl md:text-4xl font-bold text-primary-600">
              {formatPrice(property.price)}
            </div>
            <div
              class="inline-block mt-2 px-4 py-2 bg-green-100 text-green-800 rounded-full text-sm font-medium"
            >
              {property.status}
            </div>
          </div>
        </div>

        <div
          class="grid grid-cols-2 md:grid-cols-4 gap-6 py-6 border-y border-gray-200"
        >
          <div class="text-center">
            <div
              class="w-12 h-12 bg-primary-100 rounded-full flex items-center justify-center mx-auto mb-2"
            >
              <Bed class="w-6 h-6 text-primary-600" />
            </div>
            <div class="text-2xl font-bold text-gray-900">
              {property.bedrooms}
            </div>
            <div class="text-sm text-gray-600">Bedrooms</div>
          </div>

          <div class="text-center">
            <div
              class="w-12 h-12 bg-accent-100 rounded-full flex items-center justify-center mx-auto mb-2"
            >
              <Bath class="w-6 h-6 text-accent-600" />
            </div>
            <div class="text-2xl font-bold text-gray-900">
              {property.bathrooms}
            </div>
            <div class="text-sm text-gray-600">Bathrooms</div>
          </div>

          <div class="text-center">
            <div
              class="w-12 h-12 bg-primary-100 rounded-full flex items-center justify-center mx-auto mb-2"
            >
              <Ruler class="w-6 h-6 text-primary-600" />
            </div>
            <div class="text-2xl font-bold text-gray-900">
              {property.area.toLocaleString()}
            </div>
            <div class="text-sm text-gray-600">Sq Ft</div>
          </div>

          <div class="text-center">
            <div
              class="w-12 h-12 bg-accent-100 rounded-full flex items-center justify-center mx-auto mb-2"
            >
              <Calendar class="w-6 h-6 text-accent-600" />
            </div>
            <div class="text-2xl font-bold text-gray-900">
              {property.yearBuilt}
            </div>
            <div class="text-sm text-gray-600">Year Built</div>
          </div>
        </div>

        <div class="mt-8">
          <h2 class="text-2xl font-bold text-gray-900 mb-4">Description</h2>
          <p class="text-gray-700 leading-relaxed">
            {property.description}
          </p>
        </div>
      </div>

      <!-- Key Features Section - Full Width -->
      <div class="bg-white rounded-xl shadow-md p-8 mb-8">
        <h2 class="text-2xl font-bold text-gray-900 mb-6">Key Features</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          {#each property.features as feature}
            <div class="flex items-start gap-3">
              <Check class="w-6 h-6 text-primary-600 shrink-0 mt-0.5" />
              <span class="text-gray-700">{feature}</span>
            </div>
          {/each}
        </div>
      </div>

      <!-- Contact Section - Full Width -->
      <div class="bg-white rounded-xl shadow-md p-8">
        <div class="text-center mb-8">
          <h2 class="text-2xl font-bold text-gray-900 mb-4">
            Interested in this property?
          </h2>
          <p class="text-gray-600 max-w-2xl mx-auto">
            Contact our expert real estate agent to schedule a viewing or get
            more information about this beautiful property.
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 max-w-4xl mx-auto">
          <!-- Agent Profile -->
          <div class="text-center">
            <div
              class="w-20 h-20 bg-primary-100 rounded-full flex items-center justify-center mx-auto mb-4"
            >
              <User class="w-10 h-10 text-primary-600" />
            </div>
            <h3 class="font-bold text-gray-900 text-lg">Sarah Johnson</h3>
            <p class="text-gray-600 mb-4">Senior Real Estate Agent</p>
          </div>

          <!-- Contact Methods -->
          <div class="space-y-4">
            <a
              href="tel:+15551234567"
              class="flex items-center gap-3 text-gray-700 hover:text-primary-600 transition-colors p-4 rounded-lg border border-gray-200 hover:border-primary-200 hover:bg-primary-50 group"
            >
              <div
                class="w-12 h-12 bg-primary-100 rounded-full flex items-center justify-center group-hover:bg-primary-200 transition-colors"
              >
                <Phone class="w-6 h-6 text-primary-600" />
              </div>
              <div class="text-left">
                <div class="font-semibold">Call Now</div>
                <div class="text-sm text-gray-600">+1 (555) 123-4567</div>
              </div>
            </a>

            <a
              href="mailto:info@premiumrealty.com"
              class="flex items-center gap-3 text-gray-700 hover:text-primary-600 transition-colors p-4 rounded-lg border border-gray-200 hover:border-primary-200 hover:bg-primary-50 group"
            >
              <div
                class="w-12 h-12 bg-primary-100 rounded-full flex items-center justify-center group-hover:bg-primary-200 transition-colors"
              >
                <Mail class="w-6 h-6 text-primary-600" />
              </div>
              <div class="text-left">
                <div class="font-semibold">Send Email</div>
                <div class="text-sm text-gray-600">info@premiumrealty.com</div>
              </div>
            </a>
          </div>

          <!-- Office Hours -->
          <div class="bg-gray-50 rounded-lg p-6">
            <h4 class="font-bold text-gray-900 mb-3">Office Hours</h4>
            <div class="space-y-2 text-sm text-gray-600">
              <div class="flex justify-between">
                <span>Mon - Fri:</span>
                <span class="font-medium">9:00 AM - 6:00 PM</span>
              </div>
              <div class="flex justify-between">
                <span>Saturday:</span>
                <span class="font-medium">10:00 AM - 4:00 PM</span>
              </div>
              <div class="flex justify-between">
                <span>Sunday:</span>
                <span class="font-medium">Closed</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
{:else}
  <div class="min-h-screen bg-gray-50 flex items-center justify-center">
    <div class="text-center">
      <h2 class="text-3xl font-bold text-gray-900 mb-4">Property not found</h2>
      <button on:click={goBack} class="btn-primary"> Back to Listings </button>
    </div>
  </div>
{/if}
