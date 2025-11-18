<script lang="ts">
  import { currentPage } from "../stores/navigation";
  import PropertyCard from "../components/PropertyCard.svelte";
  import { properties, testimonials } from "../data/properties";

  const featuredProperties = properties.filter((p) => p.featured);

  function navigateToListings() {
    currentPage.set("listings");
  }

  function navigateToContact() {
    currentPage.set("contact");
  }
</script>

<div>
  <section class="relative h-[650px] flex items-center overflow-hidden">
    <!-- Background Image -->
    <div class="absolute inset-0">
      <img
        src="https://images.pexels.com/photos/1396122/pexels-photo-1396122.jpeg?auto=compress&cs=tinysrgb&w=1600"
        alt="Hero background"
        class="w-full h-full object-cover brightness-75"
      />
    </div>

    <!-- Gradient Overlay for Text Readability -->
    <div
      class="absolute inset-0 bg-linear-to-b from-black/40 via-black/20 to-transparent"
    ></div>

    <!-- Content -->
    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <h1
        class="text-5xl md:text-6xl lg:text-7xl font-bold text-white mb-6 leading-tight drop-shadow-lg"
      >
        Find Your Dream<br />
        <span class="text-primary-300">Property</span>
      </h1>

      <p
        class="text-xl md:text-2xl text-gray-200 mb-8 max-w-3xl mx-auto drop-shadow"
      >
        Discover exceptional homes and properties tailored to your lifestyle.
        Your perfect space awaits.
      </p>

      <div class="flex flex-col sm:flex-row gap-4 justify-center">
        <button
          on:click={navigateToListings}
          class="btn-primary cursor-pointer text-lg px-8 py-4 shadow-lg"
        >
          Browse Properties
        </button>

        <button
          on:click={navigateToContact}
          class="btn-primary cursor-pointer text-lg px-8 py-4 shadow-lg"
        >
          Contact Us
        </button>
      </div>
    </div>
  </section>

  <section class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-12">
        <h2 class="text-4xl font-bold text-gray-900 mb-4">
          Featured Properties
        </h2>
        <p class="text-xl text-gray-600">
          Explore our handpicked selection of premium properties
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mb-12">
        {#each featuredProperties as property}
          <PropertyCard {property} />
        {/each}
      </div>
    </div>
  </section>

  <section class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <h2 class="text-4xl font-bold text-gray-900 mb-4">Why Choose Us</h2>
        <p class="text-xl text-gray-600">Your trusted partner in real estate</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <!-- Card 1 -->
        <div
          class="bg-white p-8 rounded-xl shadow-md hover:shadow-xl transition-shadow text-center"
        >
          <div
            class="w-16 h-16 bg-primary-100 rounded-full flex items-center justify-center mb-6 mx-auto"
          >
            <svg
              class="w-16 h-16 text-primary-600"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
              />
            </svg>
          </div>
          <h3 class="text-2xl font-bold text-gray-900 mb-4">Expert Guidance</h3>
          <p class="text-gray-600 leading-relaxed">
            Our experienced agents provide personalized service and expert
            market insights to help you make informed decisions.
          </p>
        </div>

        <!-- Card 2 -->
        <div
          class="bg-white p-8 rounded-xl shadow-md hover:shadow-xl transition-shadow text-center"
        >
          <div
            class="w-16 h-16 bg-accent-100 rounded-full flex items-center justify-center mb-6 mx-auto"
          >
            <svg
              class="w-16 h-16 text-accent-600"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"
              />
            </svg>
          </div>
          <h3 class="text-2xl font-bold text-gray-900 mb-4">
            Premium Selection
          </h3>
          <p class="text-gray-600 leading-relaxed">
            Access exclusive listings and premium properties that match your
            specific requirements and lifestyle preferences.
          </p>
        </div>

        <!-- Card 3 -->
        <div
          class="bg-white p-8 rounded-xl shadow-md hover:shadow-xl transition-shadow text-center"
        >
          <div
            class="w-16 h-16 bg-primary-100 rounded-full flex items-center justify-center mb-6 mx-auto"
          >
            <svg
              class="w-16 h-16 text-primary-600"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M13 10V3L4 14h7v7l9-11h-7z"
              />
            </svg>
          </div>
          <h3 class="text-2xl font-bold text-gray-900 mb-4">
            Fast & Efficient
          </h3>
          <p class="text-gray-600 leading-relaxed">
            Streamlined processes and dedicated support ensure a smooth
            transaction from search to closing.
          </p>
        </div>
      </div>
    </div>
  </section>

  <section class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <h2 class="text-4xl font-bold text-gray-900 mb-4">
          What Our Clients Say
        </h2>
        <p class="text-xl text-gray-600">
          Real stories from satisfied homeowners
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        {#each testimonials as testimonial}
          <div class="bg-gray-50 p-8 rounded-xl">
            <div class="flex gap-1 mb-4">
              {#each Array(testimonial.rating) as _}
                <svg
                  class="w-5 h-5 text-yellow-400"
                  fill="currentColor"
                  viewBox="0 0 20 20"
                >
                  <path
                    d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"
                  />
                </svg>
              {/each}
            </div>
            <p class="text-gray-700 mb-6 leading-relaxed italic">
              "{testimonial.content}"
            </p>
            <div class="flex items-center gap-4">
              <img
                src={testimonial.image}
                alt={testimonial.name}
                class="w-12 h-12 rounded-full object-cover"
              />
              <div>
                <p class="font-bold text-gray-900">{testimonial.name}</p>
                <p class="text-sm text-gray-600">{testimonial.role}</p>
              </div>
            </div>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <section class="py-20 bg-gray-50 text-center">
    <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <h2 class="text-4xl md:text-5xl font-bold mb-6">
        Ready to Find Your Perfect Property?
      </h2>
      <p class="text-xl mb-8 opacity-90">
        Let our expert team guide you through every step of your real estate
        journey.
      </p>
      <button
        on:click={navigateToListings}
        class="btn-primary cursor-pointer text-lg px-8 py-4 shadow-lg"
      >
        View All Properties
      </button>
    </div>
  </section>
</div>
