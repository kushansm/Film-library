<script setup lang="ts">
import { ref } from 'vue';

const firstName = ref('');
const lastName = ref('');
const email = ref('');
const telephone = ref('');
const message = ref('');
const agreed = ref(false);

const errors = ref({
  firstName: '',
  lastName: '',
  email: '',
  message: '',
  agreed: '',
});

function validate() {
  errors.value = {
    firstName: firstName.value ? '' : 'First name is required',
    lastName: lastName.value ? '' : 'Last name is required',
    email: email.value ? '' : 'Email is required',
    message: message.value ? '' : 'Message is required',
    agreed: agreed.value ? '' : 'You must agree to the Terms & Conditions',
  };

  const isValid = Object.values(errors.value).every((e) => e === '');

  if (isValid) {
    alert(
        `Form Submitted:\nFirst Name: ${firstName.value}\nLast Name: ${lastName.value}\nEmail: ${email.value}\nTelephone: ${telephone.value}\nMessage: ${message.value}`
    );

    // Reset fields
    firstName.value = '';
    lastName.value = '';
    email.value = '';
    telephone.value = '';
    message.value = '';
    agreed.value = false;
  }
}
</script>

<template>
  <section class="contact-us-heading" tabindex="0">
    <h2>How to reach us</h2>
    <p class="intro-text">Lorem ipsum dolor sit amet, consetetur.</p>
  </section>

  <section class="contact-map">
    <div class="form-section fade-in" role="form" aria-labelledby="contact-form-title">
      <form @submit.prevent="validate" novalidate>
        <h3 id="contact-form-title" class="form-title" tabindex="0">Contact Form</h3>

        <div class="form-group" :class="{ error: errors.firstName }">
          <label for="firstName">First Name *</label>
          <input id="firstName" v-model="firstName" aria-required="true" aria-invalid="{{errors.firstName ? 'true' : 'false'}}" />
          <p v-if="errors.firstName" role="alert">{{ errors.firstName }}</p>
        </div>

        <div class="form-group" :class="{ error: errors.lastName }">
          <label for="lastName">Last Name *</label>
          <input id="lastName" v-model="lastName" aria-required="true" aria-invalid="{{errors.lastName ? 'true' : 'false'}}" />
          <p v-if="errors.lastName" role="alert">{{ errors.lastName }}</p>
        </div>

        <div class="form-group" :class="{ error: errors.email }">
          <label for="email">Email *</label>
          <input id="email" v-model="email" type="email" aria-required="true" aria-invalid="{{errors.email ? 'true' : 'false'}}" />
          <p v-if="errors.email" role="alert">{{ errors.email }}</p>
        </div>

        <div class="form-group">
          <label for="telephone">Telephone</label>
          <input id="telephone" v-model="telephone" type="tel" />
        </div>

        <div class="form-group" :class="{ error: errors.message }">
          <label for="message">Message *</label>
          <textarea id="message" v-model="message" aria-required="true" aria-invalid="{{errors.message ? 'true' : 'false'}}"></textarea>
          <p v-if="errors.message" role="alert">{{ errors.message }}</p>
        </div>

        <div class="form-group" :class="{ error: errors.agreed }">
          <div class="checkbox-wrapper">
            <input type="checkbox" id="agreed" v-model="agreed" aria-required="true" aria-invalid="{{errors.agreed ? 'true' : 'false'}}" />
            <label for="agreed">I agree to the Terms & Conditions</label>
          </div>
          <p v-if="errors.agreed" role="alert">{{ errors.agreed }}</p>
        </div>

        <button type="submit" aria-label="Submit contact form">SUBMIT</button>
      </form>
    </div>

    <div class="map-section" aria-label="Location map">
      <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3037.204040437366!2d-3.6530426843102294!3d40.43966056393764!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd422f183e51e3b9%3A0x60a3136e08673a6d!2sAmadeus%20IT%20Group!5e0!3m2!1sen!2slk!4v1688283556186!5m2!1sen!2slk"
          style="border:0;"
          allowfullscreen
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
      ></iframe>
    </div>
  </section>
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

.contact-us-heading {
  padding: 2rem 7vw 1rem;
  background-color: #000;
  color: white;
  outline-offset: 4px;
}
.contact-us-heading h2 {
  font-size: 2rem;
  margin-bottom: 0.5rem;
  cursor: pointer;
  transition: color 0.3s ease, text-decoration 0.3s ease;
  outline-offset: 2px;
}
.contact-us-heading h2:hover,
.contact-us-heading h2:focus {
  color: #f89603;
  text-decoration: underline;
  outline: none;
}

.contact-us-heading .intro-text {
  color: #ccc;
  font-size: 1rem;
}

.contact-map {
  background-color: #000;
  color: white;
  padding: 7vw;
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
  box-sizing: border-box;
}
@media (min-width: 768px) {
  .contact-map {
    grid-template-columns: 1fr 2fr;
  }
}
@media (min-width: 1024px) {
  .contact-map {
    grid-template-columns: 1fr 2fr;
  }
}

.form-section,
.map-section {
  width: 100%;
  box-sizing: border-box;
}
.map-section iframe {
  width: 100%;
  height: 100%;
  min-height: 500px;
  border: none;
  box-sizing: border-box;
}

form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.form-title {
  font-size: 1.75rem;
  margin-bottom: 1rem;
  cursor: pointer;
  transition: color 0.3s ease, text-decoration 0.3s ease;
  outline-offset: 2px;
}
.form-title:hover,
.form-title:focus {
  color: #f89603;
  text-decoration: underline;
  outline: none;
}

input,
textarea {
  width: 100%;
  padding: 0.75rem;
  background: #111;
  border: 1px solid #555;
  border-radius: 4px;
  color: white;
  font-size: 1rem;
  box-sizing: border-box;
  outline-offset: 3px;
}
input:focus,
textarea:focus {
  border-color: #f89603;
  outline: none;
}

textarea {
  resize: vertical;
  min-height: 100px;
}

button {
  padding: 0.5rem 1rem;
  background-color: #f89603;
  color: white;
  border: none;
  border-radius: 4px;
  font-weight: bold;
  font-size: 1rem;
  cursor: pointer;
  width: fit-content;
  align-self: flex-end;
  transition: background-color 0.3s ease;
}

button:hover,
button:focus {
  background-color: #ebf300;
  outline: none;
}

.form-group.error input,
.form-group.error textarea {
  border-color: red;
}

.form-group.error p {
  color: red;
  font-size: 0.85rem;
  margin-top: 0.25rem;
}

.checkbox-wrapper {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 1rem;
}

.checkbox-wrapper input[type='checkbox'] {
  accent-color: #f89603;
  width: 18px;
  height: 18px;
  cursor: pointer;
  outline-offset: 3px;
}
.checkbox-wrapper input[type='checkbox']:focus {
  outline: 2px solid #f89603;
  outline-offset: 0;
}

.checkbox-wrapper label {
  cursor: pointer;
}

.map-section iframe {
  width: 100%;
  height: 100%;
  min-height: 400px;
  border: none;
}

@media (max-width: 768px) {
  .contact-map {
    grid-template-columns: 1fr;
    padding: 5vw;
  }
  .contact-us-heading h2 {
    font-size: 1.5rem;
  }
  .map-section iframe {
    min-height: 300px;
  }
}

@media (max-width: 480px) {
  .contact-us-heading h2 {
    font-size: 1.2rem;
  }
  .contact-us-heading .intro-text {
    font-size: 0.95rem;
  }
  button {
    width: 100%;
  }
}
</style>
