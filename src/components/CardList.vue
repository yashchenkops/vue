<script setup>
import Card from './Card.vue'

const onClickAdd = () => {
  alert(111);
}
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      title="Мужские кроссовки Nike Mid Suede"
      imageUrl="/sneakers/sneakers-1.jpg"
      :price="3250"
      :isAdded="false"
      :isFavorite="false"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
