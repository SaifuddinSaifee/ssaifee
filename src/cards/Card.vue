<!-- Card.vue -->
<template>
	<div :class="['card-container', sizeClass]" :style="containerStyle">
		<!-- Left section with mini image, headings -->
		<div class="content-section">
			<!-- Mini image with error handling -->
			<div class="mini-image-container">
				<img
					:src="miniImage"
					:alt="miniImageAlt"
					@error="handleImageError('mini')"
					v-if="miniImage && !miniImageError"
					class="mini-image"
				/>
				<div v-else class="image-placeholder mini">
					{{
						miniImageError
							? "Mini image failed to load"
							: "No mini image"
					}}
				</div>
			</div>

			<!-- Headings -->
			<div class="headings-container">
				<h2 v-if="heading" class="heading">{{ heading }}</h2>
				<p v-if="subheading" class="subheading">{{ subheading }}</p>
			</div>
		</div>

		<!-- Right section with primary image -->
		<div class="primary-image-section">
			<img
				:src="primaryImage"
				:alt="primaryImageAlt"
				@error="handleImageError('primary')"
				v-if="primaryImage && !primaryImageError"
				class="primary-image"
			/>
			<div v-else class="image-placeholder primary">
				{{
					primaryImageError
						? "Primary image failed to load"
						: "No primary image"
				}}
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "Card",

	props: {
		// Size props with validation
		width: {
			type: Number,
			validator: (value) => [100, 200, 300, 400].includes(value),
			default: 300,
		},
		height: {
			type: Number,
			validator: (value) => [100, 200, 300, 400].includes(value),
			default: 200,
		},

		// Content props
		miniImage: {
			type: String,
			default: "",
		},
		miniImageAlt: {
			type: String,
			default: "Mini image",
		},
		heading: {
			type: String,
			default: "",
		},
		subheading: {
			type: String,
			default: "",
		},
		primaryImage: {
			type: String,
			default: "",
		},
		primaryImageAlt: {
			type: String,
			default: "Primary image",
		},
	},

	data() {
		return {
			miniImageError: false,
			primaryImageError: false,
		};
	},

	computed: {
		// Compute container styles based on props
		containerStyle() {
			return {
				width: `${this.width}px`,
				height: `${this.height}px`,
			};
		},

		// Compute size class based on dimensions
		sizeClass() {
			return `size-${this.width}-${this.height}`;
		},
	},

	methods: {
		// Handle image loading errors
		handleImageError(type) {
			if (type === "mini") {
				this.miniImageError = true;
				console.error("Mini image failed to load");
			} else {
				this.primaryImageError = true;
				console.error("Primary image failed to load");
			}
		},
	},
};
</script>

<style scoped>
.card-container {
	display: flex;
	border: 1px solid #e0e0e0;
	border-radius: 8px;
	overflow: hidden;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.content-section {
	width: 50%;
	padding: 16px;
	display: flex;
	flex-direction: column;
	gap: 12px;
}

.mini-image-container {
	width: 100%;
	height: 60px;
	overflow: hidden;
	border-radius: 4px;
}

.mini-image {
	width: 100%;
	height: 100%;
	object-fit: cover;
}

.headings-container {
	flex-grow: 1;
	display: flex;
	flex-direction: column;
	gap: 8px;
}

.heading {
	margin: 0;
	font-size: 1.25rem;
	font-weight: 600;
	color: #333;
}

.subheading {
	margin: 0;
	font-size: 0.875rem;
	color: #666;
}

.primary-image-section {
	width: 50%;
	position: relative;
}

.primary-image {
	width: 100%;
	height: 100%;
	object-fit: cover;
}

.image-placeholder {
	width: 100%;
	height: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: #f5f5f5;
	color: #666;
	font-size: 0.875rem;
	text-align: center;
	padding: 8px;
}

.image-placeholder.mini {
	height: 60px;
}

/* Responsive adjustments for small sizes */
@media (max-width: 200px) {
	.heading {
		font-size: 1rem;
	}

	.subheading {
		font-size: 0.75rem;
	}
}
</style>
