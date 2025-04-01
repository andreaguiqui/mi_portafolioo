<script>
	import { onMount } from 'svelte';
	import { faBars } from '@fortawesome/free-solid-svg-icons';

	import {
		faHtml5,
		faCss3Alt,
    	faReact,
		faVuejs,
		faNodeJs,
		faJava,
		faJsSquare,
		faGithub,
		faPython,   
		faGitlab   
	} from '@fortawesome/free-brands-svg-icons';


	import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';

	let menuOpen = false;
	function toggleMenu() {
		menuOpen = !menuOpen;
	}

	const skills = [
		{ icon: faJava, color: 'text-red-500' },
		{ icon: faGithub, color: 'text-black' },
		{ icon: faPython, color: 'text-green' },
		{ icon: faGitlab, color: 'text-orange' }
	];

	const projects = [
		{
			title: 'Password Generator',
			description: 'Made by Andrea Guillen',
			photo: '/Password_Generator.png',
			link: 'https://andreaguiqui.github.io/password-generator/'
		},
		{
			title: 'Project 2',
			description: 'Description 2',
			photo: 'https://via.placeholder.com/150',
			link: '#'
		},
		{
			title: 'Project 3',
			description: 'Description 3',
			photo: 'https://via.placeholder.com/150',
			link: '#'
		}
	];

	function handleSubmit(event){
		event.preventDefault();
		const name = document.getElementById("name").value;
		const email = document.getElementById("email").value;
		const message = document.getElementById("message").value;

		alert(`Datos del formulario recibido: \n Nombre: ${name}\nEmail: ${email}\nMessage: ${message}`)
	}
</script>

<header class="bg-opacity-80 top-0 left-0 z-50 w-full bg-white shadow-lg">
	<nav class="container mx-auto flex items-center justify-between px-6 py-4">
		<div class="hidden items-center space-x-4 md:flex">
			<a href="about-me" class="px-3 py-2 text-sm font-medium text-pink-700 hover:text-pink-900"
				>About Me</a
			>
			<a href="skills" class="px-3 py-2 text-sm font-medium text-pink-700 hover:text-pink-900"
				>Skills</a
			>
			<a href="projects" class="px-3 py-2 text-sm font-medium text-pink-700 hover:text-pink-900"
				>Projects</a
			>
			<a href="contact" class="px-3 py-2 text-sm font-medium text-pink-700 hover:text-pink-900"
				>Contact</a
			>
		</div>
		<div class="md:hidden">
			<button
				on:click={toggleMenu}
				aria-label="Open menu"
				class="text-pink-700  hover:text-pink-900 focus:outline-none"
			>
				<FontAwesomeIcon icon={faBars} class="text-2xl" />
			</button>
		</div>
	</nav>

	{#if menuOpen}
		<div class="w-full bg-white text-center shadow-md md:hidden">
			<ul class="flex cursor-pointer flex-col p-4">
				<li>
					<a
						href="about-me"
						class="px-3 py-2 text-sm font-medium text-pink-700 hover:text-pink-900">About Me</a
					>
				</li>
				<li>
					<a
						href="skills"
						class="px-3 py-2 text-sm font-medium text-pink-700 hover:text-pink-900">Skills</a
					>
				</li>
				<li>
					<a
						href="projects"
						class="px-3 py-2 text-sm font-medium text-pink-700 hover:text-pink-900">Projects</a
					>
				</li>
				<li>
					<a
						href="contact"
						class="px-3 py-2 text-sm font-medium text-pink-700 hover:text-pink-900">Contact</a
					>
				</li>
			</ul>
		</div>
	{/if}
</header>

<!--About Me-->
<section
	id="about-me"
	class="flex w-full flex-col items-center gap-8 bg-pink-200  py-20 text-white lg:flex-row"
>
	<div class="flex justify-center lg:mb-0 lg:w-1/3">
		<img
			src="/flores.jpg"
			alt="clb dev"
			class="transorm h-48 w-48 rounded-full bg-white ring-4 ring-pink-700 transition-all duration-300 hover:-translate-y-2 hover:scale-105 hover:ring-pink-500"
		/>
	</div>
	<div class="flex flex-col text-center md:text-start">
		<h1 class="mb-4 text-5xl leading-tight font-extrabold">About Me</h1>
		<p class="mt-2 mb-4 text-lg text-pink-900">Hi, my name is Andrea. I'm a student.</p>
	</div>
</section>

<!--Skills-->
<section
	id="skills"
	class="flex w-full flex-col items-center bg-white py-20 text-white lg:flex-row"
>
	<div class="container mx-auto px-6">
		<h2 class="text-center text-2xl font-bold text-pink-900">Skills</h2>
		<div class="grid grid-cols-3 place-items-center gap-6 md:grid-cols-4">
			{#each skills as skill}
				<div class="group relative w-1/2 p-6 md:w-1/4 lg:w-1/6">
					<FontAwesomeIcon
						icon={skill.icon}
						class="{skill.color} transform text-5xl transition-transform hover:scale-110"
					/>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Projects -->
<section id="projects" class="flex w-full flex-col items-center bg-pink-100 py-20 text-white">
	<h2 class="text-center text-2xl font-bold text-pink-700">Projects</h2>
	<div class="mt-6 grid w-full max-w-6xl grid-cols-1 gap-6 px-6 md:grid-cols-2 lg:grid-cols-3">
		{#each projects as project}
			<div class="rounded-lg border border-pink-300 bg-white p-4 text-center shadow-md">
				<img
					src={project.photo}
					alt={project.title}
					class="mb-4 h-32 w-full rounded-md object-cover"
				/>
				<h3 class="mb-2 text-xl font-semibold text-pink-700">{project.title}</h3>
				<p class="mb-4 text-sm text-gray-700">{project.description}</p>
				<a href={project.link} target="_blank" class="text-pink-500 hover:text-pink-700"
					>See project</a
				>
			</div>
		{/each}
	</div>
</section>
<!-- Contact Form -->
<section id="contact-form" class="py-12 bg-white">
	<div class="container mx-auto px-6 max-w-lg">
		<h2 class="text-2xl font-bold mb-6 text-pink-700 text-center">Contact</h2>
		<form class="mb-4 rounded bg-pink-100 px-8 pt-6 pb-8 shadow-md" on:submit={handleSubmit}>
			<div class="mb-4">
				<label class="mb-2 block text-sm font-bold text-pink-700" for="name">Name</label>
				<input class="shadow-md appearance-none border rounded w-full p-2 text-gray-700 focus:outline-none focus:shadow-outline" 
					id="name" type="text" placeholder="Add your name"/>
			</div>
			<div class="mb-4">
				<label class="mb-2 block text-sm font-bold text-pink-700" for="email">Email</label>
				<input class="shadow-md appearance-none border rounded w-full p-2 text-gray-700 focus:outline-none focus:shadow-outline" 
					id="email" type="email" placeholder="Add your email"/>
			</div>
			<div class="mb-4">
				<label class="mb-2 block text-sm font-bold text-pink-700" for="message">Message</label>
				<input class="shadow-md appearance-none border rounded w-full p-2 text-gray-700 focus:outline-none focus:shadow-outline" 
					id="message" type="text" placeholder="Add your message"/>
			</div>
			<div class="flex items-center justify-center">
				<button class="bg-pink-700 text-white hover:bg-indigo-900 font-bold p-4 rounded focus:outline-none focus:shadow-outline" 
					type="submit">Send</button>
			</div>
		</form>
	</div>
</section>
