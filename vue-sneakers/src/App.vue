<script setup>
import MyHello from './components/MyHello.vue'
</script>

<template>
  <MyHello title="Puma sneakers" :price="9500" is-added />
  <MyHello />
  <MyHello />
  <MyHello />
</template>
