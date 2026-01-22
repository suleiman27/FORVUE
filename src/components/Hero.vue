<template>
  <section id="home" class="hero parallax">
    <div class="hero-slideshow">
      <img v-for="(slide, index) in slides" :key="index" :src="slide" class="slide" :class="{ active: currentSlide === index }" />
    </div>
    <div class="hero-overlay"></div>
    <div class="hero-content container fade-in-up">
      <h1>Efficient customer support and accurate data solutions.</h1>
      <p class="lead">Delivering dependable support and precise data for your business.</p>
      <div class="ctas">
        <a class="btn btn-primary" href="#booking">Start our services</a>
        <button class="btn btn-secondary" @click="quote">Get a Free Quote</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      slides: [
        "/images/BACKGROUND.jpg",
        "/images/OUTSOURCING.jpg",
        "/images/OUTSOURCING1.jpg",
      ],
      currentSlide: 0,
    };
  },
  mounted() {
    setInterval(() => {
      this.currentSlide = (this.currentSlide + 1) % this.slides.length;
    }, 4000);
  },
  methods: {
    quote() {
      alert("Quote feature coming soon!");
    },
  },
};
</script>
