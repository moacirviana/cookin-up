<template>
  <main class="conteudo-principal">
    <SuaLista :ingredientes="ingredientes"/>
    <KeepAlive include="SelecionarIngredientes">
        <SelecionarIngredientes @adicionar-ingrediente="adicionarIngrediente" 
                                @remover-ingrediente="removeIngrediente" 
                                @buscar-receitas="navegar('MostrarReceitas')"
                                v-if="conteudo === 'SelecionarIngredientes'"/>
        <MostrarReceitas v-else-if="conteudo === 'MostrarReceitas'"
                  @editar-receitas="navegar('SelecionarIngredientes')"
                  :ingredientes="ingredientes"
                  />
  </KeepAlive>
  </main>
</template>


<script lang="ts">
import MostrarReceitas from './MostrarReceitas.vue';
import SelecionarIngredientes from './SelecionarIngredientes.vue';
import SuaLista from './SuaLista.vue';

type Pagina = 'SelecionarIngredientes' | 'MostrarReceitas'

export default {
  data() {
        return {
            ingredientes: [] as string[],
            conteudo: 'SelecionarIngredientes' as Pagina
        };
    },
    components: { SelecionarIngredientes, SuaLista, MostrarReceitas },
    methods:{
      adicionarIngrediente(ingrediente: string){
        this.ingredientes.push(ingrediente)
      }
        ,
        removeIngrediente : function (ingrediente: string) {
          this.ingredientes = this.ingredientes.filter(iLista => ingrediente !== iLista);
        },
        navegar(pagina: Pagina){
          this.conteudo=pagina
        }
    }
}
</script>

<style scoped>
.conteudo-principal {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #FFFAF3);
  color: var(--cinza, #444);

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}

@media only screen and (max-width: 1300px) {
  .conteudo-principal {
    padding: 5rem 3.75rem;
    gap: 3.5rem;
  }
}

@media only screen and (max-width: 767px) {
  .conteudo-principal {
    padding: 4rem 1.5rem;
    gap: 4rem;
  }
}
</style>
