<template>
	<div class="profile-container">
		<!-- Resume Section -->
		<div class="resume-section">
			<Card
				type="std-hr"
				mini-image="https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/Gdrive.png?raw=true"
				primary-image="https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/Resume.png?raw=true"
				heading="Saifuddin Saifee Resume"
				subheading="drive.google.com"
				link="https://bit.ly/saifeecv"
			/>
		</div>

		<!-- Contact Section -->
		<div class="contact-section">
			<Card type="slim-hr" heading="+91 83087 97952" link="tel:+918308797952" mini-image="https://raw.githubusercontent.com/SaifuddinSaifee/ssaifee/a3a89336fc8e021be3ee36db2270a01f7baae01c/src/assets/call.svg"/>
			<Card
				type="slim-hr"
				heading="saifeesaifuddinq@gmail.com"
        link="mailto:saifeesaifuddinq@gmail"
				class="email-card"
        mini-image="https://raw.githubusercontent.com/SaifuddinSaifee/ssaifee/a3a89336fc8e021be3ee36db2270a01f7baae01c/src/assets/mail.svg"
			/>
		</div>

		<!-- Location Section -->
		<div class="location-section">
			<Card
				type="std-hr"
        mini-image="https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/maps-logo.png?raw=true"
				primary-image="https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/maps.png?raw=true"
				heading="Dhule, Maharashtra, India"
				subheading="maps.google.com"
        link="https://maps.app.goo.gl/drqdUQcC8CEjBzLA8"
			/>
		</div>

		<!-- Social Links Section -->
		<div class="social-section">
			<Card
				type="sqr-m"
				mini-image="https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/linkedin.png?raw=true"
				heading="Saifuddin's LinkedIn"
				subheading="linkedin.com"
				link="https://www.linkedin.com/in/saifuddinsaifee/"
			/>
			<Card
				type="sqr-m"
				mini-image="https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/Notion.png?raw=true"
				heading="Saifuddin blogs"
				subheading="Saifuddins Content Writing Work"
				link="https://bit.ly/saifeewrites"
			/>
		</div>

		<!-- GitHub Section -->
		<div class="github-section">
			<Card
				type="std-hr"
				mini-image="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg"
				primary-image="https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/ghgrid.png?raw=true"
				heading="Saifuddin Saifee"
        subheading="github.com"
				link="https://github.com/Saifuddinsaifee"
			/>
		</div>

		<!-- Articles Section -->
		<div class="articles-section">
			<Card
				v-for="article in articles"
				:key="article.title"
				type="slim-hr"
				:mini-image="article.miniImage"
				:heading="article.title"
				:link="article.link"
			/>
		</div>

		<!-- Social Media Section -->
		<div class="social-media-section">
			<Card
				type="sqr-m"
				mini-image="https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/x-logo.png?raw=true"
				heading="@SaifSaifee_dev"
				subheading="x.com"
				link="https://x.com/SaifSaifee_dev"
			/>
			<Card
				type="sqr-m"
				mini-image="https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/insta-logo.png?raw=true"
				heading="@saifsaifee._"
				subheading="instagram.com"
				link="https://www.instagram.com/saifsaifee._/"
			/>
		</div>
	</div>
</template>

<script setup lang="ts">
import Card from "./Card.vue";

const articles = [
	{ title: "All you need to know about DevOps", miniImage: "https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fthepracticaldev.s3.amazonaws.com%2Fi%2F78hs31fax49uwy6kbxyw.png", link: "https://dev.to/saifuddinsaifee/devops-simplified-for-beginners-5bdb"},
	{ title: "Git and Version Control: A Beginner's Guide to Smarter Coding", miniImage: "https://github.com/SaifuddinSaifee/ssaifee/blob/main/src/assets/Hashnode.png?raw=true", link: "https://saifsaifee.hashnode.dev/git-and-version-control-for-beginners"},
];
</script>

<style scoped>
.profile-container {
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	gap: 12px;
	max-width: 1200px;
	margin: 0 auto;
	padding: 24px;
	box-sizing: border-box;
	min-width: 872px;
	max-width: 872px;
}

/* Resume section - spans 2 columns */
.resume-section {
	grid-column: span 2;
}

/* Contact section - vertical stack of slim cards */
.contact-section {
	grid-column: span 2;
	display: flex;
	flex-direction: column;
	gap: 12px
}

/* Location section - spans 2 columns */
.location-section {
	grid-column: span 2;
}

/* Social links section - 2 square cards side by side */
.social-section {
	grid-column: span 2;
	display: flex;
	gap: 12px;
}

/* GitHub section - spans 2 columns */
.github-section {
	grid-column: span 2;
}

/* Articles section - vertical stack */
.articles-section {
	grid-column: span 2;
	display: flex;
	flex-direction: column;
	gap: 12px
}

/* Social media section - 2 square cards side by side */
.social-media-section {
	grid-column: span 2;
	display: flex;
	gap: 12px;
}

/* Email card with accent color */
.email-card {
	background-color: #1493dc;
	color: white;
}

.email-card:hover {
	background-color: #0f85c9;
	color: white;
}

/* Responsive adjustments */
@media (max-width: 1024px) {
	.profile-container {
		grid-template-columns: repeat(2, 1fr);
	}

	.resume-section,
	.contact-section,
	.location-section,
	.social-section,
	.github-section,
	.articles-section,
	.social-media-section {
		grid-column: span 2;
	}
}

@media (max-width: 640px) {
	.profile-container {
		grid-template-columns: 1fr;
	}

	.resume-section,
	.contact-section,
	.location-section,
	.social-section,
	.github-section,
	.articles-section,
	.social-media-section {
		grid-column: 1;
	}

	.social-section,
	.social-media-section {
		flex-direction: column;
	}

	.profile-container {
		padding: 12px;
		gap: 12px
	}
}
</style>
