<template>
	<!-- Navbar -->
	<nav class="navbar navbar-light navbar-expand-lg bg-body-tertiary px-5">
	    <div class="container-fluid">
	        <a class="navbar-brand" href="#" id="logo">JAYCEE</a>
	        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
	                aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
	            <span class="navbar-toggler-icon"></span>
	        </button>
	        
	        <div class="collapse navbar-collapse" id="navbarNav">
	            <ul class="navbar-nav ms-auto">
	                <li class="nav-item"><a class="nav-link" href="#landing">Home</a></li>
	                
	                <!-- Dropdown for Projects -->
	                <li class="nav-item dropdown">
	                    <a class="nav-link dropdown-toggle" href="#projects" id="navProjectdrop" role="button" 
	                       data-bs-toggle="dropdown" aria-expanded="false">
	                        My Projects
	                    </a>
	                    <ul class="dropdown-menu" aria-labelledby="navProjectdrop">
	                        <li><a class="dropdown-item" href="#">E-commerce API Documentation</a></li>
	                        <li><a class="dropdown-item" href="#">Course Booking API Documentation</a></li>
	                        <li><a class="dropdown-item" href="#">Course Booking App</a></li>
	                        <li><a class="dropdown-item" href="#">E-commerce App</a></li>
	                        <li><a class="dropdown-item" href="#">Airline Booking System Mockup</a></li>
	                        <li><a class="dropdown-item" href="#">Airline Booking System Prototype</a></li>
	                    </ul>
	                </li>
	                
	                <li class="nav-item"><a class="nav-link" href="#tools">Tools</a></li>
	                <li class="nav-item"><a class="nav-link" href="#contact">Contact</a></li>
	            </ul>
	        </div>
	    </div>
	</nav>
</template>