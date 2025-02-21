<template>
    <button class="ingrediente"
        @click="onClick"
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
    components: {Tag},
    methods: {
        onClick(){
            this.selecionado = !this.selecionado
            if (this.selecionado){
                this.$emit('adicionarIngrediente', this.ingrediente)
            }else{
                this.$emit('removerIngrediente', this.ingrediente)
            }
        }
    },
    emits:['adicionarIngrediente', 'removerIngrediente']
});
</script>
   
<style scoped>
   .ingrediente{
    cursor: pointer;
   }
</style>
   