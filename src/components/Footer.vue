<template>
  <footer>
    <div class="footer-top">
      <div class="footer-left">
        <div class="company-name">Amadeus IT Group</div>
        <div class="address">
          <p>C. Salvador de Madariaga, 1</p>
          <p>28027 Madrid</p>
          <p>Spain</p>
        </div>
      </div>

      <div class="footer-right-icons">
        <div class="follow-text">Follow us on</div>
        <img src="../../src/assets/Twitter White.svg" alt="Twitter" />
        <img src="../../src/assets/Youtube White.svg" alt="YouTube" />
      </div>
    </div>

    <hr class="footer-divider" />

    <div class="footer-bottom">
      <div class="footer-copy">Copyright © 2022 Amadeus Hotels. All rights reserved.</div>
      <div class="footer-photo">Photos by Felix Mooneeram & Serge Kutuzov on Unsplash</div>
    </div>
  </footer>
</template>


<style scoped>
footer {
  background: #151515;
  color: white;
  padding: 1.5rem 7vw;
  font-size: 0.9rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.footer-top {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-wrap: wrap;
}

.footer-left {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  text-align: left;
}

.company-name {
  font-size: 1.2rem;
  font-weight: bold;
}

.follow-text {
  font-size: 1rem;
}

.address p {
  margin: 0;
  line-height: 1.3;
}

.footer-right-icons {
  display: flex;
  gap: 0.7rem;
  align-items: center;
}

.footer-right-icons img {
  height: 20px;
}

.footer-divider {
  border: none;
  border-top: 0.5px solid #555;
  margin: 0;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  font-size: 0.75rem;
}

.footer-copy,
.footer-photo {
  text-align: left;
}

/* Tablet view: center footer-bottom text */
@media (max-width: 1024px) and (min-width: 768px) {
  .footer-bottom {
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 0.5rem;
  }
}

/* Mobile view: stack everything centered */
@media (max-width: 767px) {
  .footer-top {
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 0.5rem;
  }

  .footer-left {
    align-items: center;
    text-align: center;
  }

  .footer-right-icons {
    justify-content: center;
  }

  .footer-bottom {
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 0.5rem;
  }
}

</style>
<script setup lang="ts">
</script>