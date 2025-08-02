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
  <section class="contact-map">
    <div class="form-section">
      <h2>How to reach us</h2>
      <p class="intro-text">Lorem ipsum dolor sit amet, consetetur.</p>
      <form @submit.prevent="validate">
        <div class="form-group" :class="{ error: errors.firstName }">
          <label for="firstName">First Name *</label>
          <input id="firstName" v-model="firstName" />
          <p v-if="errors.firstName">{{ errors.firstName }}</p>
        </div>

        <div class="form-group" :class="{ error: errors.lastName }">
          <label for="lastName">Last Name *</label>
          <input id="lastName" v-model="lastName" />
          <p v-if="errors.lastName">{{ errors.lastName }}</p>
        </div>

        <div class="form-group" :class="{ error: errors.email }">
          <label for="email">Email *</label>
          <input id="email" v-model="email" type="email" />
          <p v-if="errors.email">{{ errors.email }}</p>
        </div>

        <div class="form-group">
          <label for="telephone">Telephone</label>
          <input id="telephone" v-model="telephone" type="tel" />
        </div>

        <div class="form-group" :class="{ error: errors.message }">
          <label for="message">Message *</label>
          <textarea id="message" v-model="message"></textarea>
          <p v-if="errors.message">{{ errors.message }}</p>
        </div>

        <div class="form-group" :class="{ error: errors.agreed }">
          <div class="checkbox-wrapper">
            <input type="checkbox" id="agreed" v-model="agreed" />
            <label for="agreed">I agree to the Terms & Conditions</label>
          </div>
          <p v-if="errors.agreed">{{ errors.agreed }}</p>
        </div>


        <button type="submit">SUBMIT</button>
      </form>

    </div>

    <div class="map-section">
      <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3037.204040437366!2d-3.6530426843102294!3d40.43966056393764!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd422f183e51e3b9%3A0x60a3136e08673a6d!2sAmadeus%20IT%20Group!5e0!3m2!1sen!2slk!4v1688283556186!5m2!1sen!2slk"
          width="100%"
          height="100%"
          style="border:0;"
          allowfullscreen
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
      ></iframe>
    </div>
  </section>
</template>

<style scoped>
.contact-map {
  display: flex;
  width: auto;
  min-height: 100vh;
  background-color: #000;
  color: white;
  flex-wrap: wrap;
  padding-left: 7vw;
  padding-right: 7vw;
}

.form-section,
.map-section {
  flex: 1;
  padding: 2rem;
}

h2 {
  margin-bottom: 0.5rem;
  font-size: 2rem;
}

.intro-text {
  margin-bottom: 1.5rem;
  font-size: 1rem;
  color: #ccc;
}

form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
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
  margin-top: 0.5rem;
  width: fit-content;
  align-self: flex-end;
}

button:hover {
  background-color: #ebf300;
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

.checkbox-wrapper input[type="checkbox"] {
  accent-color: #f89603;
  width: 18px;
  height: 18px;
  cursor: pointer;
}

.checkbox-wrapper label {
  cursor: pointer;
}

.map-section iframe {
  width: 100%;
  height: 100%;
  min-height: 500px;
  border: none;
}
</style>
