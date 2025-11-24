<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import Card from '../components/Card.vue'

defineProps({
  id: Number,
  title: String,
  imageUrl: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickFavorite: Function,
  onClickAdd: Function,
})

const favorites = ref([]);
// const emit = defineEmits(['addToCart']);

onMounted(async () => {
  try {
    const { data } = await axios.get('https://fa58b7fdb36d538b.mokky.dev/favorites');
    favorites.value = data;
  } catch (err) {
    console.log(err);
  }
});
</script>

<template>
  <h2 class="text-3xl font-bold mb-8">Мои закладки</h2>

  <div class="grid grid-cols-4 gap-5" v-auto-animate>
    <Card
      v-for="fav in favorites"
      :key="fav.item.id"
      :id="fav.item.id"
      :title="fav.item.title"
      :imageUrl="fav.item.imageUrl"
      :price="fav.item.price"
      :isFavorite="fav.item.isFavorite"
      :isAdded="fav.item.isAdded"
      :onClickFavorite="() => emit('addToFavorite', fav.item)"
      :onClickAdd="() => emit('addToCart', fav.item)"
    />
  </div>
</template>
