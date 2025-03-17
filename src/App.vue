<script setup>
import { ref } from 'vue';

  let idnya = 0
  const tampungText = ref("")
  const tampilkanMasukkanNama = ref(false)
  const tampilkanBelumCentang= ref(true)

  const listNama = ref([
    {id: idnya++, nama: "ikura", checked: true},
    {id: idnya++, nama: "sensei farchan", checked: false},
    {id: idnya++, nama: "senpai rahmat", checked: false},
  ])

  function listNamaBelumCentang(){
    return tampilkanBelumCentang.value ?
      listNama.value.filter((t) => t.checked === false):
      listNama.value
  }

  function tambahListNama(){
    if (tampungText.value === ""){
      console.log("mohon masukkan nama")
      tampilkanMasukkanNama.value = true
      return null
    }

    listNama.value.push({id: idnya++, nama: tampungText.value, checked: false})
    tampilkanMasukkanNama.value = false
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
    <input type="text" v-model="tampungText">
    <p v-if="tampilkanMasukkanNama">Gagal menambahkan! Jangan kosongkan field-nya</p>
    <br>
    <button @click="tambahListNama" type="button">Tambah Data</button>

    <ul v-for="i in (listNamaBelumCentang())" :key="listNama.id">
      <li :class=" { tercentang: i.checked }">
        <input type="checkbox" v-model="i.checked">
        {{ i.nama }}
      </li>
      <button @click="hapusListNama(i)">Hapus</button>
    </ul>
    <br>
    <button @click="tampilkanBelumCentang = !tampilkanBelumCentang">{{ tampilkanBelumCentang ?  "Tutup" : "Tampilkan Semua"}}</button>
  </main>
</template>

<style>
  .tercentang{
    font-style: italic;
    text-decoration: line-through;
  }
</style>

