<script setup>
import { ref } from 'vue';

  const nilai = ref(0);
  

  function tambah(){
    nilai.value+=1
  }

  function kurang(){
    nilai.value-=1
  }
</script>
<template>
  <main>
    <h1>Mencoba membuat counter tanpa melihat sumber lain, just coding</h1>
    <button @click="tambah"> Tambah </button> 
    <p>{{ nilai }}</p>
    <button @click="kurang"> Tambah </button> 
  </main>
</template>

