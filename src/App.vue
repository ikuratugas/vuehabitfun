<script setup>
import { ref } from 'vue';

  let idnya = 0

  const listNama = ref([
    {id: idnya++, nama: "ikrar aprianto"},
    {id: idnya++, nama: "tanti ade destiani"},
    {id: idnya++, nama: "selvi"},
  ])

  function hapusListNama(id){
    // listNama.value = listNama.value.filter((t) => t.id !== id.id) // bisa juga gini kok
    listNama.value = listNama.value.filter((t) => t !== id)
  }

</script>
<template>
  <main>
    <ul v-for="i in listNama" :key="listNama.id">
      <li> {{ i.nama }}</li>
      <button @click="hapusListNama(i)">Hapus</button>
    </ul>
  </main>
</template>

