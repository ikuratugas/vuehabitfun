<script setup>
import { ref } from 'vue';

  let idnya = 0
  const tampungText = ref("")
  const tampilkanMasukkanNama = ref(false)
  const tampilkanBelumCentang= ref(false)

  const listNama = ref([
    {id: idnya++, nama: "ikura", checked: true},
    {id: idnya++, nama: "sensei farchan", checked: false},
    {id: idnya++, nama: "senpai rahmat", checked: false},
  ])


  // ** BELUM PAHAM APA BEDANYA DENGAN COMPUTED() PADAHAL BISA JUGA BEGEINI
  // function listNamaBelumCentang ()  {
  //   return tampilkanBelumCentang.value ?
  //     listNama.value.filter((t) => !t.checked):
  //     listNama.value
  // }

  const listNamaBelumCentang = computed(() => {
    return tampilkanBelumCentang.value ?
      listNama.value.filter((t) => !t.checked):
      listNama.value
  })

  function tambahListNama(){
    if (tampungText.value === ""){
      console.log("mohon masukkan nama")
      tampilkanMasukkanNama.value = true
      return null
    }

    listNama.value.push({id: idnya++, nama: tampungText.value, checked: false})
    tampilkanMasukkanNama.value = false
    tampungText.value = ""
  }

  function hapusListNama(id){
    // listNama.value = listNama.value.filter((t) => t.id !== id.id) // bisa juga gini kok
    // listNama.value = listNama.value.filter((t) => t !== id) // other alternatif
    listNama.value = listNama.value.filter(function (t) {
      return t !== id
    })
  }

</script>
<template>
  <main>
    <form @submit.prevent="tambahListNama">
      <input type="text" v-model="tampungText">
      <p v-if="tampilkanMasukkanNama">Gagal menambahkan! Jangan kosongkan field-nya</p>
      <button @click="tambahListNama" type="button">Tambah Data</button>
    </form>
    <br>

    <ul>
      <!-- masih belum apa bedanya computed dan function biasa saja ini -->
      <!-- <li v-for="todo in (listNamaBelumCentang())" :key="todo.id"> -->
      <li v-for="todo in (listNamaBelumCentang)" :key="todo.id">
      <input type="checkbox" v-model="todo.checked">
      <span :class="{ tercentang: todo.checked}">{{ todo.nama}}</span>
      <button @click="hapusListNama(todo)">X</button>
    </li>
  </ul>
    <br>
    <button @click="tampilkanBelumCentang = !tampilkanBelumCentang">{{ tampilkanBelumCentang ?  "Semua" : "Sembunyikan selesai"}}</button>
  </main>
</template>

<style>
  .tercentang{
    font-style: italic;
    text-decoration: line-through;
  }
</style>


