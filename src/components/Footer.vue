<template>
  <footer class="fade-in" aria-label="Footer">
    <div class="footer-top">
      <div class="footer-left">
        <div class="company-name">Amadeus IT Group</div>
        <address class="address">
          <p>C. Salvador de Madariaga, 1</p>
          <p>28027 Madrid</p>
          <p>Spain</p>
        </address>
      </div>

      <div class="footer-right-icons" aria-label="Follow us on social media">
        <div class="follow-text">Follow us on</div>
        <!-- Added tabindex & role="link" for keyboard accessibility -->
        <img
            src="../../src/assets/Twitter White.svg"
            alt="Twitter"
            tabindex="0"
            role="link"
            aria-describedby="twitterDesc"
            @keydown.enter="$emit('openTwitter')"
        />
        <span id="twitterDesc" class="sr-only">Link to Twitter</span>

        <img
            src="../../src/assets/Youtube White.svg"
            alt="YouTube"
            tabindex="0"
            role="link"
            aria-describedby="youtubeDesc"
            @keydown.enter="$emit('openYouTube')"
        />
        <span id="youtubeDesc" class="sr-only">Link to YouTube</span>
      </div>
    </div>

    <hr class="footer-divider" />

    <div class="footer-bottom">
      <div class="footer-copy">
        &copy; 2022 Amadeus Hotels. All rights reserved.
      </div>
      <div class="footer-photo">
        Photos by Felix Mooneeram &amp; Serge Kutuzov on Unsplash
      </div>
    </div>
  </footer>
</template>

<style scoped>
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(12px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in {
  animation: fadeIn 1s ease forwards;
}

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

.address p {
  margin: 0;
  line-height: 1.3;
}

address {
  font-style: normal;
}

.follow-text {
  font-size: 1rem;
}

.footer-right-icons {
  display: flex;
  gap: 0.7rem;
  align-items: center;
}

.footer-right-icons img {
  height: 20px;
  cursor: pointer;
  outline-offset: 3px;
  transition: filter 0.3s ease, transform 0.3s ease;
}

.footer-right-icons img:hover,
.footer-right-icons img:focus {
  filter: brightness(1.5);
  transform: scale(1.1);
  outline: 2px solid #f89603;
  outline-offset: 2px;
}

/* Screen-reader only text */
.sr-only {
  position: absolute !important;
  width: 1px !important;
  height: 1px !important;
  padding: 0 !important;
  margin: -1px !important;
  overflow: hidden !important;
  clip: rect(0, 0, 0, 0) !important;
  white-space: nowrap !important;
  border: 0 !important;
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
