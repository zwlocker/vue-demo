<script setup>
import { ref, onMounted } from 'vue'
import OpenBookTemplate from './OpenBookTemplate.vue'

const cats = ref([])
const featuredCat = ref(null)

onMounted(async () => {
  const res = await fetch('https://api.thecatapi.com/v1/images/search?limit=10')
  cats.value = await res.json()
  featuredCat.value = cats.value[0]
})
</script>

<template>
  <div class="pattern">
    <OpenBookTemplate>
      <template #left>
        <div class="left-inner">
          <p class="page-label">Vue Cat-alog</p>
          <div class="thumbnails">
            <button
              v-for="cat in cats"
              v-bind:key="cat.id"
              type="button"
              class="thumb"
              v-on:click="featuredCat = cat"
            >
              <img :src="cat.url" alt="" />
            </button>
          </div>
        </div>
      </template>
      <template v-slot:right>
        <div v-if="featuredCat" class="featured">
          <img v-bind:src="featuredCat.url" alt="Featured cat" />
          <p class="caption">Featured Cat</p>
        </div>
      </template>
    </OpenBookTemplate>
  </div>
</template>

<style scoped>
.pattern {
  min-height: 100vh;
  position: relative;
  background-color: #dacbb6;
  background-image: url('https://i.imgur.com/m5Mig5o.png');
}

.left-inner {
  height: 100%;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.page-label {
  margin: 0;
  font-family: Georgia, 'Times New Roman', serif;
  font-size: 2rem;
  color: #5c5348;
  text-align: center;
}

.thumbnails {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-left: 40px;
  padding: 6px;
  overflow: visible;
}

.thumb {
  position: relative;
  z-index: 0;
  padding: 0;
  border: none;
  cursor: pointer;
  background: transparent;
  overflow: visible;
  line-height: 0;
}

.thumb:hover {
  z-index: 2;
}

.thumb img {
  box-sizing: border-box;
  width: 88px;
  height: 88px;
  object-fit: cover;
  display: block;
  border: 2px solid #8b7d72;
  cursor: pointer;
  transform-origin: center;
  transition:
    transform 0.22s ease,
    border-color 0.22s ease;
}

.thumb img:hover {
  border-color: #5c5348;
  transform: scale(1.12);
}

.featured {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  overflow: visible;
  padding: 12px;
}

.featured img {
  max-width: 100%;
  width: 300px;
  max-height: 420px;
  height: auto;
  object-fit: cover;
}

.caption {
  margin: 0;
  font-family: system-ui, sans-serif;
  font-size: 1.3rem;
  color: #3a3428;
}
</style>
