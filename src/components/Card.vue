<!-- Card.vue -->
<template>
	<component
		:is="link ? 'a' : 'div'"
		:href="link"
		:target="link ? '_blank' : null"
		:rel="link ? 'noopener noreferrer' : null"
		:class="[
			'card',
			cardSizeClass,
			orientationClass,
			{ 'card--link': link },
		]"
		:style="cardStyles"
		@click="handleClick"
	>
		<!-- Right/Top Section -->
		<div
			v-if="hasRightSection"
			:class="[
				'card__content',
				{
					'card__content--slim': isSlim,
					'card__content--full': !hasPrimaryImage,
				},
			]"
		>
			<!-- Mini Image -->
			<img
				v-if="miniImage"
				:src="miniImage"
				:alt="miniImageAlt"
				class="card__mini-image"
				@error="handleImageError('mini')"
			/>

			<!-- Description -->
			<div v-if="heading || subheading" class="card__description">
				<h3 v-if="heading" class="card__heading">{{ heading }}</h3>
				<p v-if="subheading" class="card__subheading">
					{{ subheading }}
				</p>
			</div>
		</div>

		<!-- Left/Bottom Section -->
		<div
			v-if="primaryImage"
			:class="[
				'card__primary-image-container',
				{ 'card__primary-image-container--full': !hasRightSection },
			]"
		>
			<img
				:src="primaryImage"
				:alt="primaryImageAlt"
				class="card__primary-image"
				@error="handleImageError('primary')"
			/>
		</div>
	</component>
</template>

<script>
// Card size configurations
const CARD_SIZES = {
	"std-hr": { width: 390, height: 175 },
	"std-vr": { width: 175, height: 390 },
	"slim-hr": { width: 390, height: 68 },
	"slim-vr": { width: 68, height: 390 },
	"sqr-l": { width: 390, height: 390 },
	"sqr-m": { width: 175, height: 175 },
	"sqr-s": { width: 68, height: 68 },
};

export default {
	name: "Card",

	props: {
		// Card type from predefined sizes
		type: {
			type: String,
			validator: (value) => Object.keys(CARD_SIZES).includes(value),
			required: true,
		},
		// Images
		miniImage: {
			type: String,
			default: "",
		},
		miniImageAlt: {
			type: String,
			default: "Mini image",
		},
		primaryImage: {
			type: String,
			default: "",
		},
		primaryImageAlt: {
			type: String,
			default: "Primary image",
		},
		// Content
		heading: {
			type: String,
			default: "",
		},
		subheading: {
			type: String,
			default: "",
		},
		// Link
		link: {
			type: String,
			default: "",
		},
	},

	emits: ["click", "imageError"],

	computed: {
		// Determine if card has right section content
		hasRightSection() {
			return this.miniImage || this.heading || this.subheading;
		},

		// Determine if card has primary image
		hasPrimaryImage() {
			return !!this.primaryImage;
		},

		// Determine if card is slim type
		isSlim() {
			return this.type.includes("slim");
		},

		// Determine if card is vertical
		isVertical() {
			return this.type.includes("vr");
		},

		// Get card size class
		cardSizeClass() {
			return `card--${this.type}`;
		},

		// Get orientation class
		orientationClass() {
			return this.isVertical ? "card--vertical" : "card--horizontal";
		},

		// Calculate card styles based on type
		cardStyles() {
			const size = CARD_SIZES[this.type];
			return {
				minWidth: `${size.width}px`,
				maxWidth: `${size.width}px`,
				minHeight: `${size.height}px`,
				maxHeight: `${size.height}px`,
			};
		},
	},

	methods: {
		// Handle card click
		handleClick(event) {
			// Only emit click event if card is not a link
			if (!this.link) {
				this.$emit("click", event);
			}
		},

		// Handle image load errors
		handleImageError(type) {
			this.$emit("imageError", {
				type,
				message: `Failed to load ${type} image`,
			});
		},
	},
};
</script>

<style scoped>
/* Base card styles */
.card {
	display: flex;
	justify-content: space-between;
	padding: 24px;
	background: #ffffff;
	border-radius: 24px;
	font-family: "Inter", sans-serif;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
	border: 1px solid rgba(0, 0, 0, 0.1);
	overflow: hidden;
	transition: 300ms;
	box-sizing: border-box;
	text-decoration: none; /* Remove underline from links */
	color: inherit; /* Inherit text color */
    margin: 24px;
}

/* Link-specific styles */
.card--link {
	cursor: pointer;
}

.card--link:hover {
	background: rgba(0, 0, 0, 0.02);
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0);
}

/* Orientation variants */
.card--vertical {
	flex-direction: column;
}

.card--horizontal {
	flex-direction: row;
}

/* Content section */
.card__content {
	display: flex;
	flex-direction: column;
	gap: 12px;
	flex-shrink: 0;
	width: 45%;
}

.card__content--full {
	width: 100%;
}

.card__content--slim {
	flex-direction: row;
	align-items: center;
}

/* Mini image */
.card__mini-image {
	width: 40px;
	height: 40px;
	object-fit: cover;
	border-radius: 8px;
	margin-right: 8px;
	flex-shrink: 0;
    border: 1px solid rgba(0, 0, 0, 0.1);
    background-color: white;
}

/* Description */
.card__description {
	display: flex;
	flex-direction: column;
	gap: 4px;
}

.card__heading {
	font-size: 1rem;
	font-weight: 500;
	color: inherit;
	margin: 0;
}

.card__subheading {
	font-size: 0.75rem;
	font-weight: 400;
	color: inherit;
	margin: 0;
}

/* Primary image container */
.card__primary-image-container {
	flex: 1;
	overflow: hidden;
	max-width: 55%;
}

.card__primary-image-container--full {
	max-width: 100%;
}

.card__primary-image {
	width: 100%;
	height: 100%;
	object-fit: cover;
	border-radius: 10px;
}

/* Vertical card adjustments */
.card--vertical .card__content {
	width: 100%;
	margin-bottom: 12px;
}

.card--vertical .card__primary-image-container {
	max-width: 100%;
	flex: 1;
}
</style>
