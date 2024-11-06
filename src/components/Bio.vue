<script setup>
import { ref } from "vue";

defineProps({
	msg: String,
});

const count = ref(0);
</script>

<template>
	<div class="bio">
		<img src="../assets/saifdp.png" alt="" srcset="" />
		<h1>Saifuddin Saifee</h1>
		<p>
			Full Stack Developer and Computer Engineering student passionate
			about building scalable ML applications. GitHub Campus Expert &
			Microsoft Learn Ambassador growing student communities. Experience
			with microservices, product development & cloud solutions at
			Psylief, SigLens & Webbrinks.
		</p>
	</div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Caveat+Brush&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");

.bio {
	width: 40%;
	height: fit-content;
}

img {
	width: 184px;
	border-radius: 100%;
}

h1 {
	font-weight: 500;
	font-style: normal;
	font-size: 44px;
	font-weight: 800;
  margin: 1rem 0;
}

p {
  margin: 0;
	font-size: 20px;
	color: #565656;
	max-width: 80%;
}
</style>
