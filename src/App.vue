<script setup>
import { ref } from 'vue';
  const inputNama = ref("")

  const tampilkan = ref(false)

  function isiText(e) {
    inputNama.value = e.target.value
  }   
  
  function tampil(){
    tampilkan.value = true

    setTimeout(function(){
      tampilkan.value = false
    }, 3000)

  }
</script>

<template>
  <h1>Belajar ulang lagi, suka pemprograman</h1>
  <main>
    <!-- <input v-model="inputNama" type="text" name="" id=""> -->
    <input type="text" :value="inputNama" @input="isiText">
    <br>
    <button @click="tampil">Tampilkan nama</button>

    <h2 v-if="tampilkan">
      Hai, {{ inputNama  }}👋
    </h2>

  </main>
</template>

