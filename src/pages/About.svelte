<script lang="ts">
  import AgentCard from "../components/AgentCard.svelte";
  import { agents } from "../data/properties";
  import { currentPage } from "../stores/navigation";

  function navigateToContact() {
    currentPage.set("contact");
  }
</script>

<div class="min-h-screen bg-gray-50">
  <section
    class="bg-linear-to-br from-primary-600 to-accent-600 text-black py-20"
  >
    <div class="max-w-7xl mx-auto text-center px-4 sm:px-6 lg:px-8">
      <h1 class="text-4xl md:text-5xl font-bold mb-6">About Premium Realty</h1>
      <div class="max-w-3xl mx-auto">
        <p class="text-xl opacity-90 leading-relaxed">
          We're dedicated to helping you find your perfect property. With years
          of experience and a passion for real estate, our team provides
          unparalleled service and expertise.
        </p>
      </div>
    </div>
  </section>

  <section class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <div>
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-6">
            Our Story
          </h2>
          <div class="space-y-4 text-gray-700 leading-relaxed">
            <p>
              Founded in 2010, Premium Realty has grown from a small local
              agency to one of the most trusted names in real estate. Our
              journey began with a simple mission: to revolutionize the property
              buying and selling experience.
            </p>
            <p>
              Today, we're proud to have helped thousands of families find their
              dream homes and assisted countless investors in building
              successful real estate portfolios. Our success is built on a
              foundation of trust, expertise, and unwavering commitment to our
              clients.
            </p>
            <p>
              We believe that finding the right property is about more than just
              square footage and price tags. It's about understanding your
              lifestyle, your dreams, and your future goals. That's why we take
              the time to truly listen and provide personalized guidance every
              step of the way.
            </p>
          </div>
        </div>

        <div class="relative">
          <img
            src="https://images.pexels.com/photos/380769/pexels-photo-380769.jpeg?auto=compress&cs=tinysrgb&w=1200"
            alt="Office"
            class="rounded-xl shadow-2xl"
          />
        </div>
      </div>
    </div>
  </section>

  <section class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
          Our Values
        </h2>
        <p class="text-xl text-gray-600">What drives us every day</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div class="bg-white p-8 rounded-xl shadow-md text-center">
          <div
            class="w-16 h-16 bg-primary-100 rounded-full flex items-center justify-center mx-auto mb-6"
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
                d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z"
              />
            </svg>
          </div>
          <h3 class="text-xl font-bold text-gray-900 mb-3">Client First</h3>
          <p class="text-gray-600 leading-relaxed">
            Your goals are our priority. We put your needs first and work
            tirelessly to exceed your expectations.
          </p>
        </div>

        <div class="bg-white p-8 rounded-xl shadow-md text-center">
          <div
            class="w-16 h-16 bg-accent-100 rounded-full flex items-center justify-center mx-auto mb-6"
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
                d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"
              />
            </svg>
          </div>
          <h3 class="text-xl font-bold text-gray-900 mb-3">Integrity</h3>
          <p class="text-gray-600 leading-relaxed">
            Honesty and transparency guide every interaction. We build lasting
            relationships based on trust.
          </p>
        </div>

        <div class="bg-white p-8 rounded-xl shadow-md text-center">
          <div
            class="w-16 h-16 bg-primary-100 rounded-full flex items-center justify-center mx-auto mb-6"
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
          <h3 class="text-xl font-bold text-gray-900 mb-3">Excellence</h3>
          <p class="text-gray-600 leading-relaxed">
            We strive for excellence in everything we do, from market analysis
            to closing deals.
          </p>
        </div>
      </div>
    </div>
  </section>

  <section class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
          Meet Our Team
        </h2>
        <p class="text-xl text-gray-600">
          Expert agents ready to help you succeed
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        {#each agents as agent}
          <AgentCard {agent} />
        {/each}
      </div>
    </div>
  </section>

  <section class="py-20 bg-linear-to-br from-primary-600 to-accent-600">
    <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <h2 class="text-3xl md:text-4xl font-bold mb-6">
        Ready to Work With Us?
      </h2>
      <p class="text-xl mb-8 opacity-90">
        Let's discuss how we can help you achieve your real estate goals.
      </p>
      <button
        on:click={navigateToContact}
        class="btn-primary cursor-pointer w-full sm:w-auto px-8 py-4 rounded-lg font-medium text-lg transition-colors duration-200"
      >
        Contact Our Team
      </button>
    </div>
  </section>
</div>
