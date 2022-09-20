<template>
  <input type="text" v-model="name">
  <button class="button" @click="items.push(name)">Add</button>  
  <ul>
      <li v-for="(item, key) in items" :key="index">{{ item }}</li>
  </ul>
</template>

<script>
export default {
       data(){
           return{
               name: 'Tori',
               count:0,
               items: ['piim','sai','viin','banana']
           }
       }
}
</script>

<style>

</style>