import { Text } from 'vue';

<template>
  <div class="flex flex-col p-8">
    <input
      type="text"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Search For Meals"
    />

    <div class="flex justify-center gap-1 mt-2">
      <router-link :to="{name:'byLetter',params:{letter}}" v-for="letter of letters.split('')" :key="letter">
        {{ letter }}</router-link
      >
    </div>
  </div>
</template>

<script setup>
import { computed,onMounted,ref } from "vue";
import axiosClient from "../axiosClient";
import store from "../store";


const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
const ingredients = ref([])

onMounted(async ()=>{
  const response = await axiosClient.get('/list.php?i=list')
  console.log(response.data)
  ingredients.value = response.data
})

</script>
