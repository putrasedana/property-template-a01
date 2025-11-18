<script lang="ts">
  import { onDestroy } from "svelte";
  import { currentPage } from "./stores/navigation";
  import Navbar from "./components/Navbar.svelte";
  import Footer from "./components/Footer.svelte";
  import Home from "./pages/Home.svelte";
  import Listings from "./pages/Listings.svelte";
  import PropertyDetails from "./pages/PropertyDetails.svelte";
  import About from "./pages/About.svelte";
  import Contact from "./pages/Contact.svelte";

  const unsubscribe = currentPage.subscribe(() => {
    setTimeout(() => {
      window.scrollTo({
        top: 0,
        behavior: "smooth",
      });
    }, 0);
  });

  onDestroy(() => {
    unsubscribe();
  });
</script>

<div class="min-h-screen flex flex-col">
  <Navbar />

  <main class="grow">
    {#if $currentPage === "home"}
      <Home />
    {:else if $currentPage === "listings"}
      <Listings />
    {:else if $currentPage === "details"}
      <PropertyDetails />
    {:else if $currentPage === "about"}
      <About />
    {:else if $currentPage === "contact"}
      <Contact />
    {/if}
  </main>

  <Footer />
</div>
