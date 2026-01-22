<template>
  <section id="booking" class="section container fade-in-up half-section">
    <h2>Have a Question</h2>
    <form class="booking-form" novalidate>
      <div class="row two">
        <input name="name" type="text" placeholder="Full Name" required />
        <input name="email" type="email" placeholder="Email Address" required />
      </div>
      <div class="row two">
        <input name="phone" type="tel" placeholder="Phone / WhatsApp" required />
      </div>
      <div class="row two">
        <input name="message" type="text" placeholder="Message" required />
      </div>
    </form>
  </section>
</template>

<script>
export default {};
</script>
