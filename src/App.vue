<script setup>
import { ref } from 'vue';

  let nama = ref(false)

  function tampil(){
    nama.value = !nama.value 
  }

</script>

<template>
  <h1>Belajar ulang lagi, suka pemprograman</h1>
  <main>
    <h2>coba saja dulu {{ nama }}</h2>
    <br>

    <button @click="tampil" >{{ nama }}</button>
    <!-- // bisa juga begini -->
    <!-- <button v-on:click="tampil" >{{ nama }}</button> -->

  </main>
</template>

