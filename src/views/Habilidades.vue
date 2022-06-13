<template>
  <div v-if="!pokemon.habilidades">Selecione um pokemon</div>

  <div v-else>
    <div>
      <table class="table text-white">
        <tbody>
          <tr v-for="(habilidade, index) in pokemon.habilidades" :key="index">
            <td>{{ habilidade }}</td>
            <td class="d-flex justify-content-end">
              <button 
                type="button" 
                class="btn btn-danger btn-sm"
                @click="$emit('removerHabilidade', index)"
              >
                x
              </button>
            </td>
          </tr>
        </tbody>
      </table>
      <input
        type="text"
        class="form-control"
        placeholder="Adicionar habilidade"
        v-model="habilidade"
        @keyup.enter="adicionarHabilidade"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "Habilidades",
  props: {
    pokemon: Object,
  },

  data:()=>({
    habilidade: ""
  }),

  methods: {
    //não podemos modificar props dentro dos componentes
    adicionarHabilidade(){
      //emissao direta de um evento do compoente filho para o componente pai
      this.$emit('adicionarHabilidade', this.habilidade)
      this.habilidade = ""
    }
  }


};
</script>

<style scoped>
.table td {
  border: none;
}
</style>
