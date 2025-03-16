<script setup>
import { ref } from 'vue';
  const listNama = ref([
    "ikrar",
    "anto",
    "rian",
  ])

  const listNamaReset = ref([
    "ikrar",
    "anto",
    "rian",
  ])


  const tampil = ref(false)

  function clickTampil(){
    tampil.value = !tampil.value
  }

  function hapusList(v){
    listNama.value = listNama.value.filter((t) => t !== v)
    console.log()
    if (listNama.value.length === 0){
      listNama.value = listNamaReset.value
    }
  }

  console.log("coba saja dulu ini")
</script>
<template>
  <main>
    <h1>Belajar List tanpa lihat source apapun</h1>
    <button @click="clickTampil">Tampilkan Nama-nama yang tersedia</button>
    <ul v-for="val in listNama" :key="listNama"  v-if="tampil">
      <li>{{ val }}</li>
      <button @click="hapusList(val)">X</button>
      <br>
    </ul>
  </main>
</template>

