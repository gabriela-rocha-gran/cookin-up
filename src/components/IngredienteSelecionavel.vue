<script setup lang="ts">
import { ref } from "vue";
import Tag from "./Tag.vue";

const props = defineProps({
  ingrediente: {
    type: String,
    required: true
  }
})

const selecionado = ref(false);

const emit = defineEmits(['adicionarIngrediente', 'removerIngrediente']);

function aoClicar() {
  selecionado.value = !selecionado.value;

  if(selecionado.value) {
    emit('adicionarIngrediente', props.ingrediente)
  } else {
    emit('removerIngrediente', props.ingrediente)
  }
}

</script>

<template>
  <button
    class="ingrediente"
    @:click="aoClicar"
    :aria-pressed="selecionado"
  >
    <Tag :texto="ingrediente" :ativa="selecionado" />
  </button>
</template>

<style scoped>
.ingrediente {
  cursor: pointer;
}
</style>
