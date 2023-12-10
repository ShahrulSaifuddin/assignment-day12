<template>
  <h1>Contact Us</h1>
  <p>Use the form below to drop us an e-mail</p>
  <div id="app">
    <form>
      <label for="firstName">Name:</label>
      <input type="text" id="firstName" v-model="formData.firstName" required placeholder="First Name*"/>

      <label for="lastName">Name:</label>
      <input type="text" id="lastName" v-model="formData.lastName" required placeholder="Last Name*"/>

      <label for="email">Email:</label>
      <input type="email" id="email" v-model="formData.email" placeholder="Email*" />

      <label for="mobile">Phone Number:</label>
      <input type="tel" id="mobile" v-model="formData.mobile" placeholder="Phone Number" />

      <label for="website">Website:</label>
      <input type="text" id="website" v-model="formData.website" required placeholder="Website"/>

      <label for="company">Company:</label>
      <input type="text" id="company" v-model="formData.company" required placeholder="Company"/>

      <label for="message">What Can We Do For You?</label>
      <textarea id="message" v-model="formData.message" placeholder="What Can We Do For You?"></textarea>

      <button type="submit">Submit</button>
    </form>

    <div v-if="submitted">
      <p>Thank you for reaching out! We'll get back to you soon.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        firstName: '',
        lastName: '',
        email: '',
        mobile: '',
        website: '',
        company: '',
        message: '',
      },
      submitted: false
    };
  },
  methods: {
    submitForm() {
      this.formData = {
        firstName: '',
        lastName: '',
        email: '',
        mobile: '',
        website: '',
        company: '',
        message: '',
      };
      this.submitted = true;
    }
  }
};
</script>

<style scoped>

</style>
