<!--
 * @Author: marineyulxl
 * @Date: 2023-04-11 22:07:20
 * @LastEditTime: 2023-04-11 22:13:42
-->
<script setup lang="ts">
  import {computed,ref} from 'vue'
  let firstName = ref('')
  let lastName = ref('')
  const name =computed(()=>{
    return firstName.value+lastName.value
  })
</script>

<template>
  <input type="text" v-model="firstName"><br>
  <input type="text" v-model="lastName">
   <div>
    {{name}}
   </div>
</template>

<style scoped>

</style>
