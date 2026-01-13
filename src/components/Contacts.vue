<template>
	<!-- Contact Section -->
	<section id="contact" class="py-5">
	  <div class="container-fluid">
	    <div class="row">
	      
	      <!-- Left Side: Google Maps -->
	      <div class="col-md-6 p-0">
	        <iframe 
	          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d387190.2799182848!2d-74.2598756872381!3d40.69767006386565!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zNDDCsDQxJzUxLjYiTiA3NMKwMTUnMjkuNyJX!5e0!3m2!1sen!2sus!4v1636592377723!5m2!1sen!2sus" 
	          width="100%" 
	          height="100%" 
	          style="border:0;" 
	          allowfullscreen="" 
	          loading="lazy">
	        </iframe>
	      </div>
	      
	      <!-- Right Side: Contact Form -->
	      <div class="col-md-6 d-flex flex-column justify-content-center p-5 bg-light">
	        <h2 class="mb-4">Contact Me</h2>
	        <form @submit.prevent="submitForm">
	          <div class="mb-3">
	            <label for="name" class="form-label">Name</label>
	            <input v-model="name" type="text" class="form-control" id="name" placeholder="Enter your name" required>
	          </div>
	          <div class="mb-3">
	            <label for="email" class="form-label">Email</label>
	            <input v-model="email" type="email" class="form-control" id="email" placeholder="Enter your email" required>
	          </div>
	          <div class="mb-3">
	            <label for="message" class="form-label">Message</label>
	            <textarea v-model="message" class="form-control" id="message" rows="4" placeholder="Write your message" required></textarea>
	          </div>
	          <button type="submit" class="btn btn-dark" :disabled="isLoading">
	          	{{
	          		isLoading ? "Sending. . .": "Send"
	          	}}
	          </button>
	        </form>

	        <!-- Social Icons -->
	        <div class="mt-4 d-flex gap-3">
	          <!-- LinkedIn -->
	          <a href="https://www.linkedin.com" target="_blank">
	            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" 
	                 alt="LinkedIn" width="40" height="40">
	          </a>
	          <!-- GitHub -->
	          <a href="https://github.com" target="_blank">
	            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" 
	                 alt="GitHub" width="40" height="40">
	          </a>
	          <!-- GitLab -->
	          <a href="https://gitlab.com" target="_blank">
	            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/gitlab/gitlab-original.svg" 
	                 alt="GitLab" width="40" height="40">
	          </a>
	        </div>
	        <div class="d-flex justify-content-end">
	        	<div ref="recaptchaContainer"></div>
	        </div>
	      </div>
	      
	    </div>
	  </div>
	</section>
</template>

<!-- This is from the official documentation of web3 -->
<script setup>

import { ref, onMounted } from "vue";

import { Notyf } from 'notyf';
import 'notyf/notyf.min.css';

const WEB3FORMS_ACCESS_KEY = "d3259b9b-d8b5-4e15-803a-0fc37e7a26e6";
const name = ref("")
const email = ref("")
const message = ref("")

// Loading state
const isLoading = ref(false);

const notyf = new Notyf();

// configurations needed for the recaptcha
const SITE_KEY = '6LdnVUksAAAAAF2SPMN07TM0WVgMjNzXRn2aGTZm'
const recaptchaContainer = ref(null);
const recaptchaWidgetId = ref(null);
const recaptchaToken = ref('');

// Callback called by reCAPTCHA when successful
function onRecaptchaSuccess(token) {
  recaptchaToken.value = token;
}

// Callback when expired
function onRecaptchaExpired() {
  recaptchaToken.value = '';
}

// Function to render the reCAPTCHA widget
function renderRecaptcha() {
  if (!window.grecaptcha) {
    console.error('reCAPTCHA not loaded');
    return;
  }

  recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
    sitekey: SITE_KEY,
    size: 'normal', // or 'compact'
    callback: onRecaptchaSuccess,
    'expired-callback': onRecaptchaExpired,
  });
}

// Function to reset reCAPTCHA 
function resetRecaptcha() {
  if (recaptchaWidgetId.value !== null) {
    window.grecaptcha.reset(recaptchaWidgetId.value);
    recaptchaToken.value = '';
  }
}



onMounted(() => {
  // This code waits for the Google reCAPTCHA library to load, then renders the reCAPTCHA widget using onMounted hook. 
  // The widget is rendered with grecaptcha.render(), which requires a sitekey. 
  // Callback functions handle success and expiration events. 
  // reCAPTCHA is reset upon form submission to clear the token.
  const interval = setInterval(() => {
    if (window.grecaptcha && window.grecaptcha.render) {
      renderRecaptcha();
      clearInterval(interval);
    }
  }, 100);

  onBeforeUnmount(() => {
    clearInterval(interval);
  });
});

// The submitForm() handler function sends the form data to web3forms and displays success or failure notifications toast
const submitForm = async () => {

		if(!recaptchaToken.value){
			notyf.error('Please verify that you are not a robot.');
			return;
		}

		isLoading.value = true;
		  try{
		  	const response = await fetch("https://api.web3forms.com/submit", {
		  	  method: "POST",
		  	  headers: {
		  	    "Content-Type": "application/json",
		  	    Accept: "application/json",
		  	  },
		  	  body: JSON.stringify({
		  	    access_key: WEB3FORMS_ACCESS_KEY,
		  	    name: name.value,
		  	    email: email.value,
		  	    message: message.value,
		  	  }),
		  	});
		  	const result = await response.json();
		  	if (result.success) {
		  	  console.log(result);
		  	  isLoading.value = true;

		  	  notyf.success("Message Sent!");
		  	}
		  }
		  catch(error){
		  	console.log(error);

		  	isLoading.value = false;
		  	notyf.error("Failed to send a message.");
		  }
		}
</script>