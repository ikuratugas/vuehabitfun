<script setup>
import { ref } from 'vue';

  let idnya = 0

  const listNama = ref([
    {id: idnya++, nama: "ikura"},
    {id: idnya++, nama: "sensei farchan"},
    {id: idnya++, nama: "senpai rahmat"},
  ])

  const tampungText = ref("")

  function tambahListNama(){
    if (tampungText.value === ""){
      console.log("mohon masukkan nama lain")
      return null
    }
    listNama.value.push({id: idnya++, nama: tampungText.value})
  }

  function hapusListNama(id){
    // listNama.value = listNama.value.filter((t) => t.id !== id.id) // bisa juga gini kok
    listNama.value = listNama.value.filter((t) => t !== id)
  }

</script>
<template>
  <main>
    <input type="text" v-model="tampungText">
    <button @click="tambahListNama" type="button">Tambah Data</button>
    <ul v-for="i in listNama" :key="listNama.id">
      <li> {{ i.nama }}</li>
      <button @click="hapusListNama(i)">Hapus</button>
    </ul>
  </main>
</template>

