<template>
  <main>
    <Hero />
    <Services />
    <WhyChoose />
    <About />
    <Booking />
    <Reviews />
  </main>
</template>

<script>
import Hero from "../components/Hero.vue";
import Services from "../components/Services.vue";
import WhyChoose from "../components/WhyChoose.vue";
import About from "../components/About.vue";
import Booking from "../components/Booking.vue";
import Reviews from "../components/Reviews.vue";

export default {
  components: {
    Hero,
    Services,
    WhyChoose,
    About,
    Booking,
    Reviews,
  },
};
</script>
