import { Text } from 'vue';

<template>
  <div class="flex flex-col p-8">

  </div>
</template>

<script setup>
import { computed,onMounted,ref } from "vue";
import axiosClient from "../axiosClient";
import store from "../store";



const ingredients = ref([])

onMounted(async ()=>{
  const response = await axiosClient.get('/list.php?i=list')
  console.log(response.data)
  ingredients.value = response.data
})

</script>
