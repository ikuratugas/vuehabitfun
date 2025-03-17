<script setup>
import { ref } from 'vue';

  let idnya = 0

  const listNama = ref([
    {id: idnya++, nama: "ikura", checked: false},
    {id: idnya++, nama: "sensei farchan", checked: false},
    {id: idnya++, nama: "senpai rahmat", checked: false},
  ])

  const tampungText = ref("")
  const tampilkanMasukkanNama = ref(false)

  function tambahListNama(){
    if (tampungText.value === ""){
      console.log("mohon masukkan nama")
      tampilkanMasukkanNama.value = true
      return null
    }
    listNama.value.push({id: idnya++, nama: tampungText.value})
    tampilkanMasukkanNama.value = false
  }

  function hapusListNama(id){
    // listNama.value = listNama.value.filter((t) => t.id !== id.id) // bisa juga gini kok
    listNama.value = listNama.value.filter((t) => t !== id)
  }

</script>
<template>
  <main>
    <input type="text" v-model="tampungText">
    <p v-if="tampilkanMasukkanNama">Gagal menambahkan! Jangan kosongkan field-nya</p>
    <br>
    <button @click="tambahListNama" type="button">Tambah Data</button>

    <ul v-for="i in listNama" :key="listNama.id">
      <input type="checkbox" v-model="i.checked">
      <li :class="{ tercentang: i.checked }">{{ i.nama }}</li>
      <p :class="{ tercentang: i.checked}">apa ini</p>
      <button @click="hapusListNama(i)">Hapus</button>
    </ul>
  </main>
</template>

<style>
  .tercentang{
    font-style: italic;
    text-decoration: line-through;
  }
</style>

