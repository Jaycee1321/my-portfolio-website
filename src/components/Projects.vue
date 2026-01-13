<template>
	<!-- Projects -->
	<section id="projects" class="py-5">
	  <div class="container">
	    <h2 class="text-center mb-5">My Projects</h2>
	    <div class="row g-4">
	      
	      <!-- Project Card -->
	      <div class="col-md-4">
	        <div class="project-card">
	          <img src="/images/e-com api.webp" alt="E-commerce API Documentation">
	          <div class="project-content">
	            <h3>E-commerce API Documentation</h3>
	            <p class="short-desc">API docs for a sample e-commerce platform.</p>
	            <p class="long-desc">Detailed documentation covering endpoints for authentication, product management, and checkout workflow for a scalable e-commerce system.</p>
	          </div>
	        </div>
	      </div>

	      <!-- Project Card -->
	      <div class="col-md-4">
	        <div class="project-card">
	          <img src="/images/e-book api.webp" alt="Course Booking API Documentation">
	          <div class="project-content">
	            <h3>Course Booking API Documentation</h3>
	            <p class="short-desc">Docs for a course booking API.</p>
	            <p class="long-desc">Comprehensive documentation for endpoints handling course creation, enrollment, and scheduling, ensuring clarity for developers integrating the system.</p>
	          </div>
	        </div>
	      </div>

	      <!-- Project Card -->
	      <div class="col-md-4">
	        <div class="project-card">
	          <img src="/images/e-book app.png" alt="Course Booking App">
	          <div class="project-content">
	            <h3>Course Booking App</h3>
	            <p class="short-desc">Web app for booking online courses.</p>
	            <p class="long-desc">An intuitive booking system where users can browse, enroll, and manage online courses. Built with a responsive UI and secure backend APIs.</p>
	          </div>
	        </div>
	      </div>

	      <!-- Project Card -->
	      <div class="col-md-4">
	        <div class="project-card">
	          <img src="/images/e-com app.webp" alt="E-commerce App">
	          <div class="project-content">
	            <h3>E-commerce App</h3>
	            <p class="short-desc">Sample online shopping app.</p>
	            <p class="long-desc">A demo e-commerce application with product listings, shopping cart, and secure checkout flow. Designed to showcase frontend and backend integration.</p>
	          </div>
	        </div>
	      </div>

	      <!-- Project Card -->
	      <div class="col-md-4">
	        <div class="project-card">
	          <img src="/images/airline mockup.png" alt="Airline Booking System Mockup">
	          <div class="project-content">
	            <h3>Airline Booking System Mockup</h3>
	            <p class="short-desc">UI design for flight booking.</p>
	            <p class="long-desc">A static design mockup visualizing the flow of searching flights, selecting seats, and booking tickets. Focused on clean UI and user experience.</p>
	          </div>
	        </div>
	      </div>

	      <!-- Project Card -->
	      <div class="col-md-4">
	        <div class="project-card">
	          <img src="/images/airline prototype.webp" alt="Airline Booking System Prototype">
	          <div class="project-content">
	            <h3>Airline Booking System Prototype</h3>
	            <p class="short-desc">Prototype of a flight booking app.</p>
	            <p class="long-desc">A functional prototype showcasing user journey for searching flights, selecting seats, and completing bookings, with mock data and design system.</p>
	          </div>
	        </div>
	      </div>

	    </div>
	  </div>
	</section>
</template>

<script setup>
	// computed function from Vue to define reactive derived state.
	import {computed} from 'vue';
	// card that will be reused
	import ProjectCard from './ProjectCard.vue';

	// data
	import projects from '../data/projects.json'

	// This will be used to define the number of cards per row.
	const chunkSize = 3;

	// Create a computed property that splits the projects into smaller arrays ("chunks")
	// Each chunk will contain up to the number of the 'chunkSize' number of projects.
	//This allows us to group them visually in separate rows in the UI.
	const chunkedProjects = computed(() => {
		const chunks = [];

		for( let i = 0; i < projects.length; i += chunkSize){
			chunks.push(projects.slice(i, i + chunkSize));
		}

		return chunks;
	})

</script>