<template>
<div class="list container max-w-5xl mx-auto mt-10 mb-0 overflow-hidden rounded font-mono bg-gray-100">
	<div class="flex flex-col bg-gray-200">
		<h1 class="list-title text-center mt-5 mb-2.5 text-3xl italic">todo today</h1>
      <Form @addItem="addItem" @clearCompleted="clearCompleted" :input-value.sync="newItem"/>
    </div>
    <ul class="list-items grid gap-2.5 py-2.5 px-5">
      <Item v-for="(item, index) in items" :item-value="item" :key="`item-${index}`" @removeItem="removeItem(index)"/>
    </ul>
</div>
</template>
<script>
import Form from "./FormComponent.vue";
import Item from "./ItemComponent.vue";
export default {
  components: { Form, Item },
  data() {
    return { 
      newItem: '',
      items: []
    };
  },
methods: {
		addItem () {
      if(this.newItem){
        this.items.push(this.newItem)
        this.newItem = ''
      }
		},
    removeItem (key) {
			this.items.splice(key, 1)
		},
		clearCompleted () {
			this.items = []
		}
	}
};
</script>
<style scoped>
.list{
  height: calc(100vh - 80px);
}
</style>
