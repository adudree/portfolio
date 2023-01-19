<script setup lang="ts">
import texts from "@/json/texts.json"; 
import { computed } from "vue";

const props = defineProps<{
  selected: string, 
  id: string,
  lang: string
}>();

function isSelected(selected: string, id: string) {
  return selected == id; 
}

const text : any = texts;
const idItem = computed(() => "menu-" + props.id)
</script>

<template>
  <div :id="id" class="a" :class="{selected: isSelected(selected, id)}" >
    <p class="b">
  {{ text[idItem][lang] }}
    </p></div>
</template>

<style scoped>

.selected {
  color: var(--color-important);
  border-left: 5px solid var(--color-important) !important;
  font-weight: 800;
}

.b {
  display: block;
  margin: auto;
  text-align: center;
  transform: rotate(90deg);
  transform-origin: center;
  font-size: 1.1rem;
  pointer-events: none;
  width: 70px;
}

.a {
  display: flex;
  justify-content: space-around;
  text-decoration: none;
  flex: 1 1 auto;
  align-self: stretch;
  background: var(--color-background-menu);
  border-left: 1px solid var(--color-important);
}

.a:hover {
  background: #F28482;
  color: #fff;
  cursor: pointer;
}

</style>
