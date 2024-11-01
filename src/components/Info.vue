<template>
  <div class="info">
    <div class="card-grid">
      <Card
        class="item-1"
        type="std-hr"
        mini-image="https://cdn4.iconfinder.com/data/icons/logos-brands-in-colors/48/google-drive-512.png"
        primary-image="https://docs.google.com/document/d/1sVuZdmMXAvRkgfDrQvgnGrRvG_72jby53zxxbL7WCDw/edit?tab=t.0"
        heading="Resume"
        subheading="https://bit.ly/saifeecv"
        link="https://bit.ly/saifeecv"
      />
      <Card
        type="sqr-m"
        link="https://www.linkedin.com/in/saifuddinsaifee/"
        mini-image="https://upload.wikimedia.org/wikipedia/commons/c/ca/LinkedIn_logo_initials.png"
        heading="Saifuddin LinkedIn"
        subheading="linkedin.com"
      />
      <Card
        type="sqr-m"
        mini-image="https://images.pexels.com/photos/17483809/pexels-photo-17483809/free-photo-of-an-artist-s-illustration-of-artificial-intelligence-ai-this-image-represents-how-ai-accountability-is-a-strong-foundation-in-a-world-of-unpredictability-it-was-created-by-champ-panupon.png"
        heading="Resume"
        subheading="https://bit.ly/saifeecv"
      />
      <Card
        type="sqr-m"
        mini-image="https://images.pexels.com/photos/17483809/pexels-photo-17483809/free-photo-of-an-artist-s-illustration-of-artificial-intelligence-ai-this-image-represents-how-ai-accountability-is-a-strong-foundation-in-a-world-of-unpredictability-it-was-created-by-champ-panupon.png"
        heading="Resume"
        subheading="https://bit.ly/saifeecv"
      />
      <Card
        class="item-2"
        type="std-hr"
        primary-image="https://images.pexels.com/photos/17483809/pexels-photo-17483809/free-photo-of-an-artist-s-illustration-of-artificial-intelligence-ai-this-image-represents-how-ai-accountability-is-a-strong-foundation-in-a-world-of-unpredictability-it-was-created-by-champ-panupon.png"
      />
      <Card
        class="item-3"
        type="std-vr"
        mini-image="https://images.pexels.com/photos/17483809/pexels-photo-17483809/free-photo-of-an-artist-s-illustration-of-artificial-intelligence-ai-this-image-represents-how-ai-accountability-is-a-strong-foundation-in-a-world-of-unpredictability-it-was-created-by-champ-panupon.png"
        primary-image="https://images.pexels.com/photos/17483809/pexels-photo-17483809/free-photo-of-an-artist-s-illustration-of-artificial-intelligence-ai-this-image-represents-how-ai-accountability-is-a-strong-foundation-in-a-world-of-unpredictability-it-was-created-by-champ-panupon.png"
        heading="std-vr"
        subheading="https://bit.ly/saifeecv"
      />
      <Card
        type="slim-hr"
        mini-image="https://images.pexels.com/photos/17483809/pexels-photo-17483809/free-photo-of-an-artist-s-illustration-of-artificial-intelligence-ai-this-image-represents-how-ai-accountability-is-a-strong-foundation-in-a-world-of-unpredictability-it-was-created-by-champ-panupon.png"
        heading="slim-hr"
        subheading="https://bit.ly/saifeecv"
      />

      <Card
        type="sqr-m"
        primary-image="https://images.pexels.com/photos/17483809/pexels-photo-17483809/free-photo-of-an-artist-s-illustration-of-artificial-intelligence-ai-this-image-represents-how-ai-accountability-is-a-strong-foundation-in-a-world-of-unpredictability-it-was-created-by-champ-panupon.png"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import Card from './Card.vue';
</script>

<style scoped>
.info {
  width: 60%;
  max-width: 860px; /* Accommodates 4 cards of 390px width plus gaps */
  margin: 0 auto;
  padding: 24px;
  box-sizing: border-box;
}

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(390px, 1fr));
  gap: 24px;
  align-items: start;
  justify-content: center;
}

/* Responsive adjustments */
@media (max-width: 860px) {
  .card-grid {
    grid-template-columns: repeat(3, minmax(390px, 1fr));
  }
}

@media (max-width: 1320px) {
  .card-grid {
    grid-template-columns: repeat(2, minmax(390px, 1fr));
  }
}

@media (max-width: 920px) {
  .card-grid {
    grid-template-columns: minmax(390px, 1fr);
  }
}

/* Ensure no overflow on small screens */
@media (max-width: 480px) {
  .info {
    padding: 12px;
  }
  
  .card-grid {
    grid-template-columns: 1fr;
  }
}
</style>