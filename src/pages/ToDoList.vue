<template>
    
            <div class="field has-addons"> 
                <p class="control">
                    <input class="input" type="text" v-model="newItem" @keydown.enter="addItem()">
                </p>
                <p class="control">
                    <button class="button" @click="addItem()">Add</button>        
                </p>    
            </div>
            <div class="content">
                <item-list title="All items" v-bind:items="items"></item-list>
                <item-list title="Done items" v-bind:items="doneItems"></item-list>
                <item-list title="Not done items" v-bind:items="notDoneItems"></item-list>
                
            </div>
       
</template>

<script>
import ItemList from '../components/ItemList.vue';
export default {
  components: { ItemList },
    data(){
        return {
            newItem: '',
            count: 0,
            items: [
                {name:'piim', done: true, id: 0},
                {name:'sai', done: false, id: 1},
                {name:'viin', done: true, id: 2},
                {name:'õlu', done: false, id: 3},
            ]
        }
    },
    methods: {
        addItem(){
            if(this.newItem.trim() != ''){
                this.items.push({name:this.newItem, done: false, id: this.items.length});
            }
            this.newItem = '';
        }
    },
    computed: {
        doneItems(){
            return this.items.filter(item => item.done);
        },
        notDoneItems(){
            return this.items.filter(item => !item.done);
        },
    }
}
</script>

<style>
</style>