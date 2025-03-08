<script setup>
import { ref } from 'vue';

  let nama = ref(false)

  let listNama = ref([
    "ikrar",
    "tanti",
    "selvi",
  ])

  function tampil(){
    nama.value = !nama.value
  }

</script>

<template>
  <h1>Belajar ulang lagi, suka pemprograman</h1>
  <main>

    <h2 v-if="nama === true">Ini jadi Benar</h2>
    <h2 v-else>Ini jadi salah</h2>

    <h3 v-if="nama === true">
      <ul v-for="l in listNama">
        <li>nama : {{ l }}</li>
      </ul>
    </h3>

    <br>
    <button v-on:click="tampil">Ubah Nilai</button>
    <!-- // bisa juga begini -->
    <!-- <button v-on:click="tampil" >{{ nama }}</button> -->

  </main>
</template>

