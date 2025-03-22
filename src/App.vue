<script setup>
import { ref } from 'vue';

  let keyid = 0
  const listNama = ref([
    {id: keyid++ ,nama : "ikrar aprianto", centang: false},
    {id: keyid++, nama : "sensi farchan", centang: false},
    {id: keyid++, nama : "senpai rahmat fahmi", centang: false},
	])
  // TODO: buat input tambah data
  const tampungText = ref("")

</script>

<template>

  <main>
    <h1>Coba membuat CRUD</h1>
    <input type="text" v-model="tampungText" placeholder="Masukkan Nama">


	<ul>
		<li v-for="item in listNama" :key="item.id">
      <input type="checkbox" v-model="item.centang">
      <span :class="{tercentang: item.centang}">
        {{ item.nama }}
      </span>
		</li>
	</ul>
  </main>

</template>

<style>

.tercentang {
  color: green;
  text-decoration: line-through;
}

</style>
