<script setup>
import { ref } from 'vue';

  const nama = ref(false)

  const listNama = ref([
    "ikrar",
    "tanti",
    "selvi",
  ])

  const friends = ref(
    [
      "adam",
      "sarif",
      "asrul",
      "almin",
      "vito",
    ]
  )

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

    <h2>List Friends</h2>
    <ul v-for="(item, i) in friends">
      <li>no. {{ i+1 }} - {{ item }}</li>
    </ul>

    <br>
    <button v-on:click="tampil">Ubah Nilai</button>
    <!-- // bisa juga begini -->
    <!-- <button v-on:click="tampil" >{{ nama }}</button> -->

  </main>
</template>