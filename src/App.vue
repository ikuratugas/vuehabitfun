<script setup>
import { ref } from 'vue';
  const inputNama = ref("")

<<<<<<< HEAD
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
=======
  const tampilkan = ref(false)

  function tampil(){
    tampilkan.value = true
>>>>>>> coba

    setTimeout(function(){
      tampilkan.value = false
    }, 3000)

  }
</script>

<template>
  <h1>Belajar ulang lagi, suka pemprograman</h1>
  <main>
<<<<<<< HEAD
=======
    <input v-model="inputNama" type="text" name="" id="">
    <br>
    <button @click="tampil">Tampilkan nama</button>

    <h2 v-if="tampilkan">
      Hai, {{ inputNama  }}👋
    </h2>

  </main>
</template>
>>>>>>> coba

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