<template>
	<!-- Projects -->
	<section id="projects" class="py-5">
	  <div class="container">
	    <h2 class="text-center mb-5">My Projects</h2>
	    <div class="row g-4">

	       <!-- Project Card: E-commerce App -->
	       <div class="col-md-4">
	       	<a href="http://zuitt-bootcamp-prod-582-9211-lavaro.s3-website.us-east-1.amazonaws.com/" target="_blank">
	         <div class="project-card">
	           <img src="/images/e-com app.webp" alt="E-commerce App">
	           <div class="project-content">
	             <h3>E-commerce App</h3>
	             <p class="short-desc">Sample online shopping app.</p>
	             <p class="long-desc">A demo e-commerce application with product listings, shopping cart, and secure checkout flow. Designed to showcase frontend and backend integration.</p>
	           </div>
	         </div>
	    	   </a>
	       </div>

	      <!-- Project Card: Wuxia-Themed E-Commerce -->
	      <div class="col-md-4">
	      	<a href="https://home-page-exam-mu.vercel.app/" target="_blank">
	        <div class="project-card">
	          <img src="/images/frontendEcommerce.png" alt="Wuxia-Themed E-Commerce">
	          <div class="project-content">
	            <h3>Wuxia E-Commerce</h3>
	            <p class="short-desc">Static wuxia-themed online store.</p>
	            <p class="long-desc">
	              Created a visually immersive static e-commerce website using HTML, CSS, and Bootstrap. Focused on product display, responsive layout, and user navigation, inspired by wuxia aesthetics to enhance engagement.
	            </p>
	          </div>
	        </div>
	      	</a>
	      </div>

	      <!-- Project Card: Course Booking -->
	      <div class="col-md-4">
	      	<a href="https://course-booking-roan.vercel.app/" target="_blank">
	        <div class="project-card">
	          <img src="/images/e-book app.png" alt="Course Booking App">
	          <div class="project-content">
	            <h3>Course Booking App</h3>
	            <p class="short-desc">Web app for booking online courses.</p>
	            <p class="long-desc">An intuitive booking system where users can browse, enroll, and manage online courses. Built with a responsive UI and secure backend APIs.</p>
	          </div>
	        </div>
	       </a>
	      </div>

	      <!-- Project Card: Movie Catalog App -->
	      <div class="col-md-4">
	      	<a href="https://movie-app-eight-gules.vercel.app/" target="_blank">
	        <div class="project-card">
	          <img src="/images/movieApp.jpg" alt="Movie Catalog Application">
	          <div class="project-content">
	            <h3>Movie Catalog Application</h3>
	            <p class="short-desc">Full-stack movie search and watchlist app.</p>
	            <p class="long-desc">
	              Developed a MEVN stack application with Node/Express and MongoDB backend, and Vue.js + Bootstrap frontend. Integrated external movie APIs allowing users to search, browse, and save favorite movies. Implemented user authentication and personalized watchlists.
	            </p>
	          </div>
	        </div>
	      	</a>
	      </div>

	      <!-- Project Card: Fitness Tracker -->
	      <div class="col-md-4">
	      	<a href="https://fitness-app-xi-pearl.vercel.app/" target="_blank">
	        <div class="project-card">
	          <img src="/images/fitnessApp.webp" alt="Fitness Tracker App">
	          <div class="project-content">
	            <h3>Fitness Tracker</h3>
	            <p class="short-desc">Track workouts and monitor progress.</p>
	            <p class="long-desc">
	              Full-stack MEVN application for logging and tracking workouts. Backend RESTful API built with Node/Express and MongoDB to store workout data. Vue.js frontend with Bootstrap provides real-time statistics, progress tracking, and an intuitive user interface.
	            </p>
	          </div>
	        </div>
	      	</a>
	      </div>

	      <!-- Project Card: Job Tracker -->
	      <div class="col-md-4">
	      	<a href="https://job-tracker-client-gold.vercel.app/login" target="_blank">
	        <div class="project-card">
	          <img src="/images/jobApp.jpg" alt="Job Tracker App">
	          <div class="project-content">
	            <h3>Job Tracker</h3>
	            <p class="short-desc">Manage job applications efficiently.</p>
	            <p class="long-desc">
	              MEVN stack application for tracking job applications. Backend API with Node/Express and MongoDB stores job posts, application statuses, and deadlines. Vue.js + Bootstrap frontend features job filtering, status updates, and user-friendly navigation.
	            </p>
	          </div>
	        </div>
	      	</a>
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