<template>
  <footer class="site-footer">
    <div class="container">
      <div>© <span>{{ year }}</span> SulTech Solutions</div>
      <div><a href="mailto:info@sultech.com">info@sultech.com</a> • +254 708189577</div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      year: new Date().getFullYear(),
    };
  },
};
</script>
