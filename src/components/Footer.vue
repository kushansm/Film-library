<template>
  <footer>
    <div class="ui-top">
      <div class="ui-top-companyname">Amadeus IT Group</div>
      <div class="social-links">
        <span>Follow us on</span>
        <img src="../../src/assets/Twitter White.svg" alt="Twitter" />
        <img src="../../src/assets/Youtube White.svg" alt="YouTube" />
      </div>
    </div>

    <div class="address">
      <p>C. Salvador de Madariaga, 1</p>
      <p>28027 Madrid</p>
      <p>Spain</p>
    </div>

    <hr class="footer-divider" />

    <div class="footer-bottom">
      <div class="footer-left">
        <p> Copyright © 2022 Amadeus Hotels. All rights reserved.</p>
      </div>
      <div class="footer-right">
        <p>Photos by Felix Mooneeram & Serge Kutuzov on Unsplash</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
footer {
  background: #151515;
  color: white;
  padding: 0.5rem 1.5rem;
  font-size: 0.9rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding-left: 7vw;
  padding-right: 7vw;
}


.ui-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}

.ui-top-companyname {
  font-size: 1.2rem;
  font-weight: bold;
}


.social-links {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 1rem;
}
.social-links img {
  height: 20px;
}


.address {
  text-align: left;
  font-size: 0.95rem;
}
.address p {
  margin: 2px 0;
  line-height: 1.2;
}

.footer-divider {
  border: none;
  border-top: 0.5px solid #555;
  margin: 0px
}


.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  font-size: 0.75rem;
}

.footer-left {
  text-align: left;
}
.footer-right {
  text-align: right;
}
</style>

<script setup lang="ts">
</script>