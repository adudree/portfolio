<script setup lang="ts">
import { ref, watch } from 'vue';
import MenuBtn from './MenuBtn.vue';

defineProps<{
  lang: string,
}>();

const emit = defineEmits<{
  (e: 'select', text: string): void
}>();

const selected = ref("home");

watch(selected, (newSelected) => {
  emit('select', newSelected);
})

function select(event: Event) {
  const target = event.target as HTMLInputElement;
  selected.value = target.id;
}

</script>

<template>
  <nav id="menu">
    <ul>
    <MenuBtn id="home" :selected="selected" @click="select" :lang="lang"/>
    <MenuBtn id="projects" :selected="selected" @click="select" :lang="lang"/>
    <MenuBtn id="contact" :selected="selected" @click="select" :lang="lang"/>
    </ul>
  </nav>
</template>

<style scoped>

#menu {
  height:100%;
  z-index: 2;
}

#menu ul {
  height: 100%;
  list-style: none;
  display: flex;
  flex-flow: column ;
}

</style>
