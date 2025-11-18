<script lang="ts">
  import { MapPin, Phone, Mail, Clock, Navigation } from "lucide-svelte";

  function openInGoogleMaps() {
    window.open(
      "https://www.google.com/maps/dir/?api=1&destination=123+Real+Estate+Avenue+New+York+NY+10001",
      "_blank"
    );
  }
</script>

<div class="min-h-screen">
  <section class="bg-linear-to-br from-primary-600 to-accent-600 py-20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <h1 class="text-4xl md:text-5xl font-bold text-black mb-6">
        Visit Our Office
      </h1>
      <p class="text-xl text-black opacity-90 max-w-2xl mx-auto">
        Come see us in person or get in touch. We're here to help with all your
        real estate needs.
      </p>
    </div>
  </section>

  <section class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        <!-- Contact Information -->
        <div class="space-y-8">
          <div>
            <h2 class="text-3xl font-bold text-gray-900 mb-6">
              Contact Information
            </h2>

            <div class="bg-white rounded-xl shadow-md p-8 space-y-6">
              <div class="flex items-start gap-4">
                <div
                  class="w-12 h-12 bg-primary-100 rounded-full flex items-center justify-center shrink-0"
                >
                  <MapPin class="w-6 h-6 text-primary-600" />
                </div>
                <div>
                  <h3 class="font-bold text-gray-900 mb-1">Office Address</h3>
                  <p class="text-gray-600">
                    123 Real Estate Avenue<br />Suite 100<br />New York, NY
                    10001
                  </p>
                  <button
                    on:click={openInGoogleMaps}
                    class="mt-2 text-primary-600 hover:text-primary-700 font-medium text-sm flex items-center gap-1 transition-colors"
                  >
                    <Navigation class="w-4 h-4" />
                    Get Directions
                  </button>
                </div>
              </div>

              <div class="flex items-start gap-4">
                <div
                  class="w-12 h-12 bg-accent-100 rounded-full flex items-center justify-center shrink-0"
                >
                  <Phone class="w-6 h-6 text-accent-600" />
                </div>
                <div>
                  <h3 class="font-bold text-gray-900 mb-1">Phone</h3>
                  <p class="text-gray-600">
                    <a
                      href="tel:+15551234567"
                      class="hover:text-primary-600 transition-colors font-medium"
                      >+1 (555) 123-4567</a
                    >
                  </p>
                </div>
              </div>

              <div class="flex items-start gap-4">
                <div
                  class="w-12 h-12 bg-primary-100 rounded-full flex items-center justify-center shrink-0"
                >
                  <Mail class="w-6 h-6 text-primary-600" />
                </div>
                <div>
                  <h3 class="font-bold text-gray-900 mb-1">Email</h3>
                  <p class="text-gray-600">
                    <a
                      href="mailto:info@premiumrealty.com"
                      class="hover:text-primary-600 transition-colors font-medium"
                      >info@premiumrealty.com</a
                    >
                  </p>
                </div>
              </div>

              <div class="flex items-start gap-4">
                <div
                  class="w-12 h-12 bg-accent-100 rounded-full flex items-center justify-center shrink-0"
                >
                  <Clock class="w-6 h-6 text-accent-600" />
                </div>
                <div>
                  <h3 class="font-bold text-gray-900 mb-1">Business Hours</h3>
                  <p class="text-gray-600">
                    Monday - Friday: 9:00 AM - 6:00 PM<br />
                    Saturday: 10:00 AM - 4:00 PM<br />
                    Sunday: Closed
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Google Map Embed -->
        <div class="space-y-8">
          <h2 class="text-3xl font-bold text-gray-900 mb-6">Our Location</h2>
          <div class="bg-white rounded-xl shadow-md overflow-hidden">
            <div class="w-full h-[470px] overflow-hidden">
              <iframe
                title="Google Maps Embed"
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3022.9663095343008!2d-74.00425892426408!3d40.74096685738839!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x89c259bf5c1654f3%3A0xc80f9cfce5383d5d!2s123%20Real%20Estate%20Ave%2C%20New%20York%2C%20NY%2010001%2C%20USA!5e0!3m2!1sen!2s!4v1700000000000!5m2!1sen!2s"
                width="100%"
                height="100%"
                style="border:0;"
                loading="lazy"
                allowfullscreen
                referrerpolicy="no-referrer-when-downgrade"
              ></iframe>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- CTA Section -->
  <section class="py-16 bg-white">
    <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <h2 class="text-3xl font-bold text-gray-900 mb-4">
        Ready to Get Started?
      </h2>
      <p class="text-xl text-gray-600 mb-8 max-w-2xl mx-auto">
        Whether you're buying, selling, or just exploring options, we're here to
        guide you every step of the way.
      </p>
      <div class="flex flex-col sm:flex-row gap-4 justify-center">
        <a
          href="tel:+15551234567"
          class="btn-primary cursor-pointer px-8 py-4 rounded-lg font-medium transition-colors duration-200 inline-flex items-center justify-center gap-3 text-lg"
        >
          <Phone class="w-6 h-6" />
          Call Us Today
        </a>
        <a
          href="mailto:info@premiumrealty.com"
          class="btn-primary cursor-pointer px-8 py-4 rounded-lg font-medium transition-colors duration-200 inline-flex items-center justify-center gap-3 text-lg"
        >
          <Mail class="w-6 h-6" />
          Send Message
        </a>
      </div>
    </div>
  </section>
</div>
