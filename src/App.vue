<script setup>
import { ref } from 'vue';

  let nama = ref("ikrar aprianto")

  function tampil(){
    console.log("tampilkan saja dulu")
  }

</script>

<template>
  <h1>Belajar ulang lagi, suka pemprograman</h1>
  <main>
    <h2>coba saja dulu {{ nama }}</h2>
    <br>
    <button @click="tampil">{{ nama }}</button>
  </main>
</template>

