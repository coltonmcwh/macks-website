<template>
  <div>
    <nav class="site-nav">
      <RouterLink to="/" class="nav-brand">✦ <span>Macks</span>Jewelry</RouterLink>
      <ul class="nav-links">
        <li><RouterLink to="/">Home</RouterLink></li>
        <li><RouterLink to="/shop">Shop</RouterLink></li>
      </ul>
    </nav>
    <RouterView />
    <footer class="site-footer">
      <div class="ornate-divider"><span>✦ ✦ ✦</span></div>
      <p class="footer-text">✦ Macks Jewelry ✦ for baddies ✦</p>
    </footer>
  </div>
</template>

<script setup>
</script>

<style>
@import './assets/main.css';

.site-footer {
  padding: 2rem 3rem;
  text-align: center;
  border-top: 1px solid #1a1a1a;
  margin-top: 4rem;
}

.footer-text {
  font-family: 'Cinzel', serif;
  font-size: 0.65rem;
  letter-spacing: 0.4em;
  color: #444;
  text-transform: uppercase;
}
</style>
