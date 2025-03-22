<script setup>
import { computed, ref } from 'vue';

  let keyid = 0
  const listNama = ref([
    {id: keyid++ ,nama : "ikrar aprianto", centang: false},
    {id: keyid++, nama : "sensi farchan", centang: false},
    {id: keyid++, nama : "senpai rahmat fahmi", centang: false},
	])

  const tampungText = ref("")
  const textDiIsiKosong = ref(false)
  const tampilkanSemuDatLisNama = ref(true)

  function tambahData(){
    if(tampungText.value === ""){
      textDiIsiKosong.value = true
      return null
    }
    listNama.value.push({id: keyid++, nama:tampungText.value, centang: false})
    tampungText.value = ""
  }

  let dataFilterListNama = computed(() => {
    return tampilkanSemuDatLisNama.value ?
      listNama.value.filter((t) => t.centang === false):
      listNama.value;
  })

  function merubahNilai(){
    tampilkanSemuDatLisNama.value = !tampilkanSemuDatLisNama.value
  }
  
  function hapusData(i){
    listNama.value = listNama.value.filter((item)=> item.id !== i)
  }

</script>

<template>

  <main>
    <h1>Coba membuat CRUD</h1>
    <input type="text" v-model="tampungText" placeholder="Masukkan Nama">
    <button v-on:click="tambahData">tambah data</button>

	<ul>
		<li v-for="item in dataFilterListNama" :key="item.id">
      <input type="checkbox" v-model="item.centang">
      <span :class="{tercentang: item.centang}">
        {{ item.nama }}
      </span>
      <button v-on:click="hapusData(item.id)">X</button>
		</li>
	</ul>
  <button v-on:click="merubahNilai">
    {{ tampilkanSemuDatLisNama? "Tampilkan semua" : "Tampilkan Belum Tercentang" }}
  </button>
  </main>

</template>

<style>

.tercentang {
  color: green;
  text-decoration: line-through;
}

</style>
