<template>
    <button class="ingrediente"
        @click="selecionado = !selecionado"
        :aria-pressed="selecionado"
    >
      <Tag :texto="ingrediente" :ativa="selecionado"/>
    </button>
</template>
   
<script lang="ts">
import { defineComponent } from 'vue';
import Tag from './Tag.vue';

export default defineComponent({
    name: 'IngredienteSelecionavel',
    data() {
      return {
        selecionado: false
      }  
    },
    props:{
        ingrediente: {type : String, required: true},
    },
    components: {Tag}
});
</script>
   
<style scoped>
   .ingrediente{
    cursor: pointer;
   }
</style>
   