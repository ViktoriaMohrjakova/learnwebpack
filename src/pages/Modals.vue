<template>
  <img-model v-if="active" @close="active=false" src="http://placekitten.com/800/600"></img-model>
<button class="button is-primary" @click="active=true">Open Model</button>
<img-model v-if="active2" @close="active2=false" src="https://placebear.com/800/600"></img-model>
<button class="button is-primary" @click="active2=true">Open Model</button>
<img-model v-if="active3" @close="active3=false">
   <h1>lkuyfg</h1>
</img-model>
<button class="button is-primary" @click="active3=true">Open Model</button>
</template>

<script>
import Modal from '../components/Modal.vue'
import ImgModel from '../components/ImgModel.vue'
export default {
  components: { Modal, ImgModel },
     data(){
         return{
             active: false,
             active2: false,
             active3: false
         }
     }
}
</script>

<style>

</style>