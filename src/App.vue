<script setup>
import { ref } from 'vue';
  const listNama = ref(
    [
      "ikrar",
      "anto",
      "rian",
    ]
  )

  const tampil = ref(false)

  function clickTampil(){
    tampil.value = !tampil.value
  }

  console.log("coba saja dulu ini")
</script>
<template>
  <main>
    <h1>Belajar List tanpa lihat source apapun</h1>
    <button @click="clickTampil">Tampilkan Nama-nama yang tersedia</button>
    <ul v-for="val, i in listNama  " v-if="tampil">
      <li>no. {{ i+1 }} adalah {{ val }}</li>
    </ul>
  </main>
</template>

