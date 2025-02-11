<script setup>
import { ref, onMounted } from 'vue'

const gifts = ref([])

onMounted(async () => {
  // ...fetch logic from index.html...
  console.log("fDSFAJSDA FK")
  const response = await fetch('https://api.sheety.co/f5ed5f784cefe4bd415ae1dd167760ae/listeMariageNoéEtMarine/feuille1');
  const data = await response.json();
  gifts.value = data.feuille1;
})
</script>

<template>
  <div v-if="!gifts.length">
    Chargement des cadeaux...
  </div>
  <div v-else class="my-8">
    <div class="flex flex-row gap-4 flex-wrap justify-baseline ">
      <div v-for="(gift, index) in gifts" :key="index" class="gift-card">
        <img v-if="gift.imageUrl" :src="gift.imageUrl" :alt="gift.name" class="gift-image" />
        <div v-else class="gift-image bg-[#295264]"></div>
        <div class="p-4">
          <h3>{{ gift.name }}</h3>
          <p>{{ gift.description }}</p>
          <p class="price">Prix : CHF {{ gift.price }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.gift-card {
  /* border: 1px solid #ccc; */
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(180, 82, 80, 0.3);
  max-width: 300px;
  width: 300px;
}
.gift-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-bottom: 1px solid #ddd;
  margin-bottom: 8px;
}
.price {
  font-weight: bold;
}
</style>