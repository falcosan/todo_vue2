<template>
<li class="item flex items-center justify-between border-b-2">
  <div class="item-core flex items-center">
    <input class="item-control mr-2.5 cursor-pointer" type="checkbox" @click="setChecked($event)" :checked="checked">
    <h1 :class="`item-value ${checked ? 'line-through italic' : ''}`" v-text="itemValue" />
  </div>
  <span class="item-action text-3xl transform rotate-45 cursor-pointer transition hover:scale-110 text-red-400" @click="$emit('removeItem')" >+</span>
</li>
</template>
<script>
export default {
  props: {
    itemValue: {
      type: String,
      required: true
    },
  },
  data(){
    return{
      checked: false
    }
  },
    methods :{
      setChecked(event) {
      if (event.target.checked) {
        this.checked = true
        
      } else {
         this.checked = false 
      }
    },
  }
}
</script>

