<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'
import CardList from '../components/CardList.vue'
import InfoBlock from '../components/InfoBlock.vue'

const favorites = ref([])
const isLoading = ref(true)

onMounted(async () => {
  try {
    isLoading.value = true;

    const { data } = await axios.get(
      'https://6ce4eca66bb84e30.mokky.dev/favorites?_relations=items'
    )

    favorites.value = data.map((obj) => obj.item)
  } catch (err) {
    console.error(err)
  } finally {
    isLoading.value = false
  }
})
</script>

<template>
  <div>
    <h2 class="text-3xl font-bold mb-8">
      My Favorites ❤️
    </h2>

    <InfoBlock
      v-if="isLoading"
      title="Loading Favorites..."
      image-url="/loader.png"
    />

    <CardList 
      v-else-if="favorites.length > 0" 
      :items="favorites" 
      is-favorites
    />

    <InfoBlock
      v-else
      title="No Favorites Yet"
      description="Explore our collection and add some kicks to your favorites!"
      image-url="/emoji-1.png"
    />
  </div>
</template>
