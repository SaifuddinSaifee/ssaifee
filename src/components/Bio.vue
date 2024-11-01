<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <div class="bio">
    <img src="../assets/saifdp.png" alt="" srcset="">
    <h1>Saifuddin Saifee</h1>
    <p>Full Stack Developer and Computer Engineering student passionate about building scalable ML applications. GitHub Campus Expert & Microsoft Learn Ambassador growing student communities. Experience with microservices, product development & cloud solutions at Psylief, SigLens & Webbrinks.</p>
  </div>
</template>

<style scoped>
.bio {
    width: 40%;
    height: fit-content;
}

img {
    width: 184px;
    border-radius: 100%;
}

h1 {
    font-size: 44px;
    font-weight: 800;
}

p {
    font-size: 20px;
    color: #565656;
    max-width: 80%;
}
</style>